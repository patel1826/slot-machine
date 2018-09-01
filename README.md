# slot-machine
 private ArrayList<Integer> slotImg = new ArrayList<Integer>();
    private ArrayList<Integer> s1 = new ArrayList<Integer>();
    private ArrayList<Integer> s2 = new ArrayList<Integer>();
    private ArrayList<Integer> s3 = new ArrayList<Integer>();
    private int bet =0;
    private int coin =100;
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
                startTime = System.currentTimeMillis();
                timerHandler.postDelayed(s1Runnable,0);//tells handlers to add runnables to queue and run them
                timerHandler.postDelayed(s2Runnable,0);
                timerHandler.postDelayed(s3Runnable,0);
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
    }
    public void checkWinning(){//checks result of spin to see if player won anything
        int matches =0;
        for (int num:dispNum){//checks to see how many times 2 appears in all slots
            if(num==2){
                matches++;
            }
        }
        if(matches==3){//triple
            coin+=(bet*10);//player gets 10* original bet
            Toast.makeText(getBaseContext(),"TRIPLE",Toast.LENGTH_LONG).show();
        }
        else if(matches==2){//double
            coin+=(bet*4);
            Toast.makeText(getBaseContext(),"DOUBLE",Toast.LENGTH_LONG).show();
        }
        else if(matches==1 && (dispNum[0]==2 ||dispNum[2]==2)){//single
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
        numCoin.setText("BET: " +bet);
        totalCoin.setText("TOTAL: "+coin);
    }
