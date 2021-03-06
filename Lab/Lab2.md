# Lab2 會呼吸的RGB LED,  按鍵控制, 狀態輸出

#### 目錄
<a name="000"/>

##### [2-1 觀查LED亮度變化是否有像"呼吸的效果"且跟示波器有關聯性](#001)
##### [2-2 讓LED輪流表現正紅、正綠、正藍，三個顏色,觀查LED顏色和波形或是電壓有什麼關連性](#002)
##### [2-3 讓RGB LED燈全彩模組也可會"呼吸" LED顏色變化是否有像"呼吸的效果"和示波器的波形有什麼關連](#003)
##### [2-4 當你改變可變電阻的阻值時，序列監視器輸出的數值有什麼改變?](#004)
##### [2-4  按下按鍵, G LED亮 & R LED滅; 放開按鍵, G LED滅 & R LED亮](#005)

<a name="001"/>

## 2-1 analogWrite(): 並且觀查LED亮度變化是否有像"呼吸的效果"和示波器的波形有什麼關連性?

![image](https://user-images.githubusercontent.com/89327102/132112778-84441431-1758-4613-841f-012d42b53cea.png)

### 程式

````c
int brightness = 0;

void setup()
{
  pinMode(9, OUTPUT);
}

  for (brightness = 0; brightness <=255; brightness +=5){
       analogWrite(9, brightness);
       delay(30); 
  }    
  
  for (brightness = 255; brightness >=0; brightness -=5){
       analogWrite(9, brightness);
       delay(30); 
  }
}
````

<a name="002"/>

## 2-2 RGB LED燈全彩模組, 分別讓LED輪流表現正紅、正綠、正藍，三個顏色，時間間隔1秒鐘。並且觀查LED顏色和波形或是電壓有什麼關連性?

![螢幕擷取畫面 2021-09-05 223042](https://user-images.githubusercontent.com/89327102/132130600-05502901-eeea-49e2-808c-841dabce77f7.jpg)

### 程式

````c
const int R = 9 ;
const int G = 10 ;
const int B = 11 ;

  void setup()
{
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);
}

void loop()
{
  analogWrite(R,255);
  analogWrite(G,0);
  analogWrite(B,0);
    
    delay(1000);
  analogWrite(R,0);
  analogWrite(G,255);
  analogWrite(B,0);
    
    delay(1000); 
  analogWrite(R,0);
  analogWrite(G,0);
  analogWrite(B,255);
  
   delay(1000); 
}
````
<a name="003"/>

## 2-3, 讓你的RGB LED燈全彩模組也可會"呼吸", LED顏色變化是否有像"呼吸的效果"和示波器的波形有什麼關連性?

![螢幕擷取畫面 2021-09-12 095531](https://user-images.githubusercontent.com/89327102/132968047-973ca7d8-449f-4aac-ab43-09035f634c7d.jpg)

### 程式

````c
const int R = 9 ;
const int G = 10 ;
const int B = 11 ;
int brightness = 0;

  void setup()
{
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);
}

void loop()
{
 for (brightness = 0; brightness <=255; brightness +=5){
       analogWrite(R,255);
  analogWrite(G,0);
  analogWrite(B,0);
    
    delay(1000);
  analogWrite(R,0);
  analogWrite(G,255);
  analogWrite(B,0);
    
    delay(1000); 
  analogWrite(R,0);
  analogWrite(G,0);
  analogWrite(B,255);
  
   delay(1000); 
  }    
  
  for (brightness = 255; brightness >=0; brightness -=5){
  analogWrite(R,255);
  analogWrite(G,0);
  analogWrite(B,0);
   
    delay(1000);
  analogWrite(R,0);
  analogWrite(G,255);
  analogWrite(B,0);
    
    delay(1000); 
  analogWrite(R,0);
  analogWrite(G,0);
  analogWrite(B,255);
  
   delay(1000); 
  }
  }
  ````
  <a name="004"/>
  
## 2-4 analogRead(), 1024解析度 (i.e.,10-bit): 可變電阻 + 序列監視器與輸出; 當你改變可變電阻的阻值(e.g., 10K-ohm)時，序列監視器輸出的數值有什麼改變? 數值又有什麼意義呢? 

![螢幕擷取畫面 2021-09-12 101308](https://user-images.githubusercontent.com/89327102/132969182-dc6e62d5-f8c2-4b5a-97d0-4e34babd9fda.jpg)
![螢幕擷取畫面 2021-09-12 103055](https://user-images.githubusercontent.com/89327102/132969544-e900d31d-0599-4c05-a1b3-cf855b982c22.jpg)

### 程式

````c


int sensorValue = 0;

void setup()
{
  pinMode(A0, INPUT);
  Serial.begin(9600);
 
}

void loop()
{
  
  sensorValue = analogRead(A0);
 
  Serial.println(sensorValue);
 
  delay(10); 
}
````
<a name="005"/>

## 2-5 按下按鍵, Green LED亮 & Red LED滅; 放開按鍵, Green LED滅 & Red LED亮.

![螢幕擷取畫面 2021-09-19 094126](https://user-images.githubusercontent.com/89327102/133912790-27317b7f-d28a-45c1-9f45-d1316ccb50de.jpg)
![螢幕擷取畫面 2021-09-19 095257](https://user-images.githubusercontent.com/89327102/133912941-898f0c5a-9ced-4019-be72-6ded11ecd82c.jpg)

### 程式

````c


int buttonState=0;

void setup()
{
  pinMode(2, INPUT);
  pinMode(8, INPUT); // R
  pinMode(7, INPUT); // G
  Serial.begin(9600);
}

void loop()
{
  if(buttonState == HIGH){
    digitalWrite(7, HIGH);
    digitalWrite(8, LOW);
  }
  if(buttonState == LOW){
    digitalWrite(8, HIGH);
    digitalWrite(7, LOW);
  }
  buttonState = digitalRead(2);
  Serial.println(buttonState);
  delay(10);
}
````

##### [TOP](#000)
