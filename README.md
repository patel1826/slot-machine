public class ThreeByThree extends AppCompatActivity {
    ImageView slot1,slot2,slot3,slot4,slot5,slot6,slot7,slot8,slot9;
    private TextView showCalc;
    private ArrayList<ImageView> slots = new ArrayList<ImageView>();
    private ArrayList<Integer> slotImg = new ArrayList<Integer>();
    private ArrayList<Integer> s1 = new ArrayList<Integer>();
    private ArrayList<Integer> s2 = new ArrayList<Integer>();
    private ArrayList<Integer> s3 = new ArrayList<Integer>();
    private double numCalc=0;
    private int gameCt=0;
    private int operationCount =0;
    private int bet =0;
    private int coin =100;
    private int coinsEarned;
    private Boolean[] operation= new Boolean[4];//add,subtract,multiply,divide
    //private Integer[] numPlacement[0] = new Integer[3];//numPlacement[0] will hold the final #'s after slot machine runs
    private Integer[][] numPlacement= new Integer[3][3];//2d array for the 3x3 spinning numbers
    Handler timerHandler = new Handler();
    //sends runnables to a queue and executes them (each runnable creates a spinning slot)
    long startTime =0;
    Runnable s1Runnable = new Runnable() {
        @Override
        public void run() {
            //displays images in short->longer time intervals in image view (looks like spinning)
//            slot1 = findViewById(R.id.slot1);
//            slot4 = findViewById(R.id.slot4);
//            slot7 = findViewById(R.id.slot7);
            numPlacement[0][0]=s1.get((int) (Math.random() * s1.size()));
            numPlacement[1][0]=s1.get((int) (Math.random() * s1.size()));
            numPlacement[2][0]=s1.get((int) (Math.random() * s1.size()));
            slot1.setImageResource(slotImg.get(numPlacement[0][0]));//displays random image
            slot4.setImageResource(slotImg.get(numPlacement[1][0]));//displays random image
            slot7.setImageResource(slotImg.get(numPlacement[2][0]));//displays random image
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
//            slot2 = findViewById(R.id.slot2);
//            slot5 = findViewById(R.id.slot5);
//            slot8 = findViewById(R.id.slot8);
            numPlacement[0][1]=s2.get((int) (Math.random() * s1.size()));
            numPlacement[1][1]=s2.get((int) (Math.random() * s1.size()));
            numPlacement[2][1]=s2.get((int) (Math.random() * s1.size()));
            slot2.setImageResource(slotImg.get(numPlacement[0][1]));//displays random image
            slot5.setImageResource(slotImg.get(numPlacement[1][1]));//displays random image
            slot8.setImageResource(slotImg.get(numPlacement[2][1]));//displays random image
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
//            slot3 = findViewById(R.id.slot3);
//            slot6 = findViewById(R.id.slot6);
//            slot9 = findViewById(R.id.slot9);
            numPlacement[0][2]=s3.get((int) (Math.random() * s3.size()));
            numPlacement[1][2]=s3.get((int) (Math.random() * s3.size()));
            numPlacement[2][2]=s3.get((int) (Math.random() * s3.size()));
            slot3.setImageResource(slotImg.get(numPlacement[0][2]));//displays random image
            slot6.setImageResource(slotImg.get(numPlacement[1][2]));//displays random image
            slot9.setImageResource(slotImg.get(numPlacement[2][2]));//displays random image
            int milisec = (int)((System.currentTimeMillis()-startTime));

            if (milisec>=2000){
                 //checkWinning();//checks to see if player won anything
                timerHandler.removeCallbacks(this);
//                if(gameCt%5==0){//calls minigame to run every 5 games

                    //openMain();
//                }
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
        setContentView(R.layout.activity_three_by_three);
        showCalc=findViewById(R.id.showCalc);
        slot1 = findViewById(R.id.slot1);
        slot4 = findViewById(R.id.slot4);
        slot7 = findViewById(R.id.slot7);
        slot2 = findViewById(R.id.slot2);
        slot5 = findViewById(R.id.slot5);
        slot8 = findViewById(R.id.slot8);
        slot3 = findViewById(R.id.slot3);
        slot6 = findViewById(R.id.slot6);
        slot9 = findViewById(R.id.slot9);
        slots.add(slot1);
        slots.add(slot2);
        slots.add(slot3);
        slots.add(slot4);
        slots.add(slot5);
        slots.add(slot6);
        slots.add(slot7);
        slots.add(slot8);
        slots.add(slot9);

        final Button spin = findViewById(R.id.spinBtn);
        final Button addCoin = findViewById(R.id.addCoin);
        final Button add=findViewById(R.id.add);
        final Button subtract=findViewById(R.id.subtract);
        final Button multiply=findViewById(R.id.multiply);
        final Button divide=findViewById(R.id.divide);


        for (int i=0;i<6;i++){//fills possible outcomes of spin to array (0-6)
            s1.add(i);
            s2.add(i);
            s3.add(i);
            //sets elements of operation array to false
            if(i<4){
                operation[i]=false;
            }
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
//                    timerHandler.postDelayed(s4Runnable,0);//tells handlers to add runnables to queue and run them
//                    timerHandler.postDelayed(s5Runnable,0);
//                    timerHandler.postDelayed(s6Runnable,0);
//                    timerHandler.postDelayed(s7Runnable,0);//tells handlers to add runnables to queue and run them
//                    timerHandler.postDelayed(s8Runnable,0);
//                    timerHandler.postDelayed(s9Runnable,0);
                    //changes the ui for 24
                    spin.setVisibility(Button.INVISIBLE);
                    TextView title1=findViewById(R.id.textView);
                    title1.setVisibility(TextView.GONE);
                    TextView title2=findViewById(R.id.textView4);
                    title2.setVisibility(TextView.GONE);
                    showCalc.setVisibility(TextView.VISIBLE);
                    add.setVisibility(Button.VISIBLE);
                    subtract.setVisibility(Button.VISIBLE);
                    multiply.setVisibility(Button.VISIBLE);
                    divide.setVisibility(Button.VISIBLE);
                    Toast.makeText(ThreeByThree.this, "Make 24 to Win", Toast.LENGTH_SHORT).show();
                }
//                Toast.makeText(getBaseContext(),"hiii",Toast.LENGTH_LONG).show();

            }
        });

        add.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                for(int i=0; i<4; i++){
                    operation[i]=false;
                }
                operation[0]=true;
            }
        });
        subtract.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                for(int i=0; i<4; i++){
                    operation[i]=false;
                }
                operation[1]=true;
            }
        });
        multiply.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                for(int i=0; i<4; i++){
                    operation[i]=false;
                }
                operation[2]=true;
            }
        });
        divide.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                for(int i=0; i<4; i++){
                    operation[i]=false;
                }
                operation[3]=true;
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
        for(int i=0; i<9; i++) {
            slots.get(i).setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    calculateNum(v);
                    for(int j=0; j<9; j++){
                        if(slots.get(j).getId()==v.getId()){
                            slots.get(j).setVisibility(ImageView.INVISIBLE);
                        }
                    }
                    operationCount++;
                    if(operationCount==9){
                        checkWinning();
                    }
                }
            });
        }

        Intent intent2=getIntent();//when minigame runs and then reopens this activity, all numbers reset to original values(ex, player money count)
        Bundle bundle = intent2.getExtras();//minigame passes along data in a bundle
        if(bundle!=null){//checks in case the bundle sent is empty
            coin = bundle.getInt("coin");//the int value for the total coins a player has, comes with a string key to identify it
            //coinsEarned= 0;
        }
//        coin+=intent2.getIntExtra(MiniGame.EXTRA_INT, 0);
        dispMoney();//disps new money
    }

    public double calculateNum(View v){
        //called when an image view is clicked and handles the caluclations
        int temp=0;
        for(int j=0; j<9; j++){
             if(slots.get(j).getId()==v.getId()){
                 temp=numPlacement[j/3][j%3];
                 Toast.makeText(ThreeByThree.this, temp+"", Toast.LENGTH_SHORT).show();
                 break;
             }
        }
        if(showCalc.getText().equals("")){
            showCalc.setText(temp+"");
            numCalc=temp;
        }
        else{
            if(operation[0]){
                //Toast.makeText(ThreeByThree.this, Double.parseDouble(showCalc.getText().toString())+"", Toast.LENGTH_SHORT).show();
                numCalc=temp+Double.parseDouble(showCalc.getText().toString());
                //Toast.makeText(ThreeByThree.this, "a", Toast.LENGTH_SHORT).show();
            }
            else if(operation[1]){
                numCalc=Double.parseDouble(showCalc.getText().toString())-temp;
                Toast.makeText(ThreeByThree.this, "s", Toast.LENGTH_SHORT).show();
            }
            else if(operation[2]){
                numCalc=temp*Double.parseDouble(showCalc.getText().toString());
                Toast.makeText(ThreeByThree.this, "m", Toast.LENGTH_SHORT).show();
            }
            else if(operation[3]){
                numCalc=Double.parseDouble(showCalc.getText().toString())/temp;
                Toast.makeText(ThreeByThree.this, "d", Toast.LENGTH_SHORT).show();
            }
            showCalc.setText(numCalc+"");
        }
        return numCalc;
    }

    public void checkWinning(){//checks if the player successfully got 24
        //int totalNum=0;
        if(Double.parseDouble(showCalc.getText().toString())==24){
            coin+=bet*24;
            Toast.makeText(getBaseContext(),"You Win",Toast.LENGTH_LONG).show();
        }
        else {
            Toast.makeText(getBaseContext(),"You Lose",Toast.LENGTH_LONG).show();
        }
//        for (int i=0; i<3;i++)
//        {
//            //goes through each row
//            for (int x=0;x<3;x++) {
//                //Toast.makeText(getBaseContext(),"num"+numPlacement[i][x],Toast.LENGTH_LONG).show();
//                if (numPlacement[i][x]==2)
//                {
//                    totalNum++;
//                }
//                //totalNum+=x;
//                //goes through each collumn
////                if (x == chosenNum) {
////                    //if the number is found, then adds a one to the new array(numFound) at the same position, if not, adds a a zero
////                    numFound[i][x]=1;
////                    numsFound++;
////
////
////                }
////                else
////                {
////                    numFound[i][x]=0;
////                }
//
//            }
//        }
        //coin+=bet*totalNum;

        dispMoney();



        }

    public void dispMoney(){//displays players bet and the total coins they have
        TextView numCoin = findViewById(R.id.numCoin);
        TextView totalCoin = findViewById(R.id.totalCoin);
        numCoin.setText("BET:" +bet);
        totalCoin.setText("TOTAL:"+coin);
    }
    public void openMain(){//opens new activity
        Intent intent = new Intent(this, MainActivity.class);//goes from this class, to minigame class
        Bundle bundle = new Bundle();//passes along data to new activity
        bundle.putInt("coin",coin);//total money(coin) is connected to key word "coin" which will help identify what the number is
        bundle.putInt("earn",0);
        intent.putExtras(bundle);//sends bundle to mini game class
        startActivity(intent);//opens/starts minigame class
    }
}
