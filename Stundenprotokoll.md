# (1) 10.01.2023

Heute war unsere erste Informatikstunde nach den Ferien und es geht in die zweite Runde. Da unser altes Projekt ja abgeschlossen war und wir Lust auf etwas Neues haben, haben wir heute damit begonnen uns nach einer neuen Projektidee umzuschauen. Hierzu haben wir zunächst bei den alten Projekten ehemaliger Schüler nachgeschaut, um uns Inspiration zu holen. Wir wissen zwar noch nicht, was wir genau als unser nächstes Projekt in Angriff nehmen wollen, haben uns aber schon gegen ein Spiel in Greenfoot, mit Snap oder Scratch entschieden. 
Unsere erste Überlegung ist es nun etwas in die Richtung "Physical Computing" mithilfe von Arduino zu machen. Des Weiteren würden wir hierbei gerne wieder mit Java coden. In den nächsten Stunden planen wir nun uns genauer mit Physical Computing und möglichen Projektideen auseinanderzusetzen.  

# (2) 11.01.2023

In der heutigen Stunde haben wir damit gestartet, uns zu überlegen, ob ein "Raspberry Pi" oder ein "Arduino" günstiger für uns zum programmieren ist. Hierzu haben wir uns im Internet zu den Unterschieden zwischen den beiden mini-Computern informiert. 

> https://www.techtag.de/it-und-hightech/arduino-vs-raspberry-pi-wo-liegt-der-unterschied/

Dann haben wir uns zunächst einmal über mögliche Projekte mit Arduino auseinandergesetzt. Hierfür haben wir nach Projektbeispielen im Internet gesucht. 

> https://www.ionos.de/digitalguide/server/knowhow/arduino-projekte-ideen-beispiele-fuer-arduino-uno-nano/

Danach haben wir uns auch über Projekte mit Raspberry Pi informiert, um zu schauen, was alles so möglich ist. 

> https://tutorials-raspberrypi.de/raspberry-pi-projekte-fuer-anfaenger-zum-nachbauen/

Dann haben wir Arduino auf unserem Laptop installiert, um den Code programmieren zu können. 
Eigentlich wollten wir im 2. Teil der heutigen Stunde schonmal den Arduino anschließen und ein LED per Knopfrdruck zum Leuchten bringen, allerdings gab es keine Steckbrette mehr und von daher konnten wir dieses Vorhaben nicht umsetzen. Mit den Krokodilklammern mit denen wir arbeiten sollten kamen wir nämlich nicht so gut zurecht. 
Deshalb haben wir stattdessen die Anfänge mit Arduino geübt und uns zu diesem Zweck mehrere Tutorials angeschaut. 

> https://starthardware.org/

# (3) 17.01.2023

Heute haben wir uns noch weiter mit unserem Projekt beschäftigt. Unser Projekt soll in etwa so aussehen: eine Lampe geht an, entweder mithilfe eines Bewegungssensors, der Bewegung wahrnimmt oder mithilfe eines Wärmesensors, der Infrarotstrahlung, also Wärme, registriert. Abhängig davon, was besser funktioniert, entscheiden wir uns die nächsten Stunden genau wie unser Projekt aussehen soll. 
Anonsten haben wir heute weiter Recherche zu Arduino und dem Arbeiten mit Arduino beschäftigt; noch sind wir sehr gespannt, wie wir das so hinbekommen, da unser altes Projekt ja nichts mit physical computing zu tun hatte. 

# (4) 18.01.2023

Heute haben wir uns nun an Arduino herangewagt und erste kleine Versuche unternommen, dadurch, dass wir bereits mit Greenfoot gearbeitet hatten, war uns Java schon etwas geläufiger. Zunächst haben wir mithilfe des Arduinos und Krokodilklammern ein LED zum Leuchten gebracht. Außerdm haben wir einen Arduino-Dimmschalters angebracht und die Spannung des Arduinos (0V - 5V) damit gemessen, indem wir den Widertand erhöht haben. Danach haben wir den Widerstand des Dimschalters gemessen. Anschließend haben wir versucht die Teilspannug des Arduinos durch den Dimschalter digital einzulesen, mit dem "Serial Monitor".

> ![grafik](https://user-images.githubusercontent.com/111414662/213119963-d4e1d268-f1b5-4654-a84a-52813ae486ed.png)

> ![grafik](https://user-images.githubusercontent.com/111414662/213120056-37aa18b0-5346-46fc-b273-fdb922730cc1.png)


Als Hilfestellung haben wir uns im Internet auf verschiedenen Seiten informiert.

> ![grafik](https://user-images.githubusercontent.com/111414662/213120124-8691201d-1a89-4dc6-bc55-7f31ace56056.png)

> https://starthardware.org/arduino-serial-print/ 

# (5) 24.01.2023

Heute haben wir ein Breadboard erhalten und uns zunächst damit etwas eingearbeitet. Die Idee war, erstmal ein LED zum Leuchten zu bringen. Den Code dafür findet man in einem vorgespeicherten Beispiel bei Arduino, sodass man nur alles richitg verkablen musste. Als wir dies getan haben, leuchtete jedoch zunächst nur das kleine Lämpchen auf dem Arduino selbst und nicht das eingesteckte LED Licht. 

> ![grafik](https://user-images.githubusercontent.com/111414662/214284597-481c5b2b-ddec-45c5-8749-58d83a63cbad.png)

> ![grafik](https://user-images.githubusercontent.com/111414662/214287320-c7902ea7-4535-45a2-ab81-e6d8eedd8b7c.png)

Trotz einiges hin- und herprobierens und googelns konnten wir das Porblem in der diesigen Stunde nicht lösen und werden uns deshalb morgen damit beschäftigen. 

# (6) 25.01.2023

In der heutigen Stunde haben wir uns zunächst mit dem Problem aus letzter Stunde beschäftigt und es schließlich auch gelöst; der Code war richtig, der Arduino war lediglich nicht richtig verkabelt. Nun leuchtet und blickt also auch das LED. 

> ![grafik](https://user-images.githubusercontent.com/111414662/214511096-e875ac4f-50a9-4fd1-b34d-3a35d2944c06.png)

Dann haben wir noch eine Konstante (Const) für unseren Port definiert, die besagt, dass der LEDPIN = 4 ist. Somit können wir die Variable 4 (den Output-Port) im Code immer durch LEDPIN ersetzen. 
Außerdem haben wir noch den "Serial Monitor" programmiert, der immer das ausspuckt, was der Arduino gerade als Befehl bekommt, also in unserem Falle "On" und "Off", je nachdem ob das LED gerade blinkt oder nicht. 

> ![grafik](https://user-images.githubusercontent.com/111414662/214511163-209a0e23-54d5-4d39-994d-acc94652655c.png)

Schlussendlich haben wir noch angefangen, eine Schleife (mit dem Befehl "for") einzurichten. Dabei soll das LED in der Theorie immer 4x mal blinken und dann eine Puase machen. Dabei wird ein Zähler eingerichtet, der pro blinken immer 1 dazu addiert. Der Code wurde zwar geuploaded, allerdings pausiert das Blinken des LEDs bisher noch nicht. Darum werden wir uns also in den nächsten Stunden kümmern müssen. 

> ![grafik](https://user-images.githubusercontent.com/111414662/214514180-0dcd95bb-6dea-4599-b2c6-7002d7ee1267.png)

Am Ende wollen wir einen kleinen Rechner damit programmieren (mithilfe vom Blinken); Hilfe haben wir dazu auf dieser Website gefunden: 

> https://starthardware.org/lektion-10-for-schleife-und-der-led-rechner/

# (7) 31.01.2023

Heute haben wir an dem kleinen "Rechner" von letzter Stunde weitergearbeitet. Nun können wir mit ihm kleine Aufagben rechnen (z.B. 2+3) und er spukt die Antwort mit Hilfe des LEDs aus (beim Beispiel 2+3 blinkt er 5x).

# (8) 01.02.2023

In der heutigen Stunde haben wir zunächst noch weitere LEDS zum Leuchten gebracht. Danach haben wir angenfangen, eine Glühbirne anzuschließen. Hierzu mussten wir uns erstmal mit Transistoren auseinandersetzen und lernen, wie man diese bedient. Danach haben wir begonnen einen Stromkreis aufzustellen und den Transistor eingebaut. Damit hatten wir anfänglich Probleme, und so hat es eine Weile gedauert, bis wir den Stromkreis fertig hatten. Zum Schluss haben wir dann noch angefangen, uns den richtigen Code zu erschließen, sind damit aber noch nicht so weit, sodass wir das nächste Stunde in Angriff nehmen müssen.

> ![grafik](https://user-images.githubusercontent.com/111414662/218076510-22bbb878-6cd7-4520-98ef-3af6b4ffc510.png)
> ![grafik](https://user-images.githubusercontent.com/111414662/218076602-c64183df-e8a2-4cd4-90b3-cc4b458cc409.png)

# (9) 10.02.2023

Heute haben wir uns weiter mit unserer Spielidee beschäftigt. Um uns noch intensiver damit auseinaderzustezen, nehmen wir den Arduino-Baukasten mit nach Hause übers Wochenende. Dananch haben wir noch weiter an dem Code aus letzter Stunde gearbeitet.

# (10) 12.02.2023 (Zuhause)

Wir haben uns für ein Projekt entschieden. Wir wollen eine Glühbirne mit Hilfe eines Bewegungsmelders zum Leuchten bringen. Zudem soll die Glühbirne mit Hilfe eines Transistoren gesteuert werden. Dazu haben wir den Code heute geschrieben. In den nächsten Stunden werden wir dann versuchen, den Transistor und den Bewegungsmelder anzuschließen und das Programm laufen zu lassen. 

> ![grafik](https://user-images.githubusercontent.com/111414662/218325427-030b8660-82c8-466a-835b-fd999146807a.png)

# (11) 15.02.2023

Heute haben wir alles verkabelt und angeschlossen (Bewegungsmelder, Transistor etc.), was wir für unser Projekt brauchen. Es war zunächt etwas schwierig, den Bewegungsmelder anzuschließen, da es schwer zu erkennen war, in welchen Port die ANschlüsse gehören. Schließlich haben wir das allerdings dann hinbekommen. Als wir den Code geuploaded hatten, funktionierte es allerdings noch nicht (obwohl keine "Error" Mitteilung kam). Aus dem Grund haben wi noch den Serial Monitor" einprogrammiert, müssen uns allerdings nächste Stunde damit beschäftigen, warum der Bewegungsmelder und die Glühbirne noch nicht funktionieren. 

> ![grafik](https://user-images.githubusercontent.com/111414662/220561168-4414227f-5cfe-4bf6-b0ef-fa29cbb6c311.png)
> ![grafik](https://user-images.githubusercontent.com/111414662/220561651-45a54a9c-05f4-46e4-9cdd-84382d632a64.png)

# (12) 22.02.2023

Heute haben wir uns weiter mit der Programmierung des serial monitors beschäftigt. 

> https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-serial-monitor
