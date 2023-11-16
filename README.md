#calculator
 
 EditText input1;
    EditText input2;
    RadioGroup select;
    Button btn;
    TextView res;
    Double num1, num2, ans;
    @Override

    input1 = findViewById(R.id.editTextTextPersonName);
        input2 = findViewById(R.id.editTextTextPersonName2);
        select = findViewById(R.id.select);
        btn = findViewById(R.id.button);
        res = findViewById(R.id.textView3);

        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {


                switch (select.getCheckedRadioButtonId()){
                    case R.id.radioButton:
                        num1 = Double.parseDouble(input1.getText().toString());
                        num2 = Double.parseDouble(input2.getText().toString());
                        ans = num1+num2;
                        res.setText(ans.toString());
                        break;
# music player
music = MediaPlayer.create( context: this, R.raw.song); }
public void musicplay (View v) {
music.start();
}
#text app
 EditText number_ip, message_ip;
    Button btn;
number_ip = findViewById(R.id.editTextTextPersonName);
        message_ip = findViewById(R.id.editTextTextPersonName2);
        btn = findViewById(R.id.button);
 btn.setOnClickListener(new View.OnClickListener()
 String number = number_ip.getText().toString();
                String message = message_ip.getText().toString();
                SmsManager messenger  = SmsManager.getDefault();
                messenger.sendTextMessage(number, null,message,null, null);
