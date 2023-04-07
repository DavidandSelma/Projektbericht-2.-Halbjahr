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
> ![grafik](https://user-images.githubusercontent.com/111414662/230464502-99120b94-535f-42a9-ac18-902fdde69b81.png)


### _Code_ 
Die zum Codieren verwendete Programmiersprache ist C. 

Hier sind zunächst einmal drei Variabel Funktionen. Jede der Variablen definiert einen Output Pin, dies hat den Zweck, dass man den Wert, der der jeweiligen Variable zugeordnet ist, nur einmal am Anfang des Codes definieren muss.  

<details>
	<summary>Ausschnitt des Codes</summary>
	
```J
  
 const int LED1 = 5; // Die LED1 (blau) ist an Pin 5 angeschlossen
const int bewegung = 7; //  Der Bewegungssensor an Pin 7 
const int LED2 = 4; // Die LED2 (grün) ist an Pin 4 angeschlossen  
  
  ```	
</details> 


Die „Void SetUp“ - Funktion bereitet das System vor, indem sie Pin 4 und 5, die den LEDs zugeordnet sind, als Ausgang definiert und Pin 7, der mit dem Bewegungssensor verknüpft ist, als Eingang. 
Des Weiteren wird der Grundzustand der LEDs als „LOW“ definiert, was bedeutet, dass sie zunächst aus sind und somit nicht leuchten. 
Außerdem wurde hier ein Counter für den Bewegungssensor programmiert, der nämlich eine Minute zum Hochfahren braucht. Wird das Programm hochgeladen, so wird im Serial Monitor die Anweisung „Initialising Sensor“ geprinted. Dann geht ein Counter los, der mit Hilfe einer „for“ - Schleife funktioniert. Jedes Mal, wenn der Counter eine 10-er Stufe erreicht, wird dann die verbleibende Zeit ausgegeben, so zählt er dann von 60 runter und die Ergebnisse werden im Serial Monitor geprinted. Ist der Sensor einsatzbereit, dann erscheint die Textzeile „Ready to use“, mit der eben dies signalisiert wird. 

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
	
	
Die Befehle, die im „Void Loop“ festgeschrieben sind, werden in einer endlosschleife wiederholt. Das bedeutet, dass sobald alle Befehle einmal durchlaufen wurden sie erneut ausgeführt werden. 
Hierbei wird der Status des Bewegungssensors im Serial Monitor geprinted. Wenn eine 1 ausgegeben wird, dann bedeutet das, dass der Bewegungssensor eine Bewegung registriert hat und wenn eine 0 ausgegeben wird, dann bedeutet das, dass eben keine Bewegung wahrgenommen wurde. 
Des Weiteren werden die LEDs so instruiert, dass wenn der Bewegungssensor eine Bewegung wahrgenommen hat, diese dann vom Ausgangsstatus „Low“ auf den Status „High“ gesetzt werden, sie leuchten nun also. 
Das Leuchten hält für eine Zeitspanne von ca. 10 Sekunden an und geht dann wieder aus und die LEDs leuchten erst dann wieder, wenn ihr Status von „Low“ auf „High“ durch eine vom Bewegungssensor registrierte Bewegung gesetzt wird. 
Falls der Sensor allerdings nichts registriert, bleiben die LEDs 1 und 2 in ihrem Ausgangzustand, also aus. 

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

Dieses Projekt hat also gezeigt, dass es gut möglich ist, Lampen (oder in diesem Falle LEDs) mit Hilfe eines Bewegungsmelders zu steuern. Heutzutage werden Häuser und Wohnungen mit immer mehr Technik ausgestattet, wie mit virtuellen Sprachassistenten (Alexa, Google Home etc.) und intelligenten Systemen, wie „smartHome“, mit denen eine Steuerung von Fernseher, Lampen und anderen elektronischen Geräten möglich ist. 
Lampen die auf Bewegung reagieren, sind nun mal sehr praktisch und eine Bereicherung sowie Vereinfachung des täglichen Lebens. Somit werden sie in der Zukunft sicherlich flächendeckender eingesetzt werden, sodass man um seine Licht einzuschalten lediglich die Hand bewegen muss. 
	
### _Quellen_
> https://www.conrad.de/de/ratgeber/entwicklungskits-bausaetze/arduino.html

>https://www.google.com/search?q=arduino+uno&client=firefox-b-d&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjM9eyspbr9AhUzcfEDHfJ2DvMQ_AUoAnoECAEQBA&biw=1600&bih=709&dpr=1.2#imgrc=qpMv2fTCPq9OJM
	
> https://starthardware.org/
	
> https://starthardware.org/arduino-serial-print/
	
> https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-serial-monitor
	
> https://blog.berrybase.de/blog/2020/05/26/arduino-einstieg-in-microcontroller-mit-dem-bewegungsmelder-sensor-hc-sr501/#HC-SR501_PIR_Sensor_-_Infrarot_Bewegungsmelder
	
> https://funduino.de/nr-8-bewegungsmelder	
