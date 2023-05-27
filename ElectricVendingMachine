#include "mbed.h"
#include "TextLCD.h"
#include "Servo.h"

Servo Servo1(PTC1);
AnalogIn sensor_5(PTC2);
PwmOut relay(PTB2);
AnalogIn cancel_button(PTB1);
AnalogIn exit_button(PTB0);
PwmOut red(PTE29);
int rm, cent, total;
int timer = 0;
TextLCD lcd(PTA1, PTA2, PTD4, PTA12, PTA4, PTA5, TextLCD::LCD16x2);
int main() {
  jump: lcd.cls();
  rm = cent = 0;
  relay = 1;
  wait(0.5);
  relay = 0;
  Servo1.SetPosition(1000);
  while (1) {
    Servo1.Enable(1000, 20000);
    float cancel = cancel_button.read();
    float first = sensor_5.read();
    float enter = exit_button.read();
    if ((enter > 0) && (cancel > 0)) {
      rm = rm;
      cent = cent;
      red = 0
      if (first < 1) {
        cent = cent + 5;
        wait(1);
        red = 1;
      }
      if (cent > 9) {
        cent = cent % 10;
        rm++;
      }
      lcd.locate(0, 0);
      lcd.printf("RM %d.%d0", rm, cent);
      total = (rm * 100) + (cent * 10);
      lcd.locate(0, 1);
      lcd.printf("total point:%d", total);
    } else if ((cancel == 0) && (enter > 0)) {
      lcd.cls();
      lcd.locate(0, 0);
      lcd.printf("thanks for trying");
      //for (int pos = 1000; pos < 2000; pos += 50) 
      //{
      Servo1.SetPosition(500);
      wait(0.2);
      // }
      wait(3);
      //for (int pos = 2000; pos > 1000; pos -= 50) {
      Servo1.SetPosition(1000);
      wait(0.2);
      // }
      wait(2);
      lcd.cls();
      goto jump;
    } else
      break;
  }
  lcd.cls();
  for (timer = total; timer >= 0; timer--) {
    lcd.cls();
    lcd.locate(0, 0);
    lcd.printf("%d", timer);
    wait(1);
    relay = 1;
  }
  relay = 0;
  lcd.cls();
  lcd.locate(0, 0);
  lcd.printf("time is up");
  wait(2);
  lcd.cls();
  //for (int pos = 1000; pos 2000; pos += 50) 
  // {
  Servo1.SetPosition(1500);
  wait(0.2);
  //}
  wait(3);
  //for (int pos = 2000; pos > 1000; pos -= 50) {
  Servo1.SetPosition(1000);
  wait(0.2); //}
  goto jump;
}
