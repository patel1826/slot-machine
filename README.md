# slot-machine
//MainActivity
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.os.Handler;
import android.view.View;
import android.widget.ImageView;
import android.widget.TextView;
import android.widget.Button;
import android.widget.Toast;
import android.content.Intent;

//import org.w3c.dom.Text;

import java.util.ArrayList;
import java.util.Timer;

public class MainActivity extends AppCompatActivity {
   // public static final String EXTRA_NUM="com.example.mpate.intro.EXTRA_NUM";
    private ArrayList<Integer> slotImg = new ArrayList<Integer>();
    private ArrayList<Integer> s1 = new ArrayList<Integer>();
    private ArrayList<Integer> s2 = new ArrayList<Integer>();
    private ArrayList<Integer> s3 = new ArrayList<Integer>();
    private int gameCt =0;
    private int bet =0;
    private int coin =100;
    private int coinsEarned;
    private Integer[] dispNum = new Integer[3];//dispNum will hold the final #'s after slot machine runs
     Handler timerHandler = new Handler();
     //sends runnables to a queue and executes them (each runnable creates a spinning slot)
     long startTime =0;
          Runnable s1Runnable = new Runnable() {
            @Override
            public void run() {
                //displays images in short->longer time intervals in image view (looks like spinning)
                ImageView slot1 = findViewById(R.id.slot1);
                dispNum[0]=s1.get((int) (Math.random() * s1.size()));
                slot1.setImageResource(slotImg.get(dispNum[0]));//displays random image
                int milisec = (int)((System.currentTimeMillis()-startTime));
                //amt of time passed btwn spinning start-now ^
                if (milisec>=500){//after certain amt of time spinning stops
                    timerHandler.removeCallbacks(this);
                }
                else if(((System.currentTimeMillis()-startTime))>=100){
                    //as time passes, the delay btwn runnable calls increases
                    timerHandler.postDelayed(this,(25*(milisec/100)));
                }
                else{
                    timerHandler.postDelayed(this,25);
                    //adds runnable to queue again, to show series of imgs quickly
                }
            }
        };
        Runnable s2Runnable = new Runnable() {
            @Override
            public void run() {
                ImageView slot2 = findViewById(R.id.slot2);
                dispNum[1]=s2.get((int) (Math.random() * s2.size()));
                slot2.setImageResource(slotImg.get(dispNum[1]));
                int milisec = (int)((System.currentTimeMillis()-startTime));
                if (milisec>=1500){
                    timerHandler.removeCallbacks(this);
                }
                else if(((System.currentTimeMillis()-startTime))>=250){
                    timerHandler.postDelayed(this,(40*(milisec/250)));
                }
                else{
                    timerHandler.postDelayed(this,25);
                }
            }
        };
        Runnable s3Runnable = new Runnable() {
            @Override
            public void run() {
                ImageView slot3 = findViewById(R.id.slot3);
                dispNum[2]=s3.get((int) (Math.random() * s3.size()));
                slot3.setImageResource(slotImg.get(dispNum[2]));
                int milisec = (int)((System.currentTimeMillis()-startTime));
                if (milisec>=2000){
                    checkWinning();//checks to see if player won anything
                    timerHandler.removeCallbacks(this);
                    if(gameCt%5==0){//calls minigame to run every 5 games
                       openMiniGame();
                    }
                }
                else if(((System.currentTimeMillis()-startTime))>=500){
                    timerHandler.postDelayed(this,(60*(milisec/500)));
                }
                else{
                    timerHandler.postDelayed(this,25);
                }
            }
        };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        final Button spin = findViewById(R.id.spinBtn);
        final Button addCoin = findViewById(R.id.addCoin);
        for (int i=0;i<6;i++){//fills possible outcomes of spin to array (0-6)
            s1.add(i);
            s2.add(i);
            s3.add(i);
        }
        slotImg.add(R.drawable.zero);
        slotImg.add(R.drawable.one);
        slotImg.add(R.drawable.two);
        slotImg.add(R.drawable.three);
        slotImg.add(R.drawable.four);
        slotImg.add(R.drawable.five);
       // slotImg.add(R.drawable.six);
        spin.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {//displays random images in imgviews(slots) to make it seem like its spinning
                 if (bet>0){
                    gameCt++;
                    startTime = System.currentTimeMillis();
                    timerHandler.postDelayed(s1Runnable,0);//tells handlers to add runnables to queue and run them
                    timerHandler.postDelayed(s2Runnable,0);
                    timerHandler.postDelayed(s3Runnable,0);
                }
//                Toast.makeText(getBaseContext(),"hiii",Toast.LENGTH_LONG).show();

            }
        });
        addCoin.setOnClickListener(new View.OnClickListener() {//player increases bet by 1
            @Override
            public void onClick(View v) {
                bet++;
                coin--;
                dispMoney();
            }
        });
           Intent intent2=getIntent();//when minigame runs and then reopens this activity, all numbers reset to original values(ex, player money count)
           Bundle bundle = intent2.getExtras();//minigame passes along data in a bundle
           if(bundle!=null){//checks in case the bundle sent is empty
               coin = bundle.getInt("coin");//the int value for the total coins a player has, comes with a string key to identify it
               coinsEarned= bundle.getInt("earn");
           }
//        coin+=intent2.getIntExtra(MiniGame.EXTRA_INT, 0);
        dispMoney();//disps new money
    }
    public void checkWinning(){//checks result of spin to see if player won anything
        int matches =0;
        for (int num:dispNum){//checks to see how many times 2 appears in all slots
            if(num==2){
                matches++;
            }
        }
        if(matches==3){//triple
            coinsEarned+=(bet*10);
            coin+=(bet*10);//player gets 10* original bet
            Toast.makeText(getBaseContext(),"TRIPLE",Toast.LENGTH_LONG).show();
        }
        else if(matches==2){//double
            coinsEarned+=(bet*4);
            coin+=(bet*4);
            Toast.makeText(getBaseContext(),"DOUBLE",Toast.LENGTH_LONG).show();
        }
        else if(matches==1 && (dispNum[0]==2 ||dispNum[2]==2)){//single
            coinsEarned+=(bet*2);
            coin+=(bet*2);
            Toast.makeText(getBaseContext(),"SINGLE",Toast.LENGTH_LONG).show();
        }
        else{//nothing
            Toast.makeText(getBaseContext(),"NILL",Toast.LENGTH_LONG).show();
        }
        bet=0;
        dispMoney();
    }
    public void dispMoney(){//displays players bet and the total coins they have
        TextView numCoin = findViewById(R.id.numCoin);
        TextView totalCoin = findViewById(R.id.totalCoin);
        numCoin.setText("BET:" +bet);
        totalCoin.setText("TOTAL:"+coin);
    }
    public void openMiniGame(){//opens new activity
        Intent intent = new Intent(this, MiniGame.class);//goes from this class, to minigame class
        Bundle bundle = new Bundle();//passes along data to new activity
        bundle.putInt("coin",coin);//total money(coin) is connected to key word "coin" which will help identify what the number is
        bundle.putInt("earn",coinsEarned);
        intent.putExtras(bundle);//sends bundle to mini game class
        startActivity(intent);//opens/starts minigame class
    }

}

//MINI GAME (SEPARATE CLASS)

import android.content.Intent;
import android.os.CountDownTimer;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.os.Handler;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.ImageView;
import android.widget.TextView;
import android.widget.Toast;

import java.util.ArrayList;

public class MiniGame extends AppCompatActivity {
    private ArrayList<Integer> slotImg = new ArrayList<Integer>();
    public static final String EXTRA_INT="com.example.mpate.intro.EXTRA_INT";
    private ArrayList<Integer> s2 = new ArrayList<Integer>();
    private long start =0;
    private Handler timer = new Handler();
    private String userGuess;
    private int prize=0;
    private int dispNum;
    private int count =0;
    private int coin=0;
    private int coinEarned=0;
    Runnable s2Runnable = new Runnable() {
        @Override
        public void run() {
            //displays images in short->longer time intervals in image view (looks like spinning)
            ImageView slot2 = findViewById(R.id.slotImg2);
            int dispNum =s2.get((int) (Math.random() * s2.size()));
            slot2.setImageResource(slotImg.get(dispNum));//displays random image
            int milisec = (int)((System.currentTimeMillis()-start));
            //amt of time passed btwn spinning start-now ^
            if (milisec>=1500){//after certain amt of time spinning stops
                checkWin();
                timer.removeCallbacks(this);
            }
            else if(((System.currentTimeMillis()-start))>=250){
                //as time passes, the delay btwn runnable calls increases
                timer.postDelayed(this,(40*(milisec/250)));
            }
            else{
                timer.postDelayed(this,25);
                //adds runnable to queue again, to show series of imgs quickly
            }
        }
    };
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_mini_game);
        final Button spin = findViewById(R.id.spin);
        for (int i=0;i<6;i++){//fills possible outcomes of spin to array (0-6)
            s2.add(i);
        }
        slotImg.add(R.drawable.zero);
        slotImg.add(R.drawable.one);
        slotImg.add(R.drawable.two);
        slotImg.add(R.drawable.three);
        slotImg.add(R.drawable.four);
        slotImg.add(R.drawable.five);
        Intent intent2=getIntent();
        //grabs int values sent from mainactivity such as total money and total money earned as both were stored in a data bundle
        Bundle bundle = intent2.getExtras();
        coin = bundle.getInt("coin");
        coinEarned = bundle.getInt("earn");
        spin.setOnClickListener(new View.OnClickListener(){
            public void onClick(View v){//on button click, one slot will start spinning
                EditText guess = findViewById(R.id.enterGuess);
                 userGuess = guess.getText().toString();
                if (userGuess.compareTo("/")>0&&userGuess.compareTo("6")<0){//slot will spin if user guessed a number from (0-6)
                    start = System.currentTimeMillis();
                    timer.postDelayed(s2Runnable,0);//runs a runnable which displays images to simulate spinning
                }
            }
        });
    }
    public void checkWin(){//checks if player won, and displays it for 2 seconds
        new CountDownTimer(2000,100) {//timer runs for 2 secs, with 100 milisecond intervals
            @Override
            public void onTick(long millisUntilFinished) {
                count++;//keeps track of how many 100 milisecond intervals have passed
                TextView dispWin = findViewById(R.id.winTxt);
                if(count%2==0){//flashes the text "you win/lose" by displaying nothing during odd count intervals, and the text during even count intervals
                    if(Integer.parseInt(userGuess)==dispNum){//if user guess = the number displayed
                        prize=50;
                        dispWin.setText("YOU WIN");
                    }
                    else{
                        dispWin.setText("YOU LOSE");
                    }
                }
                else{
                    dispWin.setText("");
                }
            }
            @Override
            public void onFinish() {//when countdown timer finishes, main activity is opened again
                coin+=prize;
                coinEarned+=prize;
                Intent intent =new Intent(MiniGame.this, MainActivity.class);
                Bundle bundle = new Bundle();
                bundle.putInt("coin",coin);
                bundle.putInt("earned",5);
                intent.putExtras(bundle);
               // intent.putExtra(EXTRA_INT, prize);
                startActivity(intent);
            }

        }.start();
    }
}

