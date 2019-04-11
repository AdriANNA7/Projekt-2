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

![start bildschirm](https://user-images.githubusercontent.com/42734752/55952502-14f62b00-5c5a-11e9-8620-43683c6a3d80.png)

Klickt man diese nun (*when I am clicked*) an erzählt sie, dass sie aufbrechen will und fordert den Spieler auf ihr zu helfen.
Zudem ist ein *next-button* (Sprite 14) auf dem Startbildschirm. Klickt man diesen an, kommt man zu der ersten Situation dem Gewitter.

![gewittter landschaft](https://user-images.githubusercontent.com/42734752/55952917-08be9d80-5c5b-11e9-8959-4db40ac6bd25.png)

Dies geschieht in dem Sprite 14 den Befehl *broadcast (hidenextbutton)* ausführt. Diese "Nachricht erhält dann Sprite 4 durch den Control-Befehl *when I recieve* und der Hintergrund einer hügeligen dunklen Landschaft erscheint (*switch to costume*). 

![next button 1](https://user-images.githubusercontent.com/42734752/55952939-1a07aa00-5c5b-11e9-896a-5cf6118dd7fb.png)
![switch gewitter landschaft](https://user-images.githubusercontent.com/42734752/55952961-268c0280-5c5b-11e9-9f1e-205858ef9fe3.png)

Desweiteren erhält der Spieler die nächste Anweisung (*think: Klicke x*).
Klickt man nun die Taste x, erscheint eine Gewitterwolke plus Sound-Effekt (*play sound (...)*) und eine kleine Kuh (Sprite 5) und zwar durch den Control-Befehl *when x kex pressed* und *switch to costume - kuh-* (+ weitere *look-Befehle*). Der Spieler erhält die nächste Anweisung *say(...) klicke w*. 

![gewitter kuh](https://user-images.githubusercontent.com/42734752/55953060-6c48cb00-5c5b-11e9-8d1e-dc2d6eff3f9c.png)

Wird nun die Taste w gedrückt, erscheint das erste Quiz (*when w key pressed (...)switch to costume (...)*).
Das Quiz stellt die Frage, was die Kuh nun tun soll, da gleich in Blitz in der Nähe einschlagen wird. Dafür gibt es verschiedene Antwortmöglichkeite (A,B,C,D).

![quiz frage 1](https://user-images.githubusercontent.com/42734752/55953144-a1edb400-5c5b-11e9-8b9d-23f27265a910.png)

Klickt man A (man soll sich unter einen Baum stellen), wird Sprite 5 (die Kuh) unter einen Baum des Hintergundes verschoben (*when a key pressed (...) go to x:(...) and y(...)*).
Nun schlägt ein Blitz(Sprite 2) direkt in den Baum ein (*when a key pressed (...) go to x:(...) and y:(...)*). Zusätzlich wird der Befehl *broadcast (Flammen)* eingefügt. Diesen Broadcast erfasst Sprite 6 durch *when I recieve (flammen)*. Dadurch erscheint eine Animation eines Feuers, so dass es aussieht als würde der Baum brennen. 

![blitz einschlag a](https://user-images.githubusercontent.com/42734752/55953361-32c48f80-5c5c-11e9-87f1-62ae5194efff.png)
![flammen bild](https://user-images.githubusercontent.com/42734752/55953380-3d7f2480-5c5c-11e9-979f-d3543f9cfeab.png)

Dies erreicht man durch eine Kombination von Look- und Controlbefehlen. Sprite 6 (Flammen) ist einmal links und einmal rechts gedreht (spiegelverkehrt). Die genaue Programmierung sieht man im Folgenden Screenshot:

![blitz a script](https://user-images.githubusercontent.com/42734752/55953512-96e75380-5c5c-11e9-88b5-f17a672204ad.png)
![flammen script](https://user-images.githubusercontent.com/42734752/55953543-a9618d00-5c5c-11e9-8974-a10eaaa2363a.png)

Nach dieser Animation erscheint eine Informationsbox, dass diese Antwort falsch ist und eine Begründung. 

![info a 1](https://user-images.githubusercontent.com/42734752/55953622-e3cb2a00-5c5c-11e9-968e-af73c358cbc8.png)


Dann kommt eine weitere Box welche sagt, dass man sich durch ein Mini-Spiel noch retten kann. Zu diesem Spiel kommt man durch Klicken der Enter-Taste(Sprite 5: *when space key pressed (...) switch to costume (kuh)*) und die Animation verschwindet (*wait until space key pressed klicked (...)hide*). 

![info a 2](https://user-images.githubusercontent.com/42734752/55953898-9e5b2c80-5c5d-11e9-85d4-7ba6505ec91c.png)

Das Mini-Spiel setzt sich daraus zusammen, dass Blitz vom Himmel kommen und die Kuh diesen ausweichen muss. Die Kuh kann man nun nach links und rechts bewegen (*when left arrow key pressed - change x by -20; when right arrow key pressed change x by 20*). Damit die Kuh nicht den Bildschirm verlässt wurde noch der befehl *if on edge bounce* eingefügt. 

![kuh bewegung minispiel a](https://user-images.githubusercontent.com/42734752/55953943-b59a1a00-5c5d-11e9-96b3-da34ae313458.png)

Die Blitze sind wieder Sprite 2. Diese erscheinen durch den Befehl *when space key pressed - show*. Diese Blitze schlagen nicht direkt ein, sondern gleiten die y-Achse herunter (*glide 5 secs to x: (pick random -240 to 240, y: -150*), damit der Spieler Zeit hat auszuweichen. Das ganze wird wiederholt bis die Zeit von 15 Sekunden abgelaufen ist oder der Blitz die Kuh berührt (*repeat until touching Sprite 5? or timer > 15*). Wenn der Blitz (Sprite 2) die Kuh (Sprite 5) berührt, ist das Spiel verloren und Sprite 2 führt 1)*Broadcast Game over* aus. Dies erreicht Sprite 6 (*when I recieve "game over" - switch to costume game over*) und ein Schild mit "Game over" erscheint. Das Spiel ist vorbei.
Wenn dies nicht eintrifft, wird der 2)*Broadcast new game* ausgeführt (*if (1) else(2)*. Dies erreicht Sprite 5 (*when I recieve new game*) und das Sprite wird wieder zum Kostüm des Quizes und man kann dieses nochmal beantworten.

![blitze minispiel a script](https://user-images.githubusercontent.com/42734752/55954055-feea6980-5c5d-11e9-816f-c9b08fb152d8.png)

![game over script](https://user-images.githubusercontent.com/42734752/55955722-64405980-5c62-11e9-8ac3-e9bf93a596e9.png)
![new game recieve quiz](https://user-images.githubusercontent.com/42734752/55955701-5ab6f180-5c62-11e9-8807-f84b4102eaa4.png)

Wenn man nun Antwort B auswählt (die Kuh kann bleiben wo sie ist, da der Blitz *nur* in der Nähe einschlägt), wird die Kuh (Sprite 5) wieder in die Anfangsposition verschoben (*go to x:(...),y.(...)*). Der Blitz (Sprite 2) schlägt neben der Kuh ein (*show-go to x:(...),y:(...)*). Dazu erscheint Sprite 8 (eine visuelle Darstellung eines kreisförmigen elektrischen Feldes) (*when b key clicked-go to (...)*). Dieses breitet sich kreisförmig aus (*repeat 5 - change size by 15*). damit es auf der gleichen Position bleibt und sich nicht nach oben verschiebt (sich also nur erkennbar in x-Richtung vergrößert, wird der Befehl *change y by -15* eingefügt. Zusätzlich wird noch ein Sound-Effekt eingefügt.

![elektrisches Feld](https://user-images.githubusercontent.com/42734752/55955494-e11f0380-5c61-11e9-8b68-d8b79af37770.png)

Kurz darauf erscheint auch Sprite 9 (Blitzwirrwarr) direkt "auf" der Kuh. Dieses zeigt, dass die Kuh einen elektrischen Schlag erfährt und wurde wie bei den Flammen in Form einer Animation programmiert (Siehe oben). 

![blitzwirrwarr](https://user-images.githubusercontent.com/42734752/55955511-f005b600-5c61-11e9-923c-5018fa0d2a3d.png)

Dazu wird ein negativer Grafikeffekt bei der Kuh (Sprite 5) erreicht, um es visuell besser darzustellen (*when touching Sprite 9 - set negative effgect to 75*).

![antwort b szenario](https://user-images.githubusercontent.com/42734752/55955466-cea4ca00-5c61-11e9-975c-4aa2f2f23417.png)

Danach erscheint Sprite 10 (*when b key pressed - wait - show*), welches Infoboxen sind, wieso B falsch ist(fantasievoll/visuell).

![b info 1](https://user-images.githubusercontent.com/42734752/55955842-c6995a00-5c62-11e9-96c9-e4387b614f29.png)
![b info 2](https://user-images.githubusercontent.com/42734752/55955865-d31db280-5c62-11e9-9dd2-1465f0be487b.png)

Dann erscheint eine weitere Box mit einer zweiten Frage "Was ist die Einheit für Stromstärke?". Diese Frage hat nur zwei Antwortmöglickeiten 1. Watt und 2. Ampere. 

![b frage 2](https://user-images.githubusercontent.com/42734752/55955883-dfa20b00-5c62-11e9-9d46-9a7559584dde.png)

Wenn jetzt die Taste 1 geklickt wird, führt Sprite 10 den Befehl *Broadcast game over* aus und das Sprite mit dem Game over- Zeichen erhält dies und erscheint (wie in Antwort A) und das Spiel ist vorbei. Antwortet man richtig und wählt Ampere aus, wird der Befehl *tell Sprite 2: Broadcast new game* ausgeführt und das Quiz kann erneut beantwortet werden. Dazu wird der Befehl *tell Sprite 5 to set negative effect to 0* ausgeführt, da sonst das Quiz ebenfalls negativ angezeigt werden würde.

Wird nun die Antwort C ( man soll in einen See) angeklickt, wechselt Sprite 5 zu einem See als Hintergrund (*whe c key pressed - switch costume*). Dazu erscheint Sprite 11 (Kuh-Kopf) und man sieht wie die Kuh erschrocken in dem See ist. Mit dem Befehl *broadcast* erscheint wieder das Game over - Zeichen. Bei dieser Antwort gibt es kein rettendes Mini-Spiel, da dies das "Worst-case-Szenario" darstellt.

Antwort D (man versteckt sich in einer Grube) ist die richtige Antwort. Klickt man dieses erscheint eine Sandlandschaft mit Gruben und es wird dem Spieler mitgeteilt, dass diese Antwort richtig ist (Sprite 5 : *switch costume to hole*). Gleichzeit wird der Befehl *broadcast belohnungsschild* aktiv. Dadurch erscheint oben rechts im Bildschirm ein kleines schwarzes Zeichen, welches eine Trophäe darstellen soll (*recieve- go to*). Dies ist die Trophöenkiste. Wird dieses Sprite nun angeklickt, wird diese Kiste sozusagen geöffnet (*when I am clicked*) und es erscheint ein hellblauer Hintergrund. Zusätzlich wird der Befehl *broadcast belohnung* ausgeführt. Sprite 12 (roter Regenschirm), die erste Belohnung erhält diesen *Broadcast* und erscheint auf dem blauen Hintergrund links oben. Es hüpft auf und ab (*glide 1 secs to x:x position, y: y position + 5 - glide 1 secs to x: x position, y: y position - 5*). Dies wird wiederholt bis man es anklickt/auswählt (*repeat until touching mouse-pointer*).
Ebenfalls auf dem blauen Hintergrund erscheint ein "Back-Button". Mit diesem kommt man wieder zu dem davorigen Hintergrund, um weiter zu spielen. Wenn man diesen Button anklickt werden zwei *Broadcasts* aktiv, einmal der der wieder zurück zu dem Hintergrund wechselt und der, der das Sprite 14 aktiviert. SPrite 14 ist ein "Next-Button" den man anklicken, um weiter zu spielen. Klickt man diesen an, kommt man durch den *broadcast Level up* und *broadcast new level* zu der nächsten Situation einer Stadt.

## Design<a name="3"></a>

Der Spieler ist eine Kuh. Dafür wurden viele verschiedene PNGs von Kühen für die Kostüme verwendet. Die grafische Darstellung (*Costumes* und *Stages*) wurden aus dem Internet importiert. Für die Hintergründe des ersten Levels haben wir einmal eine grüne Wiese verwendet, eine Hügellandschaft bei Nacht, einen See bei Gewitter und eine Sandlandschaft mit Gruben. Das zweite Level zeigt zunächst eine Straße in der Stadt und wird dann zu einer Straße in einer Landschaft. Zusätzlich wurden Animationen, sowie Grafik- und Soundeffekte eingefügt, um das Spiel visuell interessant zu gestalten und verschiedene Atmosphären zu kreieren.

## Minispiele<a name="4"></a>

Die Minuspiele wurden im Konzept schon erklärt. Sie sind dazu da, Variationen in das Spiel zu bringen und dementsprechend spannender zu machen. Trotzdessen, dass man Quize beantwortet und etwas lernt, soll dem Spieler das Spiel schließlich Spaß bringen und das Spiel den Spieler nicht langweilen, sondern unterhalten.

## Level<a name="5"></a>
Da es sich bei dem Spiel um eine Geschichte handelt, muss die Kuh natürlich verschiedene Etappen und Situationen durchlaufen. Dies wird in Form von verschiedenen Leveln gezeigt. Sie unterscheiden sich in ihrem Ort, der Aufgabe, der Minispiele und Belohnungen. So lernt der Spieler verschiedene Situationen kennen und es wird auf Dauer nicht langweilig.


