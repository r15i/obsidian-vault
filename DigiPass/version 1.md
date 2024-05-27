
loosely based on 
https://github.com/chris408/digispark-usbkey-board


``` C 
#include "DigiKeyboard.h"

  

void setup() {

  // don't need to set anything up to use DigiKeyboard

}

  

void loop() {

  // this is generally not necessary but with some older systems it seems to

  // prevent missing the first character after a delay:

  // It's better to use DigiKeyboard.delay() over the regular Arduino delay()

  // if doing keyboard stuff because it keeps talking to the computer to make

  // sure the computer knows the keyboard is alive and connected

  DigiKeyboard.delay(3000);//5 second delay

  DigiKeyboard.sendKeyStroke(0);

  DigiKeyboard.print("Password");//to note that the keys need to be conformant to the keyboard layout we are using

}
```
