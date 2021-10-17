# 嵌入式系統 - 實作4: 七段顯示器, LCD 顯示器 + 超音波感測器 (W7, W9)
## Lab 4-1 用七段顯示器來顯示數字"8."
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
#Lab 4-2 如下圖的Demo, 用七段顯示器, 顯示 . →1→ ... → 9 → 0 → 全滅, 狀態改變的間隔時間為0.5秒
![chrome-capture (4-2)](https://user-images.githubusercontent.com/89329299/137611068-d80f7191-0dd5-4d16-b71d-bc5f79154550.gif)
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
seg71(0, 0, 0, 0, 0, 0, 0, 1); // OP
seg71(0, 1, 1, 0, 0, 0, 0, 1); // 1
seg71(1, 1, 0, 1, 1, 0, 1, 1); // 2  
seg71(1, 1, 1, 1, 0, 0, 1, 1); // 3  
seg71(0, 1, 1, 0, 0, 1, 1, 1); // 4  
seg71(1, 0, 1, 1, 0, 1, 1, 1); // 5 
seg71(1, 0, 1, 1, 1, 1, 1, 1); // 6
seg71(1, 1, 1, 0, 0, 0, 0, 1); // 7
seg71(1, 1, 1, 1, 1, 1, 1, 1); // 8
seg71(1, 1, 1, 1, 0, 1, 1, 1); // 9
seg71(1, 1, 1, 1, 1, 1, 0, 1); // 0
}
````
## Lab 4-3 LCD顯示"Hello" + 你的英文名字 (e.g., "Hello Horace")
![chrome-capture (1)](https://user-images.githubusercontent.com/89329299/137612075-2e27ba02-587f-4c53-9ff0-976ce5f7175d.gif)
````C
// include the library code:
#include <LiquidCrystal.h>

// initialize the library with the numbers of the interface pins
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
  // Print a message to the LCD.
  lcd.print("hello, BUBU!");
}

void loop() {
  // set the cursor to column 0, line 1
  // (note: line 1 is the second row, since counting begins with 0):
  lcd.setCursor(0, 1);
  // print the number of seconds since reset:
  lcd.print(millis() / 100);
}
````
