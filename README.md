# smartHomeAutomation V1.0
Home Automation using Android and Arduino

You can control led or relay using this simple android app, the arduino code is:

#include <SoftwareSerial.h>
 
SoftwareSerial BTSerie(10, 11); // RX, TX
int led = 13;
int state = 0;

void setup() {
  Serial.begin(9600);
  pinMode(led, OUTPUT);
  digitalWrite(led, LOW);
  digitalWrite(9,HIGH);
  Serial.println("Enter AT commands:");
  BTSerie.begin(9600);
}
 
void loop()  
{    

if(BTSerie.available() > 0){ 
    state = BTSerie.read();
 }

if (state == '0') {
  digitalWrite(led, LOW); 
  Serial.println("LED: OFF");
  state = 0;
 }
 else if (state == '1') {
  digitalWrite(led, HIGH);
  Serial.println("LED: ON");;
  state = 0;
 } 
}  

# smartHomeAutomation V1.1 
# future release : ajout de calendrier pour automtiser l'utilisation du led ou relais ou autre ...
