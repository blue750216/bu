#嵌入式系統 - 實作4: 七段顯示器, LCD 顯示器 + 超音波感測器 (W7, W9)
##Lab 4-1 用七段顯示器來顯示數字"8."
![image](https://user-images.githubusercontent.com/89329299/137610615-6c96ecd8-3514-41bf-8a1a-6ec3d829f9eb.png)
````C
void setup()
{
for(int x = 1; x < 9; x++) {
pinMode(x,OUTPUT);
}
}

void seg71(int a, int b, int c, int d, int e, int f, int g, int h)
{
digitalWrite(1, a);
digitalWrite(2, b);
digitalWrite(3, c);
digitalWrite(4, d);
digitalWrite(5, e);
digitalWrite(6, f);
digitalWrite(7, g);
digitalWrite(8, h);
delay(500);
}

void loop()
{
//    a, b, c, d, e, f, g, h
seg71(0, 0, 0, 0, 0, 0, 0, 0); // OFF
seg71(1, 1, 1, 1, 1, 1, 1, 1); // 8
}
````
