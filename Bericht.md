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
Die meisten Lampen in einem Haus funktionieren per Lichtschalter. Allerdings gibt es gerade im Gartenbereich bereits Lampen, die auf Bewegung reagieren und dann leuchten. Diese funktion wird durch einen Bewegungsmelder gesteuert. Dieses Projekt handelt von einem Modell, das mit Hilfe eines Bewegungssensors LEDs zum Leuchten bringt. 

### _Arduino_ 
Der Arduino ist ein kleiner Computer, genauer gesagt eine "Computing-Plattform". Auf ihr kann man eine Vielzahl an Projekten programmieren, von simplen Steuerungsprozessen, wie ein LED zum Leuchten zu bringen, bis hin zur Steuerung von anspruchsvolleren  Maschinen ist alles möglich. Den Arduino verwendet man als Steuersystem, mit dem man Abläufe automatisieren kann. Hierbei sind die Aus- und Eingänge (OutPut Pin und InPut Pin) abhängig von einander und davon, was progammiert wurde. Typischerweise wird der Arduino mit C oder C++ programmiert. 
> ![This is an image](https://m.media-amazon.com/images/I/51txW1iicVL._AC_.jpg)

### _Projekt_
Das verwendete Material umfasst einen Arduino UNO, ein Steckbrett, einen Bewegungsmelder, mehrere Jumperkabel, zwei LEDs und einen Karton. Die LEDs werden über den Bewegungsmelder gesteuert. Registriert dieser etwas, fangen die LEDs an zu leuchten. Das gebaute Modell dient zur Veranschaulichung: der Karton stellt einen Lampe dar, die durch die LEDs erleuchtet wird. Dies geschieht, wenn der Bewegungsmelder, der außen am Modell befestigt ist, eine Bewegung erfasst und somit die LEDs im Inneren zum Leuchten bringt. 

### _Bewegungsmelder_ 
Der HC-SR501 verwendet einen PIR–Bewegungsmelder. Diese Abkürzung steht für „Passiv Infrarot Sensor“, das heißt, dass er Infrarotstrahlung wahrnimmt. Hat er eine Bewegung registriert, gibt er auf einem Pin eine Spannung von 5 Volt aus (das sog. HIGH-Signal). Diese wird dann vom Microcontroller ausgelesen und verarbeitet. Dann gibt es noch drei weitere Einstellungen des HC-SR501: „Time Delay Adjust“ (Ausschaltverzögerung), „Sensitivity Adjust“ (Sensitivität), „Trigger Selection“ (Jumper Ein-/ Ausschalter). 
Mit dem „Time Delay Adjust“ kann eingestellt werden, wie lange der Output Pin nach einer registrierten Bewegung ein HIGH-Signal ausgeben soll. 
Mit dem „Sensitivity Adjust“ lässt sich die Reichweite (3-7 Meter), innerhalb derer der Sensor Bewegung bemerken kann, regulieren. 
Mit der „Trigger Selection“ lässt sich einstellen, ob der Bewegungssensor mehrmals oder nur einmal ausgelöst werden soll. 
> ![grafik](https://user-images.githubusercontent.com/111414662/230464502-99120b94-535f-42a9-ac18-902fdde69b81.png)


### _Code_ 
Die zum Codieren verwendete Programmiersprache ist C. 

Zuerst werden drei Variablen durch einem kostanten Wert definiert. Jede der Variablen bestimmt einen Output Pin. Die Verwendung von Konstanten im Code hat den Zweck, den Code verstehbarer zu machen und bei Änderungen eines Wertes muss diese Änderung nur einmal im Code übernommen werden.  

<details>
	<summary>Ausschnitt des Codes</summary>
	
```J
const int LED1 = 5; // Die LED1 (blau) ist an Pin 5 angeschlossen
const int LED2 = 4; // Die LED2 (grün) ist an Pin 4 angeschlossen  
const int bewegung = 7; //  Der Bewegungssensor an Pin 7   
```	
</details> 


Die „setUp“-Funktion bereitet das System vor, indem sie Pin 4 und 5, die den LEDs zugeordnet sind, als Ausgang definiert und Pin 7, der mit dem Bewegungssensor verknüpft ist, als Eingang. Des Weiteren wird der Grundzustand der LEDs als „LOW“ festgelegt, was bedeutet, dass sie zunächst ausgeschaltet sind und somit nicht leuchten. 
Außerdem wurde hier ein Counter für den Bewegungssensor programmiert, da letztgenannter  eine Minute zum Hochfahren braucht. Wird das Programm hochgeladen, so wird im Serial Monitor die Anweisung „Initialising Sensor“ geprinted. Dann beginnt ein Counter zu laufen, der mit Hilfe einer „for“-Schleife funktioniert. Jedes Mal, wenn der Counter eine 10-er Stufe erreicht, wird die verbleibende Zeit ausgegeben. Auf diese Weise zählt er von 60 runter und die Ergebnisse werden im Serial Monitor geprinted. Ist der Sensor einsatzbereit, erscheint die Textzeile „Ready to use“, mit der  dies angezeigt wird. 

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
	

Die Befehle, die in der  „loop“-Funktion geschrieben sind, werden in einer Endlosschleife wiederholt. Das bedeutet, dass, sobald alle Befehle einmal durchlaufen wurden, sie erneut ausgeführt werden. 
	
Hierbei wird der Status des Bewegungssensors im Serial Monitor geprinted. Wenn eine 1 ausgegeben wird, dann bedeutet das, dass der Bewegungssensor eine Bewegung registriert hat, und wenn eine 0 ausgegeben wird, dann bedeutet das, dass eben keine Bewegung wahrgenommen wurde. 

Des Weiteren werden die LEDs so instruiert, dass, wenn der Bewegungssensor eine Bewegung wahrgenommen hat, diese dann vom Ausgangsstatus „LOW“ auf den Status „HIGH“ gesetzt werden. Das bringt sie zum Leuchten. 
	
Der Lichtschein hält für eine Zeitspanne von ca. 10 Sekunden an und erlischt dann wieder. Die LEDs leuchten erst dann wieder, wenn ihr Status von „LOW“ auf „HIGH“ durch eine vom Bewegungssensor registrierte Bewegung gesetzt wird. 
	
Falls der Sensor allerdings nichts registriert, bleiben die LEDs 1 und 2 in ihrem Ausgangzustand, also ausgeschaltet. 

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

Dieses Projekt hat gezeigt, dass es gut möglich ist, Lampen (oder in diesem Falle LEDs) mit Hilfe eines Bewegungsmelders zu steuern. Heutzutage werden Häuser und Wohnungen mit immer mehr Technik ausgestattet wie mit virtuellen Sprachassistenten (Alexa, Google Home, etc.).Außerem kommen immer mehr intelligenten Systeme wie „smartHome“, mit denen eine Steuerung von Fernsehern, Lampen und anderen elektronischen Geräten möglich ist, zum Einsatz. 
	
Lampen, die auf Bewegung reagieren, haben einen großen praktischen Nutzen  und stellen eine Bereicherung sowie Vereinfachung des täglichen Lebens dar. Somit werden sie in der Zukunft sicherlich noch flächendeckender eingesetzt werden.
Außerdem sind bewegungsgesteuerte Lampen enegriesparend, da sie sich ausschalten, sobald jemand den Raum verlässt. Gerade in unserer heutigen Welt, in der Nachhaltigkeit und Stromsparen wichtig sind, sind bewegungsgesteuerte Lampen eine gute Lösung. 
	
### _Quellen_
> https://www.conrad.de/de/ratgeber/entwicklungskits-bausaetze/arduino.html

>https://www.google.com/search?q=arduino+uno&client=firefox-b-d&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjM9eyspbr9AhUzcfEDHfJ2DvMQ_AUoAnoECAEQBA&biw=1600&bih=709&dpr=1.2#imgrc=qpMv2fTCPq9OJM
	
> https://starthardware.org/
	
> https://starthardware.org/arduino-serial-print/
	
> https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-serial-monitor
	
> https://blog.berrybase.de/blog/2020/05/26/arduino-einstieg-in-microcontroller-mit-dem-bewegungsmelder-sensor-hc-sr501/#HC-SR501_PIR_Sensor_-_Infrarot_Bewegungsmelder
	
> https://funduino.de/nr-8-bewegungsmelder	
