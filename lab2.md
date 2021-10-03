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
