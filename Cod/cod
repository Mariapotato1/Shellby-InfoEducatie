#include <DFRobot_HuskyLens.h>
#include <HUSKYLENS.h>
#include <HUSKYLENSMindPlus.h>
#include <HuskyLensProtocolCore.h>
#include <Servo.h>
int material = 0;//1-plastic 2-metal 3-hartie
HUSKYLENS huskylens;
Servo servoarm1, servoarm2, servoclaw, servopitch;

const int motorfr1=7, motorfr2=6; 
const int motorbr1=5, motorbr2=4;
const int motorfl1=13, motorfl2=12;
const int motorbl1=11, motorbl2=10;
const int enable12=9;
const int enable34=3;
const int motor1=2, motor2=1;
const int enable5=0;

const int TARGET_ID=1;

void moveForward(int speed){
    digitalWrite(motorfr1, HIGH);
    digitalWrite(motorfr2, HIGH);
    digitalWrite(motorbr1, LOW);
    digitalWrite(motorbr2, LOW);
    digitalWrite(motorfl1, HIGH);
    digitalWrite(motorfl2, HIGH);
    digitalWrite(motorbl1, LOW);
    digitalWrite(motorbl2, LOW);
    digitalWrite(enable12, speed);
    digitalWrite(enable34, speed); 
  }
  void turnLeft(int speed){
    digitalWrite(motorfr1, LOW);
    digitalWrite(motorfr2, LOW);
    digitalWrite(motorbr1, HIGH);
    digitalWrite(motorbr2, HIGH);
    digitalWrite(motorfl1, HIGH);
    digitalWrite(motorfl2, HIGH);
    digitalWrite(motorbl1, LOW);
    digitalWrite(motorbl2, LOW);
    digitalWrite(enable12, speed);
    digitalWrite(enable34, speed);
  }
  void turnRight(int speed){
    digitalWrite(motorfr1, HIGH);
    digitalWrite(motorfr2, HIGH);
    digitalWrite(motorbr1, LOW);
    digitalWrite(motorbr2, LOW);
    digitalWrite(motorfl1, LOW);
    digitalWrite(motorfl2, LOW);
    digitalWrite(motorbl1, HIGH);
    digitalWrite(motorbl2, HIGH);
    digitalWrite(enable12, speed);
    digitalWrite(enable34, speed);
  }
  void stopMotors(){
    digitalWrite(motorfr1, LOW);
    digitalWrite(motorfr2, LOW);
    digitalWrite(motorbr1, LOW);
    digitalWrite(motorbr2, LOW);
    digitalWrite(motorfl1, LOW);
    digitalWrite(motorfl2, LOW);
    digitalWrite(motorbl1, LOW);
    digitalWrite(motorbl2, LOW);
    digitalWrite(enable12, 0);
    digitalWrite(enable34, 0);
 }

void setup() {
Serial.begin(9600);

 if(!huskylens.begin(Wire)){
  Serial.println("Huskylens negasit");
  while (1);
 }
 servoarm1.attach(A5);
 servoarm2.attach(A4);
 servoclaw.attach(A2);
 servopitch.attach(A3);

 pinMode(motorfr1, OUTPUT);
 pinMode(motorfr2, OUTPUT);
 pinMode(motorbr1, OUTPUT);
 pinMode(motorbr2, OUTPUT);
 pinMode(motorfl1, OUTPUT);
 pinMode(motorfl2, OUTPUT);
 pinMode(motorbl1, OUTPUT);
 pinMode(motorbl2, OUTPUT);
 pinMode(enable12, OUTPUT);
 pinMode(enable34, OUTPUT);
}

void grabAndFlip(distance, x_cm){
digitalWrite(motor2, LOW);
digitalWrite(motor1, HIGH);
delay (distance*54);
digitalWrite(motor2, LOW);
digitalWrite(motor1, LOW);
  
  if (x_cm>0){ digitalWrite(motor1, HIGH);
    digitalWrite(motor2, LOW);
    delay(132*x_cm);
    digitalWrite(motor1, LOW);
    digitalWrite(motor2, LOW);
  }
  else if (x_cm<0){ digitalWrite(motor2, HIGH);
    digitalWrite(motor1, LOW);
    delay(132*x_cm);
    digitalWrite(motor1, LOW);
    digitalWrite(motor2, LOW);
  }
    
    servoarm1.write(90);
    servoarm2.write(90);
    delay(500);

    servoclaw.write(60);
    delay(500);

    servoarm1.write(120);
    servoarm2.write(120);
    delay(500);

    servoclaw.write(10);
    delay(500);

    servoarm1.write(60);
    servoarm2.write(60);
    delay(500);

    servopitch.write(90);

    delay(1000);
     if (x_cm>0){ digitalWrite(motor1, LOW);
    digitalWrite(motor2, HIGH);
    delay(132*x_cm);
    digitalWrite(motor1, LOW);
    digitalWrite(motor2, LOW);
  }
  else if (x_cm<0){ digitalWrite(motor2, LOW);
    digitalWrite(motor1, HIGH);
    delay(132*x_cm);
    digitalWrite(motor1, LOW);
    digitalWrite(motor2, LOW);
  }
    delay(10000);
  }  
void aruncare(int n){
  if (n==2){  digitalWrite(motor2, HIGH);
    digitalWrite(motor1, LOW);
    delay(132*8);
    digitalWrite(motor1, LOW);
    digitalWrite(motor2, LOW);
  

}
else if(n==3){digitalWrite(motor1, HIGH);
    digitalWrite(motor2, LOW);
    delay(132*8);
    digitalWrite(motor1, LOW);
    digitalWrite(motor2, LOW);
  
  
}
 servopitch.write(180);
 delay(10)
 servoclaw.write(60);


}
void plastic(){
 int x, y, w, H_px;
 huskylens.request();
 if(huskylens.available()){
 HUSKYLENSResult result = huskylens.read();
 x=result.centrux;
 y=result.centruy;
 w=result.centruw;
 H_px=result.centruh; 
 float distance = (6 * 250) / H_px;
 float ox = x - 160;
 float x_cm = (ox / 250) * distance;
 grabAndFlip(distance,x_cm);
 aruncare(1);
}
void metal(){
 int x, y, w, H_px;
 huskylens.request();
 if(huskylens.available()){
 HUSKYLENSResult result = huskylens.read();
 x=result.xCenter;
 y=result.yCenter;
 w=result.width;
 H_px=result.height; 
 float distance = (6 * 250) / H_px;
 float ox = x - 160;
 float x_cm = (ox / 250) * distance;
  grabAndFlip(distance,x_cm);
  aruncare(2);
}
void hartie(){
 int x, y, w, H_px;
 huskylens.request();
 if(huskylens.available()){
 HUSKYLENSResult result = huskylens.read();
 x=result.centrux;
 y=result.centruy;
 w=result.centruw;
 H_px=result.centruh; 
 float distance = (6 * 250) / H_px;
 float ox = x - 160;
 float x_cm = (ox / 250) * distance;
  grabAndFlip(distance,x_cm);
  aruncare(3);
}
void loop() {
huskyens.request();
 if(huskylens.available()){
  HUSKYLENSResult result = huskylens.read();
  int x = result.ID;
  if(x=1){
    plastic()
    }else 
    if(x=2){
    metal()
    }else 
    if(x=3){
    hartie()
    }
      while(true);
 }else
    moveForward(100);
  
  delay(100);
  }
    }
