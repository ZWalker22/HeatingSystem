#include <LiquidCrystal.h> 
#include "cactus_io_DS18B20.h" 
int DS18B20_Pin = 9; 
DS18B20 ds(DS18B20_Pin); 
int Contrast=20;
const int buttonPin = 7;
int buttonState = 0;
const int buttonPin2 = 8;
int buttonState2 = 0;
float temp = (27.00);
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);   

 void setup()
 { 
    analogWrite(6,Contrast);
    Serial.begin(9600);
     lcd.begin(16, 2);
     lcd.setCursor(0, 0);
     lcd.print("TURNING ON");   
    lcd.setCursor(0, 1);
    lcd.print("PLEASE WAIT");
    delay(1000);
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Left = cool");
    lcd.setCursor(0, 1);
    lcd.print("Right = heat");
    delay(3000);
    pinMode(buttonPin, INPUT);
    pinMode(buttonPin2, INPUT);
    lcd.print(temp);
    lcd.clear();
  }  
     void loop()
 {  
    ds.readSensor();
    buttonState = digitalRead(buttonPin);
    buttonState2 = digitalRead(buttonPin2);
    lcd.setCursor(0,0);
    lcd.print("");
    lcd.print(ds.getTemperature_C()); lcd.print(" *C");
    if (buttonState == HIGH){
      lcd.setCursor(0, 1);
      lcd.print(temp --);
    }
    if (buttonState2 == HIGH){
      lcd.setCursor(0, 1);
      lcd.print(temp ++);
    }
    lcd.setCursor(0, 1);
    lcd.print("Set = "); lcd.print(temp); lcd.print(" *C");
    lcd.setCursor(0, 0);
    if (temp < ds.getTemperature_C()) {
      delay(1000);
      lcd.print(" Cooling");
      delay(1000);
    }
    
    if (temp > ds.getTemperature_C()) {
      delay(1000);
      lcd.print(" Heating");
      delay(1000);
    }
 }
 
