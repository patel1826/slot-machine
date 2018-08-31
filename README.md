# slot-machine
 private ArrayList<Integer> slotImg = new ArrayList<Integer>();
    private ArrayList<Integer> slots = new ArrayList<Integer>();
     Handler timerHandler = new Handler();
     //sends runnables to a queue and executes them (each runnable creates a spinning slot)
     long startTime =0;
          Runnable s1Runnable = new Runnable() {
            @Override
            public void run() {
                //displays images in short->longer time intervals in image view (looks like spinning)
                ImageView slot1 = findViewById(R.id.slot1);
                int pos = slots.get((int) (Math.random() * slots.size()));
                slot1.setImageResource(slotImg.get(pos));//displays random image
                int milisec = (int)((System.currentTimeMillis()-startTime));//amt of time passed btwn spinning start-now
                if (milisec>=500){//after certain amt of time spinning stops
                    timerHandler.removeCallbacks(this);
                }
                else if(((System.currentTimeMillis()-startTime))>=100){//as time passes, the delay btwn runnable calls increases
                    timerHandler.postDelayed(this,(25*(milisec/100)));
                }
                else{
                    timerHandler.postDelayed(this,25);//adds runnable to queue again, to show series of imgs quickly
                }
            }
        };
        Runnable s2Runnable = new Runnable() {
            @Override
            public void run() {
                ImageView slot2 = findViewById(R.id.slot2);
                slot2.setImageResource(slotImg.get(slots.get((int) (Math.random() * slots.size()))));
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
                slot3.setImageResource(slotImg.get(slots.get((int) (Math.random() * slots.size()))));
                int milisec = (int)((System.currentTimeMillis()-startTime));
                if (milisec>=2000){
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
        for (int i=0;i<7;i++){//fills possible outcomes of spin to array (0-6)
            slots.add(i);
        }
        slotImg.add(R.drawable.zero);
        slotImg.add(R.drawable.one);
        slotImg.add(R.drawable.two);
        slotImg.add(R.drawable.three);
        slotImg.add(R.drawable.four);
        slotImg.add(R.drawable.five);
        slotImg.add(R.drawable.six);
        spin.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {//displays random images in imgviews(slots) to make it seem like its spinning
                startTime = System.currentTimeMillis();
                timerHandler.postDelayed(s1Runnable,0);//tells handlers to add runnables to queue and run them
                timerHandler.postDelayed(s2Runnable,0);
                timerHandler.postDelayed(s3Runnable,0);

            }
        });

    }
