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
