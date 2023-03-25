#include <Servo.h>
Servo myservo;
int led = 13;
int Sensor = A0;  //cam bien
int Value;
int pos = 9;
void setup() {
  // put your setup code here, to r once:
  myservo.attach(9);
  Serial.begin(9600);
  pinMode(Sensor, INPUT);  // đọc đầu vào giá trị
  pinMode(led, OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  Value = analogRead(Sensor);
  int pos = digitalRead(Sensor);
  Serial.println(pos);
  if (pos == 0) {
    pos = 1;
    digitalWrite(led, HIGH);
  } else {
    pos = 0;
    digitalWrite(led, LOW);
  }
  Serial.print("giá trị cảm biến");
  Serial.println(Value);
  Value = analogRead(pos);
  Value = map(Value, 0, 1023, 0, 180);
  myservo.write(Value);
  
  delay(100);
  
}
