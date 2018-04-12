```javascript
#include <LiquidCrystal.h>

const int LED = 13, rs = 12, en = 11, d10 = 10, d9 = 9, d8 = 8, d7 = 7;
LiquidCrystal lcd(rs, en, d10, d9, d8, d7);

void setup() {
  pinMode(LED, OUTPUT);
  lcd.begin(16, 4);
  lcd.print("Hello!");

  lcd.autoscroll();
}

int counter = 0;
int fllwng = 0;

void loop() {
  if (counter <= 2){
  lcd.noDisplay();
  digitalWrite(LED, LOW);
  delay(300);
  // Turn on the display:
  lcd.display();
  digitalWrite(LED, HIGH);
  delay(300);
  counter = counter + 1;
  }
  else{
    fllwng = 1;
  }
  if (fllwng == 1){
    lcd.setCursor(0, 0);
    lcd.print("Hallo");
    delay(300);
  }
}
```
