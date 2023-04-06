# **Arduino-Projektbericht** 

## **_Inhaltsverzeichnis_** 
- [1) Einleitung](#einleitung)
- [2) Arduino](#arduino)
- [3) Projekt](#projekt) 
- [4) Bewegungsmelder](#bewegungsmelder)
- [5) Code](#code) 
- [6) Fazit](#fazit) 
- [7) Quellen](#quellen) 

### _Einleitung_
Die meisten Lampen in einem Haus funktionieren per Lichtschalter. Allerdings gibt es gerade im Gartenbereich bereits Lampen, die auf Bewegung reagieren und dann leuchten. Dies ist ihnen mithilfe eines eingebauten Bewegungssensors möglich. Dieses Projekt handelt von einem Modell, welches mit Hilfe eines Bewegungssensors LEDs zum Leuchten bringt. 

### _Arduino_ 
Der Arduino ist ein kleiner Computer, genauer gesagt eine "Computing-Plattform", mit deren Hilfe man von kleinen Projekten - wie ein LED zum Leuchten bringen - bis zur Maschinensteuerung alles mögliche programmieren und machen kann. Den Arduino kann man als Steuersystem verwenden, mit dem man Abläufe automatisieren kann. Hierbei sind die Aus- und Eingänge (OutPut Pin und InPut Pin) abhängig von einander und dem, was progammiert wurde. Typischerweise wird der Arduino mit C oder C++ programmiert. 
> ![This is an image](https://m.media-amazon.com/images/I/51txW1iicVL._AC_.jpg)

### _Projekt_
Das verwendete Material umfasst einen Arduino UNO, ein Steckbrett, einen Bewegungsmelder, mehrere Jumperkabel, zwei LEDs und einen Karton. Die LEDs werden über den Bewegungsmelder gesteuert; registriert dieser etwas, fangen die LEDs an zu leuchten. Das gebaute Modell dient zur Veranschaulichung: der Karton stellt einen Lampe dar, die durch die LEDs erleuchtet wird. Dies passiert dann, wenn der Bewegungsmelder – welcher außen am Modell befestigt ist – eine Bewegung bemerkt und somit die LEDs im Inneren zum Leuchten bringt. 

### _Bewegungsmelder_ 
Der HC - SR501 verwendet einen PIR – Bewegungsmelder, was für „Passiv Infrarot Sensor“ steht. Das bedeutet, dass er Infrarotstrahlung wahrnimmt. Hat er eine Bewegung registriert, dann gibt er auf einem Pin eine Spannung von 5 Volt aus. Diese wird dann vom Microcontroller ausgelesen und verarbeitet. Dann gibt es noch drei weitere Einstellungen des HC - SR501: „Time Delay Adjust“ (Ausschaltverzögerung), „Sensitivity Adjust“ (Sensitivität), „Trigger Selection“ (Jumper Ein-/ Ausschalter). 
Mit dem „Time Delay Adjust“ kann eingestellt werden, wie lange der Output Pin nach einer registrierten Bewegung ein HIGH-Signal ausgeben soll. 
Mit dem „Sensitivity Adjust“ lässt sich die Reichweite (3-7 Meter) in der der Bewegungssensor Bewegung bemerken kann regulieren. 
Mit der „Trigger Selection“ lässt sich einstellen, ob der Bewegungssensor mehrmals oder nur einmal ausgelöst werden soll. 


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
	
> https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-serial-monitor
	
> https://blog.berrybase.de/blog/2020/05/26/arduino-einstieg-in-microcontroller-mit-dem-bewegungsmelder-sensor-hc-sr501/#HC-SR501_PIR_Sensor_-_Infrarot_Bewegungsmelder
	
> https://funduino.de/nr-8-bewegungsmelder	
