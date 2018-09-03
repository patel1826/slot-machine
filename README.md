//MainActivity
public class MainActivity extends AppCompatActivity {
    public static final String EXTRA_NUM="com.example.michellezhang.slotmachineminigame.EXTRA_INT";
    private Button btn1;
    private int numClick;
    private TextView coins;
    private int numCoin=0;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        coins=(TextView)findViewById(R.id.textView);
        numClick=0;
        btn1 = (Button) findViewById(R.id.button1);
        btn1.setOnClickListener(new View.OnClickListener(){

            @Override
            public void onClick(View v) {
                numClick++;
                //minigame will pop up evey other click
                if(numClick%2==0){
                    //this calls the method that will open up anther activity
                    openActivity();
                }
            }
        });
        Intent intent2=getIntent();
        int num=intent2.getIntExtra(Main2Activity.EXTRA_INT, 0);

        numCoin=num;
        coins.setText(num+"");
        Toast.makeText(this, num + "", Toast.LENGTH_SHORT).show();

    }
    public void openActivity(){
        //opens up a second activity
        Intent intent=new Intent(this, Main2Activity.class);
        //allows the other activity to access the number of coins the player has
        intent.putExtra(EXTRA_NUM, numCoin);
        //launches the second activity
        startActivity(intent);
    }

}
//Main2Activity

public class Main2Activity extends AppCompatActivity {
    public static final String EXTRA_INT="com.example.michellezhang.slotmachineminigame.EXTRA_INT";
    private Button spin;
    private ArrayList<Integer> slotNum=new ArrayList<>();
    //displays win or lose
    private TextView showSpin;
    //takes players guess
    private EditText input;
    //number the slot lands on
    private int spinResult;
    //how many coins the player earns
    private int prize=0;
    //how many coins the player has going into the minigame
    private int startCoins=0;
    private ArrayList<Integer> slotImg = new ArrayList<Integer>();
    private ImageView slot1;
    private int counter=0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        //accesses the number of coins the player has, gets data from the main activity
        Intent intent2=getIntent();
        startCoins=intent2.getIntExtra(MainActivity.EXTRA_NUM, 0);
        prize=startCoins;

        showSpin=(TextView)findViewById(R.id.textView2);
        slot1 = findViewById(R.id.singleSlot);
        input=(EditText)findViewById(R.id.enterGuess);

        for(int i=0; i<7; i++){
            slotNum.add(i);
        }
        slotImg.add(R.drawable.zero);
        slotImg.add(R.drawable.one);
        slotImg.add(R.drawable.two);
        slotImg.add(R.drawable.three);
        slotImg.add(R.drawable.four);
        slotImg.add(R.drawable.five);
        slotImg.add(R.drawable.six);

        spin=(Button)findViewById(R.id.btn2);
        spin.setOnClickListener(new View.OnClickListener(){

            @Override
            public void onClick(View v) {

                new CountDownTimer(5000,100){
                    @Override
                    public void onTick(long millisUntilFinished) {
                        counter++;
                        if(counter<=15) {
                            //shows random images
                            spinResult = slotNum.get((int) (Math.random() * slotNum.size()));
                            slot1.setImageResource(slotImg.get(spinResult));

                        }
                        else if (counter == 16) {
                            //adds coins to the player's original amount if they win
                            if (spinResult == Integer.parseInt(input.getText().toString())) {
                                prize = startCoins + 50;
                            }

                        }
                        else if (counter > 16) {
                            //displays win or lose
                            if (spinResult == Integer.parseInt(input.getText().toString())) {
                                showSpin.setText("You \n Win!");
                                if(counter%8==0){
                                    showSpin.setText("");
                                }

                            }
                            else {
                                showSpin.setText("You \n Lose");
                                if(counter%8==0){
                                    showSpin.setText("");
                                }
                            }
                        }

                    }
                    @Override
                    public void onFinish() {
                    //returns to the main activity and passes through the amound of coins the player has after playing the minigame
                        Intent intent =new Intent(Main2Activity.this, MainActivity.class);
                        intent.putExtra(EXTRA_INT, prize);
                        startActivity(intent);

                    }

                }.start();

            }
        });
    }
}
