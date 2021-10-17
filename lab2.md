# 嵌入式系統 - 實作2: 會呼吸的RGB LED, 按鍵控制, 狀態輸出

## 實作2-1, analogWrite(): 並且觀查LED亮度變化是否有像"呼吸的效果"和示波器的波形有什麼關連性?

![image](https://user-images.githubusercontent.com/89329299/135738895-1609af6c-937b-48db-8c45-ca03b206c399.png)

````c
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delay(1000); 
 
  digitalWrite(13, LOW);
  delay(1000); 
}
````

## 實作2-2, RGB LED燈全彩模組, 分別讓LED輪流表現正紅、正綠、正藍，三個顏色，時間間隔1秒鐘。並且觀查LED顏色和波形或是電壓有什麼關連性? 可將個人說明在更新GitHub時一起加入. (互動2)

![image](https://user-images.githubusercontent.com/89329299/135739533-805a6bd0-78c1-46a4-af29-76c49f327e24.png)
````C
int R = 11;
int y = 9;
int B = 10;

void setup()
{
  pinMode(R, OUTPUT);
  pinMode(y, OUTPUT);
  pinMode(B, OUTPUT);  
}

void loop()
{
	analogWrite(R, 255);
	analogWrite(y, 0);
	analogWrite(B, 0);
  	delay(1000);
	analogWrite(R, 0);
	analogWrite(y, 255);
	analogWrite(B, 0);
  	delay(1000);
	analogWrite(R, 0);
	analogWrite(y, 0);
	analogWrite(B, 255);
  	delay(1000);  
}
````

## B3 實作2-3, 讓你的RGB LED燈全彩模組也可會"呼吸", LED顏色變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動3), (2021-09-12)
![image](https://user-images.githubusercontent.com/89329299/136054194-55f890f3-2ada-4967-8958-f95e93d88d25.png)
````C
int brightness = 0;
int Red = 9;
int Blue = 11;
int Green = 10;
void setup()
{
  pinMode(Red, OUTPUT);
  pinMode(Blue, OUTPUT);  
  pinMode(Green, OUTPUT);  
  
  Serial.begin(9600); 
}
void loop()
{
  Serial.println("START");

  for (brightness = 0; brightness <= 255; brightness += 5) {
    analogWrite(Red, brightness);
    delay(50); 
  }
  for (brightness = 255; brightness >= 0; brightness -= 5) {
    analogWrite(Red, brightness);
    delay(50); 
  }
  delay(1000); 
  

  for (brightness = 0; brightness <= 255; brightness += 5) {
    analogWrite(Blue, brightness);
    delay(50); 
  }
  for (brightness = 255; brightness >= 0; brightness -= 5) {
    analogWrite(Blue, brightness);
    delay(50); 
  }  
  delay(1000); 
  

  for (brightness = 0; brightness <= 255; brightness += 5) {
    analogWrite(Green, brightness);
    delay(50); 
  }
  for (brightness = 255; brightness >= 0; brightness -= 5) {
    analogWrite(Green, brightness);
    delay(50); 
  }  
  delay(1000);   
  Serial.println("END");  
}
````

## 實作2-4 analogRead(), 1024解析度 (i.e.,10-bit): 可變電阻 + 序列監視器與輸出; 當你改變可變電阻的阻值(e.g., 10K-ohm)時，序列監視器輸出的數值有什麼改變? 數值又有什麼意義呢? 可試將你的想法寫在你的GitHub Page中喔!
![image](https://user-images.githubusercontent.com/89329299/136057272-7a768ff5-a2e7-4f6d-8ea5-397dc589e761.png)
````C
void setup() {
  Serial.begin(9600);
}

void loop() {
  // read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // Convert the analog reading (which goes from 0 - 1023) to a voltage (0 - 5V):
  float voltage = sensorValue * (5.0 / 1023.0);
  // print out the value you read:
  Serial.println(voltage);
}
````

##B5 實作2-5: 按下按鍵, Green LED亮 & Red LED滅; 放開按鍵, Green LED滅 & Red LED亮. 想要再深入的同學可以試試喔. (思考方向: digitalRead(), digitalWrite(): 按鍵 +序列輸出 + LED), (互動5) (2021-09-19) 
![image](https://user-images.githubusercontent.com/89329299/137609381-04dff9a1-0f59-4971-893f-fc2494aadbe9.png)
````C
int buttonState = 0;
int PinG = 13;
int PinR = 8;

void setup()
{
  pinMode(2, INPUT);
  Serial.begin(9600);
  
  pinMode(PinG, OUTPUT);
  pinMode(PinR, OUTPUT);

}

void loop()
{
  buttonState = digitalRead(2);
  if (buttonState == 1) {
    digitalWrite(PinG, HIGH);
    digitalWrite(PinR, LOW);
  } else {
    digitalWrite(PinG, LOW);
    digitalWrite(PinR, HIGH);
  }
  
  delay(10); 
}
````

