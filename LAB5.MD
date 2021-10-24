#  嵌入式系統 - 實作5: Servo伺服馬達, 溫度感應器 + LCD 顯示器,  (W10) 
##  Lab 5-1 請使用兩個伺服馬達同步從 0 度逐步掃描到 180 度之後再逐步掃描回0度, 每步的間隔時間為50ms (0.05秒), 細節請參考以下Demo.
![chrome-capture](https://user-images.githubusercontent.com/89329299/138579923-d94f8db3-79fd-49a2-a7c8-e3ffbbfd10e1.gif)
````C
#include <Servo.h>

int pos = 0;

Servo servo_9;
Servo servo_8;


void setup()
{
  servo_9.attach(9, 500, 2500);
  servo_8.attach(8, 500, 2500);

}

void loop()
{
  // sweep the servo from 0 to 180 degrees in steps
  // of 1 degrees
  for (pos = 0; pos <= 180; pos += 1) {
    // tell servo to go to position in variable 'pos'
    servo_9.write(pos);
    servo_8.write(pos);
    // wait 15 ms for servo to reach the position
    delay(50); // Wait for 15 millisecond(s)
  }
  for (pos = 180; pos >= 0; pos -= 1) {
    // tell servo to go to position in variable 'pos'
    servo_9.write(pos);
    servo_8.write(pos);
    // wait 15 ms for servo to reach the position
    delay(50); // Wait for 15 millisecond(s)
  }
}
````
## Lab 5-2 LCD顯示溫度感應器的溫度;若溫度<38 綠LED亮; 若大於38度, 紅色LED亮, 細節請參考以下Demo
![chrome-capture (2)](https://user-images.githubusercontent.com/89329299/138580337-0df1ea4e-3d0e-42b2-8e2b-466d61b5d92d.gif)
````C
// For Embedded System course, VNU, Fall 2021 

#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  lcd.begin(16, 2);
  Serial.begin(9600);	
  pinMode(A1, INPUT); // Read analog voltage (2^10)

}

void loop() {
  int reading = analogRead(A1);  // read analog level (2^10)
  lcd.setCursor(0,0);  
  lcd.print("TMP Sensor Demo");

  float voltage = (reading/1024.0) * 5.0; // Convert to voltage
  
  // converting from 10mv per degree with 500mV offset  
  float tempC = (voltage - 0.5) * 100.0; 
  lcd.setCursor(0,1);
  lcd.print("Tmp:");
  lcd.print(tempC);
  lcd.print(" C");
  delay(500);
  lcd.clear();
  Serial.println(reading);
  Serial.println(voltage);  
}
````
