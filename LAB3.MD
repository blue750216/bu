# 嵌入式系統 - 實作3: 使用超音波感測器 + LED控制, 常用的C語言程式介紹
## Lab 3-1: Ultrasonic Sensor (3-pin) + 測距 (以公分顯示即可) + RS232 Output
![chrome-capture (3)](https://user-images.githubusercontent.com/89329299/138580687-8e417da2-a3da-4d10-8040-eccdf012246e.gif)
````C
int inches = 0;

int cm = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT); 
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  
  return pulseIn(echoPin, HIGH);
}

void setup()
{
  Serial.begin(9600);
}

void loop()
{
  cm = 0.01723 * readUltrasonicDistance(7, 7);
  
  inches = (cm / 2.54);
  Serial.print(inches);
  Serial.print("in, ");
  Serial.print(cm);
  Serial.println("cm");
  delay(100);
}
````
