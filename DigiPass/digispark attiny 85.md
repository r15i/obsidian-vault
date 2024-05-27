![[Pasted image 20240208161204.jpg]]

1. download arduino ide 
2. install digistomp drivers (https://github.com/digistump/DigistumpArduino/releases/download/1.6.7/Digistump.Drivers.zip) (i have a backup in the folder of the project)
3. add in url aggiuntive per le librerie http://digistump.com/package_digistump_index.json
4. selezionare board (Default-16.5 mhz)
5. compile 
6. insert 
7. wait upload

## Sample code 
``` c
void setup() {

 pinMode(1, OUTPUT); 

 } 

 void loop() { 

 digitalWrite(1, HIGH); 

 delay(500); 

 digitalWrite(1, LOW); 

 delay(500); 

 } 
```
