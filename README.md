# Projekt-2

[1. Einleitung](#1)

[2. Aufbau/Konzept](#2)

[3. Design](#3)

[4. Minispiele](#4)

[5. Level](#5)

## Einleitung<a name="1"></a>

Das **"Die Geschichte einer Kuh"** ist ein interaktives Lernspiel, wo der Spieler aus Sicht einer Kuh Hürden bewältigen muss, wobei er allgemeine Fakten lernt und Mini-Spiele spielt.

Das Spiel ist mit dem Programm **Snap!** programmiert worden. Deswegen werden im Folgendem Begriffe der Programmiersprache Snap! verwendet, um zu erläutern, wie das Spiel funktioniert. Wir haben einige Ideen unseres ersten Spiels **Evolution Game** miteinfließen lassen und erweitert und zusätzlich auch neue Befehle etc. verwendet. Durch die Minispiele wurden viele verschiedene Funktionen von Snap! verwendet und gibt angehenden Programmierern eine gute Übersicht, was man alles mit Snap! programmieren kann.

**Beschreibung**

Wie der Name "Die Geschichte einer Kuh" schon erahnen lässt, handelt es sich bei dem Spiel darum aus Sicht einer Kuh ein Abenteuer zu erleben, welche von ihrem Bauernhof davon rennt und verschiedene Situationen überstehen muss. So gerät sie zunächst in ein Gewitter und der Spieler muss ein Quiz beantworten, wie die Kuh sich verhalten soll. Bei falschen Antworten kann der Spieler sich noch einmal durch ein Mini-Spiel retten, um die Frage erneut zu beantworten. Verliert man das Mini-Spiel so ist man *Game-over* und muss von vorne anfangen. Bei der richtigen Antwort aber erhählt man eine Belohnung (z.B. einen nützlichen Gegenstand), welcher in einer Trophäenkiste gelagert wird. Auf diese Trophäenkiste kann man das ganze Spiel über zugreifen.

## Aufbau/Konzept<a name="2"></a>

Wenn die "kleine grüne Flagge" geklickt wird, startet das Spiel. Der Startbildschirm ist eine grüne Wieso und die Kuh schaut links "aus" dem Bildschirm.
Klickt man diese nun (*when I am clicked*) an erzählt sie, dass sie aufbrechen will und fordert den Spieler auf ihr zu helfen.
Zudem ist ein *next-button* (Sprite 14) auf dem Startbildschirm. Klickt man diesen an, kommt man zu der ersten Situation dem Gewitter. Dies geschieht in dem Sprite 14 den Befehl *broadcast (hidenextbutton)* ausführt. Diese "Nachricht erhält dann Sprite 4 durch den Control-Befehl *when I recieve* und der Hintergrund einer hügeligen dunklen Landschaft erscheint (*switch to costume*). Desweiteren erhält der Spieler die nächste Anweisung (*think: Klicke x*).
Klickt man nun die Taste x, erscheint eine Gewitterwolke plus Sound-Effekt (*play sound (...)*) und eine kleine Kuh (Sprite 5) und zwar durch den Control-Befehl *when x kex pressed* und *switch to costume - kuh-* (+ weitere *look-Befehle*). Der Spieler erhält die nächste Anweisung *say(...) klicke w*. Wird nun die Taste w gedrückt, erscheint das erste Quiz (*when w key pressed (...)switch to costume (...)*).
Das Quiz stellt die Frage, was die Kuh nun tun soll, da gleich in Blitz in der Nähe einschlagen wird. Dafür gibt es verschiedene Antwortmöglichkeite (A,B,C,D).
Klickt man A (man soll sich unter einen Baum stellen), wird Sprite 5 (die Kuh) unter einen Baum des Hintergundes verschoben (*when a key pressed (...) go to x:(...) and y(...)*).
Nun schlägt ein Blitz(Sprite 2) direkt in den Baum ein (*when a key pressed (...) go to x:(...) and y:(...)*). Zusätzlich wird der Befehl *broadcast (Flammen)* eingefügt. Diesen Broadcast erfasst Sprite 6 durch *when I recieve (flammen)*. Dadurch erscheint eine Animation eines Feuers, so dass es aussieht als würde der Baum brennen. Dies erreicht man durch eine Kombination von Look- und Controlbefehlen. Sprite 6 (Flammen) ist einmal links und einmal rechts gedreht (spiegelverkehrt). Die genaue Programmierung sieht man im Folgenden Screenshot:

**Screenshot**

Nach dieser Animation erscheint eine Informationsbox, dass diese Antwort falsch ist und eine Begründung. Dann kommt eine weitere Box welche sagt, dass man sich durch ein Mini-Spiel noch retten kann. Zu diesem Spiel kommt man durch Klicken der Enter-Taste(Sprite 5: *when space key pressed (...) switch to costume (kuh)*) und die Animation verschwindet (*wait until space key pressed klicked (...)hide*). Das Mini-Spiel setzt sich daraus zusammen, dass Blitz vom Himmel kommen und die Kuh diesen ausweichen muss. Die Kuh kann man nun nach links und rechts bewegen (*when left arrow key pressed - change x by -20; when right arrow key pressed change x by 20*). Damit die Kuh nicht den Bildschirm verlässt wurde noch der befehl *if on edge bounce* eingefügt. Die Blitze sind wieder Sprite 2. Diese erscheinen durch den Befehl *when space key pressed - show*. Diese Blitze schlagen nicht direkt ein, sondern gleiten die y-Achse herunter (*glide 5 secs to x: (pick random -240 to 240, y: -150*), damit der Spieler Zeit hat auszuweichen. Das ganze wird wiederholt bis die Zeit von 15 Sekunden abgelaufen ist oder der Blitz die Kuh berührt (*repeat until touching Sprite 5? or timer > 15*). Wenn der Blitz (Sprite 2) die Kuh (Sprite 5) berührt, ist das Spiel verloren und Sprite 2 führt 1)*Broadcast Game over* aus. Dies erreicht Sprite 6 (*when I recieve "game over" - switch to costume game over*) und ein Schild mit "Game over" erscheint. Das Spiel ist vorbei.
Wenn dies nicht eintrifft, wird der 2)*Broadcast new game* ausgeführt (*if (1) else(2)*. Dies erreicht Sprite 5 (*when I recieve new game*) und das Sprite wird wieder zum Kostüm des Quizes und man kann dieses nochmal beantworten.

Wenn man nun Antwort B auswählt (die Kuh kann bleiben wo sie ist, da der Blitz *nur* in der Nähe einschlägt), wird die Kuh (Sprite 5) wieder in die Anfangsposition verschoben (*go to x:(...),y.(...)*). Der Blitz (Sprite 2) schlägt neben der Kuh ein (*show-go to x:(...),y:(...)*). Dazu erscheint Sprite 8 (eine visuelle Darstellung eines kreisförmigen elektrischen Feldes) (*when b key clicked-go to (...)*). Dieses breitet sich kreisförmig aus (*repeat 5 - change size by 15*). damit es auf der gleichen Position bleibt und sich nicht nach oben verschiebt (sich also nur erkennbar in x-Richtung vergrößert, wird der Befehl *change y by -15* eingefügt. Zusätzlich wird noch ein Sound-Effekt eingefügt.

