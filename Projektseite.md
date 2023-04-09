# Projektseite + Fazit

## [Programm](#Programm)

## [Spielprinzip](#Spielprinzip)

## [Code](#Code)

### [Weltklassen](#Weltklassen)
     
### [Actorklassen](#Actorklasssen)

## [Fazit](#Fazit)

## [Quellen](#Quellen)

## [Stundenprotokoll]
 

## Das Programm <a name="Programm"></a>

![image](https://user-images.githubusercontent.com/111414185/208302437-4ef429f7-3aab-4fd0-9d5a-947c677f55bd.png)

Ich habe mich für die Arbeit mit Greenfoot entschieden. In Greenfoot können auch unerfahrene Programnmierer sich einmal an der Erstellung eines Spiels versuchen. Es handelt sich dabei um 2D Spiele. Die Arbeitsoberfläche bei Greenfoot ist einfach aufgebaut, sodass sich auch Anfänger gut zurecht finden. Bei Greenfoot arbeitet man mit sog. Szenarien. Diese Szenarien füllt man mit Klassen, die ganz verschiedene Rollen übernehmen können. Von diesen kann man beliebig viele erstellen um z.B eine Spielwelt zu erstellen oder einen Charakter zu schaffen, der bestimmte Befehle ausführen soll.
Die Befehle, die ein Obkelt einer bestimmten Klasse ausführen soll, werden im Editor eingefügt. Die Programmiersprache ist Java. Als Anfänger muss man sich also ersteinmal mit verschiednen Befehlen vertraut machen und lernen, wie man sie richtig anwendet.


## Das Spielprinzip <a name="Spielprinzip"></a>

Da ich mich auch im zweiten Schuljahr wieder für ein Projekt mit Greenfoot entschieden habe, habe ich mir überlegt, welche Art von Spiel, abseits des "Jump&Run", noch interesannt wären. Schnell viel meine Idee auf ein Spiel in dem der Spieler druch eine Art Labyrinth kommen muss, während er Gegnern ausweicht, um zu gewinnen. Also etwas wie das sehr bekannte "PacMan". Das Spielprinzip ist also relativ Simpel. Der Spieler muss sich ein einerm Labyrinth bewegen und dabei Objekte einsammeln. Während der Spieler die Objekte bzw. Ziele einsammelt, muss er jedoch Gegnern ausweichen, die den Spieler nicht berühren dürfen. Außerdem ist der Spieler in seinem Bewegunsradius durch die Wände des Labyrinths eingeschränkt. 


## Der Code <a name="Code"></a>

Um zu verstehen, wie mein Spiel funktioniert, werde ich im Folgenden den CODE des Spiels erläutern. Ich werde die wichtigsten Methoden aufführen und ihre Funktion in Zusammenhang mit den einzelnen Befehlen erklären. 

Am Anfang habe ich zu aller erst ein neues Szenrio bei Greenfoot erstellt. 

![Screenshot (19)](https://user-images.githubusercontent.com/111414185/208303576-6b1481fb-2f3d-4d99-80af-3e59a2062ab0.png)

Das Szenario ist praktisch der Gesamtrahmen des Projektes und das fertige Spiel wird als Datein unter dem Namen des Szenarios gespeichert. 

Nun habe ich mich daran gemacht, neue Klassen zu erstellen. Wie dies genau funktioniert habe ich bereits ausführlich in meiner letzten Projketseite (2022) erläutert. Damit ich mich nicht unnötig wiederhole verzichte ich deswegen heute darauf. 

### Die Weltklassen <a name="Weltklassen"></a>

#### Die World/World2 Klassen <a name=" Die World/World2 Klassen"></a>


Ich habe also nun ersteinmal die Weltklasse erstellt. Da ich mir bereits sicher war, das ich zwei Level in meinem Spiel haben möchte, habe ich direkt zwei Weltklassen erstellt, welche später die beiden Level darstellen. 

![Screenshot (17)](https://user-images.githubusercontent.com/111414185/230773670-fb3b9abd-fe1a-4571-8902-4b46a9d27d24.png)

Da beide Level den gleichen Aufbau erhalten, habe ich das Labyrinth nur in einer Welt aufgebaut und dann per "Copy&Paste" in die zweite eingefügt.

Kommen wir nun auch direkt zum Aufbau des Labyrinths. Innerhalb des Welt soll es Hindernisse geben, die durch ihre Anordnung das Labyrinth formen. Ich habe einen Weg gefunden, dafür zu sorgen, dass es genügt lediglich ein quadratisches Hinderniss (Actor "Wall") zu erstellen. Dieses Hinderniss wird dann belibig oft eingesetzt um eine Wand o.ä. zu errichten. 

![Screenshot (18)](https://user-images.githubusercontent.com/111414185/230774016-ee0681d3-c110-4686-92bf-03d62e0b0551.png)


Ersteinmal habe ich also eine Actor-Klasse erstellt, die simpel "Wall" heißt. Sie hat die Maße, 40x40 pixel. Da meine Welt insgesamt 800px Breit (X-Richtung) und 600px hoch (Y-Richtung) ist, kann das Objekt also realtiv oft eingefügt werden, um längere Wände zu erstellen. 
Da es jedoch relativ Mühsam wäre jedes Objekt einzeln per Hand einzusetzen und dann die Koordinaten einzeln einzugeben, habe ich sog. Zählerschleifen genutzt. Man definiert das Objekt, also die "Wall", als zaehler und kann diesem dann sich beliebig oft Wiederholende Eigenschaften zuteilen. In meinem Fall sollte die "Wall an bestimmten Punkten, über eine gewisse Strecke hin, eingefügt werdem. Nutz man die Zählerschleife, sind die Objekte außerdem genau gerade in die gewünschte Richtung angeordnet.

Blicken wir einmal in den Greenfoot-Code, sehen wir das der Zaehler nun auf einem bestimmten X bzw. Y Level, im Abstand von 40 (zaehler +40) zaehlt. Nun wird ihm außerdem mitgeteilt, dass für jeden Zaehler eine "Wall" eingefügt werden soll. 

![Screenshot (20)](https://user-images.githubusercontent.com/111414185/230774530-9d054717-ee34-4b26-96b4-2eb12e6375c7.png)
(World, 1. Level)

Rot makiert ist hier einmal exemplarisch eine solche Reihe, welche druch eine Zählerschleife erstellt wurde.   

Die Reihen kann man sowohl in X, als auch in Y Richtung erstellen. Möchte man eine unvollständige Reihe, dann ist dies mit ein IF-Methode zu ergänzen. 

![Screenshot (21)](https://user-images.githubusercontent.com/111414185/230775290-03f65545-e981-4348-88a9-fb398b831f28.png)

Um die Gegner (target-Klasse) einzufügen, habe ich die selbe Methode angewendet. 

#### WIN und END-Klassen <a name="WIN und END-Klassen"></a>

Nun möchte ich auf die WIN und END Klasse eingehen. Diese befassen sich damit, was passiert, wenn der Spieler stirbt oder das Level erfolgreich beendet hat. Beginnen wir mit der "WinClass". Diese wird aufgerufen, wenn der Spieler alle "target" im ersten Level eingesammelt hat. Wie genau das passiert, werde ich erläutern wennich mich mit dem Player befasse. Wenn also die Klasse aufgerufen wird, wird ein Text eingeblendet, der sagt "Press F for lvl 2".
Im Code der Win Classe wird festgelegt, welche Farbe der Hintergrund (bg) haben soll und welche Maße er hat. Außerdem wird der Schriftzug (String Message) in gewünschter Farbe und Schriftar(Font) dargestellt. 

![Screenshot (22)](https://user-images.githubusercontent.com/111414185/230775675-00500497-b811-421c-a691-9eddbb3d2c04.png)


Nun möchte man aber auch, dass wirklich etwas passiert, wenn F gedrückt wird. Hierzu hat die Klasse eine Methode, die dies ermöglicht. 
Wird also die Taste "f" gedrückt, wird die 2. Weltklasse aufgerufen, die das zweite Level darstellt. 

![Screenshot (23)](https://user-images.githubusercontent.com/111414185/230775767-48400fa0-9227-4055-84c1-64a79703a73d.png)

Bei dieser Gelegenheit, möchte ich nocheinmal erwähnen, dass alle Methoden immer nochmal in einer Act Methode aufgegriffen werden müssen, damit sich auch ausgeführt werden. Das gilt für alle Klassen, egal ob World oder Actor. 

Parallel zu Win gibt es noch Win2 und EndGame. 
Diese Klassen sind im Aufbau gleich, werden jedoch zu anderen Umständen aufgerufen. Endgame, immer dann wenn der Spieler stirbt. Dann wird außerdem der Schriftzug "GameOver" eingefügt. Und Win2 für das überwinden des 2ten Levels, also wenn alle targets aufgesammelt wurden. Hier heißt es dann "YOU WIN". 

### Die Actorklassen <a name="Die Actorklassen"></a> 

#### Test_player <a name="Test_player"></a> 

Über den Actor "Wall" habe ich ja schon ausführlich gesprochen. Nun soll es darum gehen, zu verstehen, wie es gelingt, das weder Spieler noch Gegner über die Wall laufen, sondern sie als Hinderniss wahrnehmen. 

Hierzu wede ich eine sog. boolean Methode an. Diese gibt Variablen aus, die entweder den Wert true, oder false haben können. Meine Variable deklariere ich als "kollision". Diese ist immer dann "true" also wahr (also ungleich 0), wenn der Spieler eine Wall berührt. Kommt es zu einer kollision, wird dann ein überschneiden der Beiden Actoren verhindert. (getOneIntersectingObject) So ist es dem Spieler nicht möglich über die Wall zu laufen und er muss erst seine Bewegungsrichtung so ändern, dass es nicht mehr zu einer Kollision kommt. 

![Screenshot (24)](https://user-images.githubusercontent.com/111414185/230778903-bed55783-d424-4634-a503-4f65b7d07a5c.png)

Um die "target" Objekte auch einzusammeln habe ich die "eat" Methode genutzt. Hier habe ich mich an meinem alten Projekt bedient, da dies die effektifste Methode ist und außerdem auch sehr simpel. 

![Screenshot (25)](https://user-images.githubusercontent.com/111414185/230779017-3be1cc87-c5d4-4bd9-81cc-4613c2ba8d33.png)

In dieser Methode wird gesagt, dass das Target immer dann aus der Welt entfernt wird, wenn es mit dem Spieler kollidiert. 

#### Enemyklasse <a name="Enemyklasse"></a>

Diese Methode wird so auch in der Enemy-Klasse eingesetzt, nur das hier immer der Spieler entfert wird, wenn er mit dem Enemy kollidiert. 
Desweiteren wird im unteren Teil der Methode festgelegt, dass die erste "WinClass" eingefügt wird, wenn der Spieler 128 targets eingesammelt hat und wenn er dann auch alle aus dem zweiten Level hat (256) wird der "WIN-Class2" Screen ausgeführt und der Spieler hat gewonnen. 

![Screenshot (75)](https://user-images.githubusercontent.com/111414185/230785625-ead6e62b-b0bc-49b6-9ac9-86b9f08f380e.png)


Die Enemy-Klasse ist nicht sonderlich kompliziert aufgebaut. Sie hat die selbe Kollisions-Methode wie der Test_player (also Spieler) und die gleiche eat-Methode. Hier ist lediglich der Unterschied, dass nicht die WinClass ausgeführt wird, wenn die eat Methode eingreift, sondern die EndGame-Klasse, also wird dem Spieler mitgeteilt, dass er verloren hat. 

Die BEwegung des Enemy läuftz wie folgtz ab. Alle Actor dieser Klasse bewegen sich in X-Richtung aber nie in Y-Richtung. 
Mit einer intitialen X Bewegung von 2.
Sollte nun die "CheckForWall Methode aktiv werden, also der Enemy mit einer Wall kollidiren, ändert sich seine Bewgungsrichtung um 180 Grad aus xRichtung wird -xRichtung.

#### WalterderWaal <a name="WalterderWaal"></a>

Auch die "WalterDerWaal" Klasse ist genau so aufgebaut. Jedoch kann diese Klasse sich auch auf den "Wall" Klassen bewegen, damit es im Spiel etwas schwere wird. Hierzu habe ich einfach die Kollision-Methode weggelassen. (Der Name zu dieser Klasse ist ohne weitern Sinn, er entspringt lediglich meiner spontanen Kreativität.)








