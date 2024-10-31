#include <Servo.h>
#include <Adafruit_NeoPixel.h>
#include <SoftwareSerial.h>

#define PIN1        11
#define PIN2        12
#define NUMPIXELS 16 // Popular NeoPixel ring size
float I2;
#include "ACS712.h"
ACS712 sensor(ACS712_05B, A6);
SoftwareSerial mySerial(10, 9); // RX, TX
#define   Current_sensor A6  //The sensor analog input pin

Adafruit_NeoPixel pixels1(NUMPIXELS, PIN1, NEO_GRB + NEO_KHZ800);
Adafruit_NeoPixel pixels2(NUMPIXELS, PIN2, NEO_GRB + NEO_KHZ800);
float i;

#define DELAYVAL 500


Servo myservoBase1;
Servo myservoTop1;

Servo myservoBase2;
Servo myservoTop2;
int LDR1=A0;
int LDR2=A1;
int LDR3=A2;
int LDR4=A3;
int LDR5=A4;
int LDR6=A5;

void setup() {
  // put your setup code here, to run once:
  pinMode(LDR1,INPUT);
  pinMode(LDR2,INPUT);
  pinMode(LDR3,INPUT);
  pinMode(LDR4,INPUT);
  pinMode(LDR5,INPUT);
  pinMode(LDR6,INPUT);
  Serial.begin(9600);
  myservoBase1.attach(2);
  myservoTop1.attach(3);
  myservoBase2.attach(4);
  myservoTop2.attach(5);
   pinMode(Current_sensor, INPUT);
  pixels1.begin();
  pixels2.begin();
  pinMode(6,INPUT);
pinMode(7,INPUT);
sensor.calibrate();
  while (!Serial) {
    ; // wait for serial port to connect. Needed for native USB port only
  }
  mySerial.begin(9600);
  pinMode(Current_sensor, INPUT);
  pixels1.begin();
  pixels2.begin();
}

void loop() 
{
  // put your main code here, to run repeatedly:
  Serial.print(analogRead(LDR1));
  Serial.print(" ");
  Serial.print(analogRead(LDR2));
  Serial.print(" ");
  Serial.print(analogRead(LDR3));
  Serial.print(" ");
  Serial.print(analogRead(LDR4));
  Serial.print(" ");
  Serial.print(analogRead(LDR5));
  Serial.print(" ");
  Serial.print(analogRead(LDR6));
  // zq
  
// int adc = analogRead(A6);
//  float voltage = adc*5/1023.0;
//  float current = (voltage-2.5)/0.185;
//  if ( current<0.06){
//    current=0;
//  }
//  Serial.print("Current : ");
//  Serial.println(current);
// delay(300);
  // mySerial.println("1\n:\n");
//  Serial.print("+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++");
//
//  Serial.println(i);
int data= digitalRead(6);
  int data2= digitalRead(7);
float I = sensor.getCurrentAC();
if( data==0){
  float I2=I;
}
if (( 15<(I2-I)<=20) && data==1){
mySerial.print("1");
  
}
//ignoring the value below 0.09
  if (I < 0.09) {
    I = 0;
  }
  
//  Serial.println(I);

//Serial.print(data);
//Serial.println(data2);

pixels1.show();
pixels2.show();
if (data==0 && data2==0){
pixels1.setBrightness(0);
pixels2.setBrightness(0);

}
else if (data==1 && data2==0){
pixels1.setBrightness(255);
pixels2.setBrightness(25);
}
else if (data==0 && data2==1){
  pixels2.setBrightness(255);
pixels1.setBrightness(25);
delay(1000);
}
else if (data==1 && data2==0){
pixels1.setBrightness(255);
pixels2.setBrightness(255);
delay(1000);
}
 for(int i=0; i<NUMPIXELS; i++)
{
 pixels1.setPixelColor(i, pixels1.Color(255,255,255));
pixels2.setPixelColor(i, pixels2.Color(255,255,255));
//     delay(DELAYVAL); // Pause before next pass through loop
}
 






  
 // mySerial.println(i);
 
//  if (Serial.available() > 0) //wait for data available
//  {
//   String teststr = Serial.readString();  //read until timeout
//  teststr.trim();                        // remove any \r \n whitespace at the end of the Strin
//// 
//  int newval12=teststr.toInt();
////   
// int led_1 = int(newval12/10);
// int led_2 = newval12%10;
////   
////    Serial.print(newval12);
////    Serial.print(" ");
////    Serial.print(led_1);
////    Serial.print(" ");
////    Serial.print(led_2);
//int ledval1=map(led_1,1,5,0,255);
//  int ledval2=map(led_2,1,5,0,255);
//// 
//    for(int i=0; i<NUMPIXELS; i++)
//    {
//      pixels1.setPixelColor(i, pixels1.Color(ledval1, ledval1, ledval1));
//      pixels2.setPixelColor(i, pixels2.Color(ledval2, ledval2, ledval2));
////     delay(DELAYVAL); // Pause before next pass through loop
//    }
//     
//    pixels1.show();
//    pixels2.show();
//  }    
 
  int myMeasurements1[3] = {analogRead(LDR1),analogRead(LDR2),analogRead(LDR3)};

   int maxVal1 = myMeasurements1[0];
   int j1=0;

   for (int i = 0; i < (sizeof(myMeasurements1) / sizeof(myMeasurements1[0])); i++) {
      if (myMeasurements1[i] > maxVal1) {
         maxVal1 = myMeasurements1[i];
         j1=i;
      }
   }
   int myMeasurements2[3] = {analogRead(LDR4),analogRead(LDR5),analogRead(LDR6)};

   int maxVal2 = myMeasurements2[0];
   int j2=0;

   for (int i = 0; i < (sizeof(myMeasurements2) / sizeof(myMeasurements2[0])); i++) {
      if (myMeasurements2[i] > maxVal2) {
         maxVal2 = myMeasurements2[i];
         j2=i;
      }
   }
   Serial.print(" ");
   Serial.print(maxVal1);
   Serial.print(" ");
   Serial.print(maxVal2);
   Serial.print(" ");
   Serial.print(j1);
   Serial.print(" ");
   Serial.print(j2);
   Serial.println();



     if (j1==0)
     {
      myservoBase1.write((myservoBase1.read() + 2));
        myservoTop1.write((myservoTop1.read() - 2));
     }
     else if (j1==2)
     {
      myservoBase1.write((myservoBase1.read() - 2));
        myservoTop1.write((myservoTop1.read() - 2));
     }
     else if ( (j1==1 && myservoTop1.read()<=60))
         {
            myservoTop1.write((myservoTop1 .read() + 2));
         }
       if (j2==0)
      {
        myservoBase2.write((myservoBase2.read() + 2));
        myservoTop2.write((myservoTop2.read() - 2));
      }
      if(j2==2)
      {
        myservoBase2.write((myservoBase2.read() - 2));
        myservoTop2.write((myservoTop2.read() - 2));
      }
     if ( (j2==1 && myservoTop2.read()<=60))
         {
            myservoTop2.write((myservoTop2.read() + 2));
         }
      else
     {
        myservoBase1.write(myservoBase1.read());
        myservoTop1.write(myservoTop1.read());
        myservoBase2.write(myservoBase2.read());
        myservoTop2.write(myservoTop2.read());
     }
     
  

}
