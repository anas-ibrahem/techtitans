#include <SoftwareSerial.h>
#include <LiquidCrystal_I2C.h>
#include <avr/wdt.h> 
#define IR_SENSOR_FRONT_LEFT A0
#define IR_SENSOR_FRONT_RIGHT A1
#define IR_SENSOR_SIDE_LEFT A3
#define IR_SENSOR_SIDE_RIGHT A2
#define motorA1 8 ///right  1
#define motorA2 9 //right   2
#define motorB1 10 //lwft    1 
#define motorB2 11 //lwft    2 
#define MOTOR_ENABLE_A 6 //pwm  
#define MOTOR_ENABLE_B 5 //pwm
bool onLine, finished;
int frontLeftSensorValue, frontRightSensorValue, sideLeftSensorValue, sideRightSensorValue;
LiquidCrystal_I2C lcd(0x26, 16, 2); 
signed short minutes, secondes;
char timeline[16];
bool printed= false;
char time[16];
unsigned long lastsecond,mazestarttime = 0;
SoftwareSerial bluetooth(3,2); // RX, TX
char t,mode=' '; //mode = E for changing mode, T for bluetooth mode, V for voice control mode, M for maze mode
void reset(){
  // Simulate a restart by triggering a watchdog reset
  wdt_enable(WDTO_15MS);  // Set the watchdog timer to reset after 15ms (the smallest allowed value)
  while (1) {}  // Wait for the watchdog reset to occur




}



void isfinish(){
if (finished)
{
rotate180left(); delay(220); moveforward(); delay(285); movebackward(); delay(190); turnleft(); delay(410);
 movebackward(); delay(270); stop();   delay(200);  check_readings(); int L=0;  // pre turn left to check if its an actual ending point

 
 
 
 
 if (finished){   // check again if its an actual ending point 
   for (int i=0;i<=15;i++)  { time[i]=timeline[i]; } int print =0;
while (finished)
{  
   
   if(!print) {lcd.clear();
   lcd.setCursor(0, 0);
   lcd.print("MISSION DONE :");
   lcd.setCursor(0, 1);
   sprintf(time,"%0.2d mins %0.2d secs", minutes, secondes);
   lcd.print(time);
   print =1;}
   printed = true;
   check_readings();
   if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}  // to exit from the maze mode
}

}}

else { rotate180left();
    while(1)

  {       

     check_readings();
    
    if    (frontLeftSensorValue == 0 && frontRightSensorValue == 0)    { L=1;  }
       
    
     if ( L==1 && (frontLeftSensorValue == 1 || frontRightSensorValue == 1) ) {L=0 ; rotate180right(); delay(60); movebackward(); 
     delay(170); stop();   delay(200); if(!(frontLeftSensorValue == 1 && frontRightSensorValue == 1 )) 
     {rotate180right(); delay(70);} else {rotate180right(); delay(25);}  break;}  // if not an actual ending point, turn left




}


}


}}


void check_readings(){  // check readings from sensors and update values


  

   if (analogRead(IR_SENSOR_SIDE_RIGHT) >800 )
   sideRightSensorValue = 1; else sideRightSensorValue = 0;

   if (analogRead(IR_SENSOR_SIDE_LEFT) >800 )
   sideLeftSensorValue = 1; else sideLeftSensorValue = 0;

      if (analogRead(IR_SENSOR_FRONT_LEFT) >800 )
   frontLeftSensorValue = 1; else frontLeftSensorValue = 0;

      if (analogRead(IR_SENSOR_FRONT_RIGHT) >800 )
   frontRightSensorValue = 1; else frontRightSensorValue = 0;

   finished = (frontLeftSensorValue == 1 && frontRightSensorValue == 1 && sideLeftSensorValue == 1 && sideRightSensorValue == 1);
  Serial.print("Front Left Sensor Value: ");
  Serial.println(analogRead(IR_SENSOR_FRONT_LEFT));
  Serial.print("Front Right Sensor Value: ");
  Serial.println(analogRead(IR_SENSOR_FRONT_RIGHT));
  Serial.print("Side Left Sensor Value: ");
   Serial.println( sideLeftSensorValue );
 Serial.print("Side Right Sensor Value: ");
  Serial.println( sideRightSensorValue);
  Serial.println(" ");

  delay(1);
}

// next are the movements function we didnt use all of them but we kept them for trying and see the best of them in different situations

void moveforward(){    //done
    analogWrite(MOTOR_ENABLE_A, 51); // speed
    analogWrite(MOTOR_ENABLE_B, 51);
    digitalWrite(motorA1, LOW);
    digitalWrite(motorA2, HIGH);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, HIGH);

}

void moveforwardbt(){    //done
    analogWrite(MOTOR_ENABLE_A, 65); // speed
    analogWrite(MOTOR_ENABLE_B, 65);
    digitalWrite(motorA1, LOW);
    digitalWrite(motorA2, HIGH);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, HIGH);

}

void movebackward(){    //
    analogWrite(MOTOR_ENABLE_A, 55); // speed
    analogWrite(MOTOR_ENABLE_B, 55);
    digitalWrite(motorA1, HIGH);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, HIGH);
    digitalWrite(motorB2, LOW);}

    void movebackwardbt(){    //
    analogWrite(MOTOR_ENABLE_A, 65); // speed
    analogWrite(MOTOR_ENABLE_B, 65);
    digitalWrite(motorA1, HIGH);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, HIGH);
    digitalWrite(motorB2, LOW);}

void turnleft(){ //done
    analogWrite(MOTOR_ENABLE_A, 75); // speed //60
    analogWrite(MOTOR_ENABLE_B, 107); //105
    digitalWrite(motorA1, LOW);
    digitalWrite(motorA2, HIGH);
    digitalWrite(motorB1, HIGH);
    digitalWrite(motorB2, LOW);
    
    
    
    }


    void turnleftnew(){ //done
    analogWrite(MOTOR_ENABLE_A, 68); // speed //60
    analogWrite(MOTOR_ENABLE_B, 98); //105
    digitalWrite(motorA1, LOW);
    digitalWrite(motorA2, HIGH);
    digitalWrite(motorB1, HIGH);
    digitalWrite(motorB2, LOW);
    
    
    
    }


void turnrightnew(){ //done
    analogWrite(MOTOR_ENABLE_A, 95); // speed 105
    analogWrite(MOTOR_ENABLE_B, 65); //45
    digitalWrite(motorA1, HIGH);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, HIGH);}

void turnright(){ //done
    analogWrite(MOTOR_ENABLE_A, 104); // speed 105
    analogWrite(MOTOR_ENABLE_B, 74); //45
    digitalWrite(motorA1, HIGH);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, HIGH);}


void turnrighthard(){ //done
    analogWrite(MOTOR_ENABLE_A, 155); // speed
    analogWrite(MOTOR_ENABLE_B, 130);
    digitalWrite(motorA1, HIGH);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, HIGH);}

    void turnlefthard(){ //done
    analogWrite(MOTOR_ENABLE_A, 70); // speed
    analogWrite(MOTOR_ENABLE_B, 120);
    digitalWrite(motorA1, LOW);
    digitalWrite(motorA2, HIGH);
    digitalWrite(motorB1, HIGH);
    digitalWrite(motorB2, LOW);}


void stop(){ //done
    digitalWrite(motorA1, LOW);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, LOW);}


void rotate180rightact(){ // rotating right not just 180 degree
    analogWrite(MOTOR_ENABLE_A, 110); // speed
    analogWrite(MOTOR_ENABLE_B, 110);
    digitalWrite(motorA1, HIGH);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, HIGH);

}


void rotate180rightacthady(){ //done more stable
    analogWrite(MOTOR_ENABLE_A, 70); // speed
    analogWrite(MOTOR_ENABLE_B, 70);
    digitalWrite(motorA1, HIGH);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, HIGH);}

void rotate180right(){ //done more stable
    analogWrite(MOTOR_ENABLE_A, 114); // speed
    analogWrite(MOTOR_ENABLE_B, 97);
    digitalWrite(motorA1, HIGH);
    digitalWrite(motorA2, LOW);
    digitalWrite(motorB1, LOW);
    digitalWrite(motorB2, HIGH);

}

void rotate180lefthady(){ //done
    analogWrite(MOTOR_ENABLE_A, 66); // speed
    analogWrite(MOTOR_ENABLE_B, 75);
    digitalWrite(motorA1, LOW);
    digitalWrite(motorA2, HIGH);
    digitalWrite(motorB1, HIGH);
    digitalWrite(motorB2, LOW);

}

void rotate180left(){ //rotate left not just 180 degree
    analogWrite(MOTOR_ENABLE_A, 102); // speed
    analogWrite(MOTOR_ENABLE_B, 118);
    digitalWrite(motorA1, LOW);
    digitalWrite(motorA2, HIGH);
    digitalWrite(motorB1, HIGH);
    digitalWrite(motorB2, LOW);

}

void setup() {
  lcd.init();
  lcd.backlight();
  lcd.clear();
  lcd.begin(16, 2);
  bluetooth.begin(9600);
  Serial.begin(9600);
  pinMode(IR_SENSOR_FRONT_LEFT, INPUT);
  pinMode(IR_SENSOR_FRONT_RIGHT, INPUT);
  pinMode(IR_SENSOR_SIDE_LEFT, INPUT);
  pinMode(IR_SENSOR_SIDE_RIGHT, INPUT);

  pinMode(motorA1, OUTPUT);
  pinMode(motorA2, OUTPUT);
  pinMode(motorB1, OUTPUT);
  pinMode(motorB2, OUTPUT);

  pinMode(MOTOR_ENABLE_A, OUTPUT);
  pinMode(MOTOR_ENABLE_B, OUTPUT);
  
  mode = 'N';

}





void loop() {


if (mode=='E')
{   stop();
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Selection Mode:");
    lcd.setCursor(0, 1);
    lcd.print("T:BT V:VC M:Maze");
}
while(mode=='E') //changing mode mode
{
   stop();
if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='T') {mode='T'; break;}
  if (t=='V') {mode='V'; break;}
  if (t=='M') {mode='M'; reset(); break;}
  if (t=='E') {mode='E'; break;}
}


}


if (mode=='T'){

    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Bluetooth Mode");
    lcd.setCursor(0, 1);
    lcd.print("El3b ya 3am :)");

}
while(mode=='T') //blutooth mode
{
if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}

}
 switch(t)
 {



  case 'F':
        {            //move forward(all motors rotate in forward direction)
   moveforwardbt(); delay(7); stop(); delay(1);
         
         
        }
        
   break;
   
  case 'B':
        {      //move reverse (all motors rotate in reverse direction)
movebackwardbt(); delay(7); stop(); delay(1);
         
        }
       
   break;
   
  case 'L':
        {    
  
 for (int i = 0 ; i<=0 ; i++)         
             
{rotate180left(); delay(7); stop(); delay(1);}
       
       
        }
   break;
   
  case 'R':
        {  
          
 for (int i = 0 ; i<=0 ; i++)         
              
{rotate180rightact(); delay(7); stop(); delay(1);}
       
       
       
        }
   break;
   
    
    case 'S':
        {           //STOP (all motors stop)
stop();
          
          
        }

 
        
 }
}

if (mode == 'V')
{
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("V.Control Mode");
    lcd.setCursor(0, 1);
    lcd.print("Sam3nyy Sotak !");
}
while(mode=='V') //voice control mode
{
    if (bluetooth.available() > 0)
    {
        t = bluetooth.read();
        Serial.println(t);
          if (t=='E') {mode='E'; break;}

    }

    switch (t)
    {   


          case 'P':
        {            //move forward(all motors rotate in forward direction)
   moveforwardbt(); delay(1000); stop(); delay(1);
   movebackwardbt(); delay(1000); stop(); delay(1);
   rotate180left(); delay(7000); stop(); delay(1);
   rotate180rightact(); delay(7000); stop(); delay(1);
         
         
        }


        case 'F':
            {
                moveforwardbt(); delay(2000); stop();
            }
            break;

        case 'B':
            {
                movebackwardbt(); delay(2000); stop();
            }
            break;

        case 'L':
            {
                rotate180left(); delay(320); stop(); delay(40);  rotate180left(); delay(320); stop(); delay(40);  rotate180left(); delay(100); stop(); 
            }
            break;

        case 'R':
            {
                 rotate180rightact(); delay(320); stop(); delay(40);  rotate180rightact(); delay(320); stop(); delay(40);  rotate180rightact(); delay(100); stop();
            }
            break;

        case 'S':
            {
                stop();
            }
            break;
    }

    // Reset the command after each loop iteration
    t = ' ';  // Set to an unused or default value
}


if (mode=='N')
{
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Maze Mode");
    lcd.setCursor(0, 1);
    lcd.print("Was3lyyy !!");
    delay(4000);

    

while (mode=='N'){ //maze mode
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Recorded Time:");
  // printed = false; 
  lcd.setCursor(0, 1);
  sprintf(timeline,"%0.2d mins %0.2d secs", minutes, secondes);
  lcd.print(timeline);
  

  if ( millis() - lastsecond >= 1000 )
  {  secondes = secondes + (millis() - lastsecond )/1000;
     lastsecond = millis();   }
  
  if ( secondes >= 60 )
  { int diff = secondes - 60;
    secondes = 0;
    minutes ++;
    secondes = diff;}
    
if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}
}






check_readings();

  if (sideLeftSensorValue == 0 )

{ if (frontLeftSensorValue == 1 && frontRightSensorValue == 1) {moveforward(); delay(30);} 

else if (frontLeftSensorValue == 1 && frontRightSensorValue == 0) { turnleftnew(); delay(30);}

  else if (frontLeftSensorValue == 0 && frontRightSensorValue == 1) { turnrightnew(); delay(30);}
   
}

if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}
}

if (sideLeftSensorValue == 1 && !finished) { 
    // check_readings();
  
  
  
  if (sideLeftSensorValue == 1 && !finished) { rotate180left(); delay(220); moveforward(); delay(285); movebackward(); delay(190); turnleft(); delay(410); movebackward(); delay(270); stop();   delay(200);  rotate180left(); int L=0;

  while(1)

  {       isfinish();

     check_readings();
    
    if    (frontLeftSensorValue == 0 && frontRightSensorValue == 0)    { L=1;  }
       
    
     if ( L==1 && (frontLeftSensorValue == 1 || frontRightSensorValue == 1) ) {L=0 ; rotate180right(); delay(60); movebackward(); delay(170); stop();   delay(200); if(!(frontLeftSensorValue == 1 && frontRightSensorValue == 1 )) {rotate180right(); delay(70);} else {rotate180right(); delay(25);}  break;}
 
 
 if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}
}
 
 
  }        }  } 


if (frontLeftSensorValue == 0 && frontRightSensorValue == 0 && sideLeftSensorValue == 0 && sideRightSensorValue == 1 ) 
{movebackward(); delay(220); turnright(); delay(180); movebackward(); delay(170); stop();   delay(200);  rotate180right(); int R=0;

  while(1)

  {   
     check_readings();
    
    if    (frontLeftSensorValue == 0 && frontRightSensorValue == 0)    { R=1;  }
       
    
     if ( R==1 && (frontLeftSensorValue == 1 || frontRightSensorValue == 1) ) {R=0 ; rotate180left(); delay(70); movebackward(); delay(170); stop();   delay(200); check_readings(); if(!(frontLeftSensorValue == 1 && frontRightSensorValue == 1 )) {rotate180left(); delay(80);} else {rotate180left(); delay(32);}  break;}
 
 if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}
}
 
 
 
  }        }   






    

    

 int BACKYAMAN = 0;

 int LETSGO = 0;

  if (frontLeftSensorValue == 0 && frontRightSensorValue == 0 && sideLeftSensorValue == 0 && sideRightSensorValue == 0 )
    {   
      if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}
}

      moveforward();
      for(int i=0; i<=6 ; i++)
      
      
      
        {delay(38);
         check_readings();
         if(!(frontLeftSensorValue == 0 && frontRightSensorValue == 0 && sideLeftSensorValue == 0 && sideRightSensorValue == 0 )){ LETSGO=0;       break; }
         if(i==6)   { LETSGO=1;       break; }
         }


          if (LETSGO )
            {  movebackward(); while(1)
            {

             check_readings();
             if (frontLeftSensorValue == 1 || frontRightSensorValue == 1 ) {BACKYAMAN = 1; moveforward(); delay(170); break;}


            }
            
            
            
             movebackward(); delay(200); turnright(); delay(250); movebackward(); delay(170); stop();   delay(200);  rotate180rightact(); int L=0;

  while(1)

  {       if (finished) { stop();}

     if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}
}
     check_readings();
    
    if    (frontLeftSensorValue == 0 && frontRightSensorValue == 0)    { L=1;  }
       
    
     if ( L==1 && (frontLeftSensorValue == 1 || frontRightSensorValue == 1) ) {L=0 ; rotate180left(); delay(70); movebackward(); delay(170); stop();   delay(200); check_readings(); if(!(frontLeftSensorValue == 1 && frontRightSensorValue == 1 ))
      {rotate180left(); delay(75);} else {rotate180left(); delay(29);}  break;}
 
 
 
 
 
  }        }   

            



             } 
             
             
             
             isfinish(); 
             
             
             if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; break;}
}
             
             
              }

if(bluetooth.available()>0)
{
  t = bluetooth.read();
  Serial.println(t);
  if (t=='E') {mode='E'; }
}



}}
   
   
   
   
   
    







  
    
    



