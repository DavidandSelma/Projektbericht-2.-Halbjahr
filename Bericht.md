# **Arduino-Projektbericht** 

## **_Inhaltsverzeichnis_** 
- [1) Arduino](#arduino)
- [2) Projekt](#projekt) 
- [3) Code](#code) 
- [4) Fazit](#fazit) 
- [5) Quellen](#quellen) 

### _Arduino_ 
Arduino ist ein kleiner Computer, genauer gesagt eine "Computing-Plattform", mit Hilfe der man von kleinen Projekten - wie ein LED zum Leuchten bringen - bis zur Maschinensteuerung alles mögliche programmieren und machen kann. Den Arduino kann man als Steuersystem verwenden, mit dem man Aläufe automatisieren kann. Hierbei sind die Aus- und Eingänge abhängig von einander und dem, was progammiert wurde. Typischerweise wird der Arduino mit C oder C++ programmiert. 
> ![This is an image](https://m.media-amazon.com/images/I/51txW1iicVL._AC_.jpg)

### _Projekt_

### _Code_ 
Die hier verwendete Programmiersprache ist C. 

<details>
	<summary>Ausschnitt des Codes</summary>
	
```J
  
 const int LED1 = 5; // Die LED1 (blau) ist an Pin 5 angeschlossen
const int bewegung = 7; //  Der Bewegungssensor an Pin 7 
const int LED2 = 4; // Die LED2 (grün) ist an Pin 4 angeschlossen  
  
  ```	
</details> 


<details>
	<summary>Ausschnitt des Codes</summary>
	
```J

void setup() {
  Serial.begin(9600); 
  pinMode(LED1, OUTPUT); // Pin 5 dient als Ausgang
  pinMode(LED2, OUTPUT); // Pin 4 dient als Ausgang
  pinMode(bewegung, INPUT); // Pin 7 als Eingang
  digitalWrite(LED1, LOW); // Grundzustand: aus 
  digitalWrite(LED2, LOW); // Grundzustand: aus 
  Serial.println("Initialising Sensor!"); // wird geprinted 
  for(int i = 0; i<=60;i++ ){ //Wiederholung: 60 mal; i = Zähler, der bis 60 hochzählt
    if(i%10 == 0) { // wenn der Zähler eine 10-er-Stufe erreicht hat, wird die verbleibende Zeit ausgegeben (10, 20 etc.)
      Serial.print(60-i);
      Serial.println(" Sekunden verbleibend."); // wird ausgegeben 

    }
    delay(1000);


  }
  Serial.println("Ready to use!"); // wenn der Zähler durch ist und somit der Sensor initialisiert ist, dann ist der Sensor einsatzbereit 
}	
	
```	
</details> 
	
	
<details>
	<summary>Ausschnitt des Codes</summary>
	
```J
	

void loop() {
  int bewegungsstatus = digitalRead(bewegung); // liest die Ausgabe des Bewegungssensors (1 = Bewegung; 0 = keine Bewegung)
  Serial.println(bewegungsstatus);
  delay(1000); // 1 Sekunde Pause 
  if (bewegungsstatus == HIGH) // Nimmt der Sensor eine Bewegung war, werden die LEDS auf den Status "High" gesetzt. 
  { 
    digitalWrite(LED1, HIGH); 
    digitalWrite(LED2, HIGH);                    
    
  } 
  else                
  { 
    digitalWrite(LED1, LOW); // Nimmt der Sensor nichts war, verbleibt der LED1 in seinem Zustand
    digitalWrite(LED2, LOW);
  } 
}	
	
```	
</details> 

### _Fazit_ 

### _Quellen_
> https://www.conrad.de/de/ratgeber/entwicklungskits-bausaetze/arduino.html

>https://www.google.com/search?q=arduino+uno&client=firefox-b-d&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjM9eyspbr9AhUzcfEDHfJ2DvMQ_AUoAnoECAEQBA&biw=1600&bih=709&dpr=1.2#imgrc=qpMv2fTCPq9OJM
	
> https://starthardware.org/
	
> https://starthardware.org/arduino-serial-print/
	
>https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-serial-monitor
	
>
