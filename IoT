# Spider-IOT
Task one code

  #include <ESP8266WiFi.h>
  #include <ThingSpeak.h> //cloud service library
const int trigP = 2;  //D4 Or GPIO-2 of nodemcu
const int echoP = 0;  //D3 Or GPIO-0 of nodemcu
long duration;
int distance;
int level; 
WiFiClient client;
long IOT_channel=1134199; //channel code from ThingSpeak
const char key[]= "8FGO2A27YDW5HTHA";

void setup() {
pinMode(trigP, OUTPUT);  // Sets the trigPin as an Output
pinMode(echoP, INPUT);   // Sets the echoPin as an Input
Serial.begin(9600);
WiFi.begin("Aryan","12345678"); //My wifi name and password
while(WiFi.status()!= WL_CONNECTED)//while loop to check wifi connectivity 
{
  delay(3000);
  Serial.print("Not connected");
}
Serial.println("Yes! , now connected");
ThingSpeak.begin(client);
}
void loop()
{
  digitalWrite(trigP, LOW);   // Makes trigPin low
delayMicroseconds(2);       // 2 micro second delay

digitalWrite(trigP, HIGH);  // tigPin high
delayMicroseconds(10);      // trigPin high for 10 micro seconds
digitalWrite(trigP, LOW);   // trigPin low

duration = pulseIn(echoP, HIGH);   //Read echo pin, time in microseconds
distance= duration*0.034/2; //Distance measured from duration
level = -100/45*distance +111.11; //Level in percentage, here, at 5c.m. the tank is full and at 50 c.m. it is empty.
  Serial.println("Level : " + (String) level + "%"); //printing level in serial monitor
  ThingSpeak.writeField(IOT_channel,1,level,key); // Sending level to cloud server for plotting the graph.
  delay(1500);
  
}

