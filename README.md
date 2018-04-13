# Informatik Projekt 3  
## Grundlagen beim Arbeiten mit einem Arduino/NodeMCU  

von Lennard Korte  
Stormarnschule Ahrensburg  
Klasse 12a  
18.02.2018  

### <a name="Inhaltsverzeichnis"></a> Inhaltsverzeichnis

* **[Vorwort](#Vorwort)**  
* **[Erste Unterrichtseinheit](#1)**  
* **[Zweite Unterrichtseinheit](#2)**  
* **[Weitere Arbeit zu Hause](#3)**  
* **[Dritte Unterrichtseinheit](#4)**  
* **[Vierte Unterrichtseinheit](#5)**  
* **[Weitere Arbeit zu Hause](#6)**  
    * [Anschluss und erste Versuche der Steuerung](#7)  
    * [Firmwareupdate zuerst!?](#8)  
    * [Die verschiedenen Modi](#9)  
    * [Defekt?](#10)  
    * [Mit dem Level Shifter auf Nummer Sicher](#11)  
    * [ESP AT-Befehle und Telnet](#12)  
    * [Mail versandt?](#13)  
    * [Reedkontakte](#14)  
    * [von Grund auf neu](#15)
    * [Pushnotification](#16)
    * [Fehlerbehebung/Firmwareupdate](#17)
    * [Hinzufügen weiterer Features](#18)
    * [Code für Smarten Briefkasten](#19)
    * [Einbau des Resultats](#20)
    * [Schlusswort](#Schlusswort)  

### Vorwort <a name="Vorwort"></a>  

Das zweite Informatik-Projekt Nr.2 war beendet und bei Herrn Buhl abgegeben, sodass mir offen stand, woran ich im Informatik-Unterricht zukünftig weiterarbeiten könnte. Es waren drei Informatik-Projekte für das gesamte Schuljahr vorgesehen. Zwei waren bereits abgeschlossen, sodass noch eines fehlte. Zum einen bestand die Möglichkeit, ein neues Projekt zu startet. Zum anderen bestand weiterhin die Möglichkeit, das gerade beendete Informatik-Projekt Nr.2 zu verbessern, bzw. zu überarbeiten, was nicht meinen Ansprüchen eines kompletten Projekts entsprach. Deswegen habe ich mich entschieden mir ein neues Informatik-Projekt zu suchen, welches mich begeistern würde und in den zeitlichen Rahmen des Unterrichts hinein passte. Ein neues Informatik-Projekt zu finden, welches beide Eigenschaften kombibinierte, stellte sich für mich allerdings nicht ganz so schwierig wie gedacht heraus, was sich in den nächsten Stunden zeigte...  

[→ zurück zum Anfang](#Inhaltsverzeichnis)  

### 1. Unterrichtseinheit (15.02.2018) <a name="1"></a>  

Zunächste zeigte ich unserem Lehrer Herrn Buhl am Anfang der Informatik-Stunde das gerade beendete Projekt, bei dem ich einen Wecker auf dem Arduino UNO mit Multie-Function-Shield programmiert habe, der allerdings immer noch Verbesserungsmöglichkeiten aufweiste. Deshalb machte mich Herr Buhl auf die sogenannte <a href="https://wlanowski.de/arduinouhr-rtc-ds1307/">RTC-Module</a> (Real-Time-Clock) aufmerksam, welche zuließ, die aktuelle Uhrzeit mit Hilfe eines Quartz-Moduls einstellen zu können und somit den Wecker in seinen Funktionen zu erweitern. Herr Buhl schlug vor, einmal im Teilelager (Schrank) nachzuschauen, ob ein solches Modul bereits vorhanden sei und zeigte mir dabei ein LCD-Display. Ein RTC-Modul konnte leider nicht mehr gefunden werden. Es wurde also der Kauf eines solchen Moduls geplant, was natürlich ein paar Tage dauern konnte. Währenddessen beschlossen wir, dass es ganz interessant wäre das Display auszuprobieren und ein wenig damit zu arbeiten. Dazu musste es allerdings erst noch mit den Pins zum Anschließen an das Arduino-UNO-Board verlötet werden, was ich mir dann für die nächste Stunde vornahm. Dazu zeigte mir Herr Buhl eine Anleitung in Form eines <a href="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/documents/DE_SolderComic.pdf/">Comics</a>, wie man am besten lötet. Nach ein wenig Recherche zur Funktionsweise des <a href="https://www.buydisplay.com/default/blue-character-display-20x4-lcd-module-arduino-white-led-backlight">LCD-Displays (Blue Character Display 20x4 LCD Module)</a> war die Stunde auch schon vorüber.  

[→ zurück zum Anfang](#Inhaltsverzeichnis)  



 ### 2. Unterrichtseinheit (16.02.2018) <a name="2"></a>  

Anfang der nächsten Informatikstunde las ich mir noch einmal genauer das Comic zum Löten der Pins an das LCD-Displays durch und stellte fest, dass es für mich, wegen meiner bereits gemachten Löt-Erfahrungen beim Reparieren von defekten Steckern, keine besonders großen Neuerungen beinhaltete. Also fing ich relativ schnell damit an zu löten und war auch entsprechend schnell fertig. Nachdem ich mir sicherheitshalber die Hände gewaschen und den Tisch aufgeräumt hatte, suchte ich online auf verschiedensten Internet-Seiten nach der Funktionsweise des LCD-Displays, damit ich es auch mit dem Arduino ansteuern konnte. Dazu gab es verschiedene Vorgehensweisen, die aber auf der gleichen Grundfunktionsweise beruhten. Fast alle LiquidCrystal-Displays für Arduinos werden von einem <a href="https://de.wikipedia.org/wiki/HD44780">HD44780 Schaltkreis von Hitachi</a> angesteuert, der im Modul integriert ist und sich über die angelöteten Pins ansteuern lässt. Die Displays für Arduinos unterscheiden sich also grundsätzlich nur in ihrer Größe und in den Einstellungen, die dafür vorzunehmen sind. Für die Ansteuerung dieses Schaltkreises gibt es eine vorgefertigte <a href="https://www.arduino.cc/en/Reference/LiquidCrystal">LiquidDisplay-Library<a/>, mit der auf dem Arduino mit einfachen Befehlen Zeichen dargestellt werden können und welche zusätzliche Funktionen, wie z.B. die <a hrf="https://www.arduino.cc/en/Tutorial/LiquidCrystalAutoscroll">AutoScroll-Funktion</a> für neu hinzugefügte Texte beinhaltet. Ich versuchte nach dem Löten zunächst das LCD-Dosplay an den Arduino anzuschließen. Es gelang mir allerdings nur die Hintergrundbeleuchtung zu aktivieren, nicht aber einen Schriftzug zu erzeugen. So neigte sich die Schulstunde bei detailierter Fehlersuche und Recherche zeitlich relativ schnell dem Ende und ich musste meine Arbeit erst einmal unterbrechen. Ich baute die Schaltkreise zunächst wieder ab.  

Zu Hause recherchierte ich erneut und musste alles erneut verkabeln. Nach einiger Zeit gelang es mir das LCD-Display folgendermaßen anzuschließen:  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/IMG_20180218_180501.JPG" alt="image" width="400">  

Grundsätzlich orientierte ich mich dabei an folgenden Vorgaben, die ich in <a href="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/documents/Character%20Module%20Datasheet%20ERM2004-2%20Series.pdf">diesem Dokument</a> im Kapitel 4.1 bei den technischen Spezifikationen fand:  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/LiquidCrystal-Display%20Technical%20Specs.PNG" alt="image" width="400">  

Auch die Vorgaben zu dem Thema auf <a href="https://www.arduino.cc/en/Tutorial/HelloWorld?from=Tutorial.LiquidCrystal">Arduino.cc</a> gaben mir Aufschluss dazu, wie ich das Display verkabeln konnte. Außerdem schaute ich mir wiederholt ein <a href="https://www.youtube.com/watch?v=ftRSZ6tCl1w">YouTube-Video</a> an, dessen Erklärungen schnell auch ein etwas tieferes Verständnis möglich machten. Meinen selbst programmierten Code dazu ist <a href="https://github.com/lakgiter/Informatik-Projekt-3/tree/master/code1">hier</a> zu finden.  

[→ zurück zum Anfang](#Inhaltsverzeichnis)  



### weitere Arbeit zu Hause (17/18.02.2018) <a name="w1"></a>  

Das Display konnte nun angesteuert werden und war einsatzbereit. Allerdings hatte ich immer noch kein vollwertiges Projekt für die nächsten Informatikstunden, welches ich in Zukunft bearbeiten konnte. Ich musste mich also schon mal nach einem neuen Projekt umsehen. Diesmal sollte es etwas nützliches und gebräuchliches für den Alltag für sein. Ein Projekt, dass mir und anderen Personen den Alltag erleichtern sollte. Es dauerte ein wenig ein Projekt zu finden, welches den zeitlichen Rahmen nicht überstieg. So recherchierte ich einige Zeit. Von vorneherein machte ich mir bewusst, dass mein nächstes Projekt in der vorgegebenen Zeit realisierbar sein musste und trotzdem meinem Anspruch genügen sollte. Meine Erfahrung hatte mir gezeigt, dass der Zeitaufwand schließlich doch immer größer ist als erwartet.  
Ich schaute auf verschiedenen Internetseiten nach und hielt letztendlich den Bau eines smarten Briefkastens für eine sehr geeignete Projekt-Idee, die ich umsetzen wollte. Anregung dazu fand ich auf <a href="https://makezine.com/projects/arduino-mail-notifier/">makezine.com<a/>. Dem Nutzer würde von einem Arduino angezeigt werden, ob Post in dem Briefkasten eingesteckt wurde oder nicht. Sensor und Empfänger waren zwei verschiedene Arduinos. Diese Idee fand ich sehr gut, das Konzept allerdings nicht besonders optimal. Es fielen mir folgende Sachen auf, die ich anders umsetzen wollte:  
1. Es sollten nicht zwei Arduinos verwendet werden, die kommunizieren und dem Nutzer so über die Ferne benachrichtigen. Stattdessen sollte der Nutzer von einem einzelnen Arduino per Nachricht auf sein Handy auch unterwegs benachrichtigt werden. 
2. Ich hielt ich es für ein wenig ungenau, den Status des Briefkastens mit einem Helligkeitssender zu überwachen/ausfindig zu machen. Wenn es dunkel wird, kann kaum noch ein Helligkeitsunterschied erfasst werden und der Arduino registriert nicht, ob der Briefkasten geleert oder befüllt wird, wenn man ihn öffnet. Er kann dies mit einem Helligkeitssensor nur sehr ungenau erfassen. Deshalb wollte ich das Öffnen der Einwurf-Klappe, sowie der Leerungs-Klappe mit Hilfe von Magnetsensoren erfassen, wie sie an Fenstern einer Alarmanlage angebracht sind, und den aktuellen Status des Briefkastens ausfindig machen. So ist der Sensor nicht mehr von der Tageszeit abhängig und kann auch registieren, wenn der Briefkasten geleert wird, sodass andere Familienmitglieder ebenso Bescheid wissen und nicht unnötigerweise nachschauen müssen.
3. Es sollte möglich sein, den Arduino in ein Smart-Home Netzwerk einzubinden.  

Zunächste recherchierte ich dafür nach den benötigten Teilen und machte eine Übersicht:

1. Stromversorgung (vllt.: Netzteil mit 2 oder 1 Ampere; wetterfeste Solarzelle und Akku; Batteriefach)
2. Wasserfestes Gehäuse
3. wetterfeste Magnetsensoren (Reedkontakt?)
4. möglichst stromsparenden Arduino mit Wifi Schnittstelle

Mit Herrn Buhl war abzusprechen, ob die Bestellung eines RTC-Moduls angesichts der Möglichkeit eine Time-Library zu installieren wirklich nötig ist. Außerdem war es notwendig, die Idee zum neuen Projekt und die dafür benötigten Teile zu besprechen.

[→ zurück zum Anfang](#Inhaltsverzeichnis)



### 3. Unterrichtseinheit (22.02.2018) <a name="3"></a>  

In den nächsten Informatikstunde versuchte ich mir eine Übersicht zu machen, wie ich das Projekt nun genau umsetzen wollte. Es stellten sich nun bereits konkretere Fragen zu dem Projekt die schon an die nähere Planung heranragten. Wichtig war es zum Beispiel zu klären, ob die Stromversorgung mit einer Solarzelle sinvoll und effizient genug ist, um den Arduino langzeitig mit Energie zu versorgen. Ich machte mich also an die Arbeit und versuchte Antworten auf folgende Fragen zu finden:

Welche Stromversorgung für einen Arduino ist in diesem Fall die beste?
Generell standen <a href="https://www.youtube.com/watch?v=cUu_C1wYaic">verschiedene Möglichkeiten<a/> zur Wahl, den Arduino mit Strom zu versorgen. Dabei zog ich es auch in Erwägung möglicherweise einen Raspberry Pi in diesem Projekt zu verwenden, um einen geringeren Stromverbrauch und damit ein effizienteres System zu bauen, was ich allerdings beim Vergleich des Stromverbrauches, der beim Raspberry Pi deutlich erhöht ist, fallen ließ. Generelle Informationen zur Energieversorgung von Raspberry Pi und Arduino sind aber ähnlich, sodass mir <a href="https://www.elektronik-kompendium.de/sites/raspberry-pi/1912111.htm">diese Seite<a/> über die Grundlagen der Energieversorgung / Stromversorgung des Raspberry Pi's durchaus weiterhalf. Genauere Daten über den Arduino lieferte mir dann <a href="https://wiki.attraktor.org/images/1/1c/Arduino-Spannungsversorgung.pdf">diese Seite<a/>, sodass ich auch gleich eine Rechnung über den Stromverbrauch des Arduinos aufstellen konnte.

[→ zurück zum Anfang](#Inhaltsverzeichnis)  



### 4. Unterrichtseinheit (23.02.2018) <a name="4"></a>  

So konnte ich den Stromverbrauch eines Arduino UNO boards auch über längeren Zeitraum in Relation zu der Leistungsstärke einer Solarzelle setzen und abwägen, ob diese in Verbindung mit einem Spannungsregler und einem Akkumulator komplett alleine den Arduino nach <a href="https://www.generationrobots.com/de/401735-solarmodul-für-arduino-board-mit-ladegerät.html">diesem Vorbild<a/> versorgen konnten. Ich kam nach einigem Rechnen darauf, dass es keinen Sinn machen würde an einem häufig schattigen Ort hinter dem Haus auf dem Briefkasten oder daneben eine Solarzelle auf einem Briefkasten anzubringen, da die Sonneneinstrahlung deutlich größer sein müsste, um den Akku näherungsweise wieder aufladen zu können. Auch der mögliche Energiesparmodus des Arduinos half dabei nicht viel, da er ja stehts aufmerksam bleiben sollte, sodass ich mich letztendlich dazu entschied, den Arduino direkt an die Steckdose anzuschließen. Eine Gegenüberstellung der verschiedenen Arduino-Boards und dessen Stromverbrauchs ist <a href="https://arduino-projekte.info/stromverbrauch-arduino-wemos-boards/">hier<a/> zu finden.  

Um herauszufinden, ob wir schon Wifi-fähige Module, Shields oder Arduinos in der Schule haben, verschaffte ich mir einen Überblick über die verschiedenen Gerät. Bei dieser Suche ging ich aber leider leer aus.

[→ zurück zum Anfang](#Inhaltsverzeichnis)  



### weitere Arbeit zu Hause (ab dem 24/28.02.2018) <a name="6"></a>  

#### Auswahl der Bestandteile <a name="6.1"></a>  

Dass es ein Arduino und kein Raspberry Pi werden sollte stand also erstmal fest. Es stellten sich nun noch die Fragen: Welchen Arduino sollte ich denn nun kaufen? Denn auch hier gingen die Preiskategorien weit auseinander und es gibt eine Vielzahl von Anbietern. Nach einiger Recherche fand ich also heraus, dass es keine aktuellen Arduino-Boards gibt, die ein Wifi-Modul selber integriert haben und noch produziert werden. Eine Übersicht ist auf der Website des Herstellers zu finden. Also musste ich zusätzlich zum Standard-Arduino UNO Modell noch ein Wifi-Modul erwerben. Nur welches Wifi-Modul und welcher Arduino waren die beste Wahl? - auch mit Blick auf den Stromverbrauch und die Qualität, bzw. Nutzbarkeit? Gibt es noch weitere Unterschiede innerhalb einer Produktklasse?  
Auch beim Arduino UNO gab es Unterschiede bei den verschiedenen Herstellern. Letztendlich stellte sich heraus, dass die Arduino UNO- Modelle sich kaum unterscheiden. Wesentliche Unterschiede liegen bei den Chips, die bei neueren Modellen zwar kleiner sind, aber genau die gleiche Leistung erbringen und sich in Ihrer grundlegenden Funktionsweise nicht unterscheiden. Es gibt neuere und ältere Modelle, die etwas unterschiedlich aussehen, aber im Grunde alle ähnlich aufgebaut sind und das gleiche können. Ich wählte also ein etwas neueres und <a href="https://www.amazon.de/gp/product/B01MDJA464/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1">günstigeres Modell auf Amazon<a/> für gerade mal ein paar Euro. Der Chip darauf war dafür etwas kleiner, als der auf einem original Arduino-Board und es lag ein USB-Kabel gleich mit bei.
Nun galt es noch zu beantworten welches Netzteil gekauft werden sollte. Ich entschied mich für eines mit einer größeren Amperezahl, da ich mir davon weniger Funktionseinschränkungen und Ausfälle des Arduinos in Verbindung mit stromraubenden Sensoren oder einem Wifi-Modul erhoffte, wie ich es auf zahlreichen Seiten gelesen hatte. Es sollte ein <a href="https://www.amazon.de/gp/product/B01MS5ZQH5/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1">9.0V/2A Netzteil<a/> werden.
Dagegen war die Frage nach dem Wifi-Modul etwas komplizierter. Die Vielfalt der verschiedenen Module und Extras ist enorm und ich brauchte viel Zeit um wirklich jedes Teil den anderen gegenüberzustellen und abzuwägen, welches denn nun die richtige Wahl war. Die Vielfalt ist besonders daran erkennen, dass z.B. der ESP8266 in <a href="https://www.golem.de/news/mitmachprojekt-temperatur-messen-und-versenden-mit-dem-esp8266-1604-120378.html">16 verschiedenen Varianten<a/>, zu erwerben ist, die alle ganz unterschiedliche Möglichkeiten bieten (<a href="http://stefanfrings.de/esp8266/index.html">hier<a/> eine Übersicht). Schließlich entschied ich mich für <a href="https://www.amazon.de/gp/product/B072R6DPK7/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1">dieses Modul<a/>, welches sehr preiswert ist und dem sogar noch ein Adapter für die Steckplatte beigelegt wird, damit die Arbeit damit auf einem Steckbrett leichter war. Meine Überlegung war es, das Modul direkt auf den Arduino zu stecken, was daran scheiterte, dass geeignete Module seine Pins alle an Stellen hatten, die nicht mit dem Arduino UNO kompatibel waren. Die Idee war es eine rein softwaretechnische Kompatiblität ohne Kabel herzustellen, was damit aber sehr schnell auf Eis gelegt wurde. Dafür hatte ich mich <a href="https://www.elv.de/Arduino-verstehen-und-anwenden-Teil-1-Einstieg-in-die-Hardware-Arduino-und-AVR-Mikrocontroller/x.aspx/cid_726/detail_44820">hier<a/> und <a href="https://www.youtube.com/watch?v=E-YKpx4ucds">hier<a/> genauer über die Funktionsweise der Pins auf einem Arduino informiert und auf Wikipedia einen Eintrag zu USB-Steckern (TX/RX) gelesen.  

Der Plan war es nun also, den Arduino mit dem Wifi-Modul, wie <a href="https://www.gunook.com/senden-sie-e-mail-mit-esp8266-und-arduino-uno/">hier<a/> beschrieben zu <a href="https://www.youtube.com/watch?v=AlI3osIHkbU">verbinden und anzusteuern<a/>:  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/Arduino%20UNO%20und%20Wifi-Modul.jpg" alt="image" width="400">  

Als Sensoren suchte ich mir ganz einfache <a href="https://www.amazon.de/gp/product/B01H3QGNMM/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1">Reedkontakte<a/> auf Amazon heraus, die spritzwasserfest genug waren, um im Briefkasten angebracht werden zu können. Weitere Sensoren für einen Ausbau des Projekts bestellte ich angesichts der bereits relativ hohen Rechnung zunächst noch nicht. Zu den Sensoren fehlten mir noch Kabel und Steckplatten zum Verbinden der einzelnen Teile. Ich wählte ein einfaches <a href="https://www.amazon.de/gp/product/B073X7GZ1P/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1">Kabel-Board-Set<a/> aus, welches wesentliche Kabel beinhaltete, damit ich nicht in die Not kommen konnte, durch zu wenige Kabel oder Steckplätze in meinen Arbeiten eingeschränkt zu sein.  
Zum zusätzlichen Schutz vor Nässe blieb mir wohl nichts anderes übrig, als kreativ zu werden, wenn es so weit war...  

#### Anschluss und erste Versuche der Steuerung <a name="7"></a>  

Die Bestandteile waren angekommen. Also machte ich mich daran, das Wifi-Modul an den Arduino anzuschließen. Dies war gar nicht so leicht wie erwartet, da der Arduino den ich bestellt hatte nicht der originale war und zunächst nicht problemlos von der Software angenommen wurde. Ich starte die Konfiguration des IDE Programms neu und der Arduino wurde schließlich erkannt. Die Bezeichungen der Pins auf dem Adapter des Wifi-Moduls, wie z.B. VCC; verwirrten auch ein wenig, konnten aber nach kurzer Zeit aufgeklärt werden. Auch gab es anfangs Unklarheiten, wie ich das Modul mit dem Arduino verbinden sollte, da sich dies in zwei Richtungen auf den mitgelieferten Adapter stecken ließ. Ein kurzer Blick in die Lieferbeschreibung klärte dies jedoch recht schnell auf. Dadurch, dass die mitgelieferten Pins aber noch nicht fest am Adapter verlötet waren, gab es immer wieder einen Wackelkontakt, sodass das Wifi-Modul nicht richtig funktionierte und die ON-Leuchte dies bei leichtem Rütteln auch aufzeigte. Ich musste die Schaltung wieder auseinandernehmen und das Wifi-Modul mit anderen Kabeln und ohne Adapter an den Arduino und das Board anschließen. Das Löten nahm ich mir dann für die nächste Unterrichtseinheit vor.

Nach dem Anschließen des Moduls versuchte ich endlich das Wifi-Board anzusteuern. Dies sollte eig. über einem Spannungskonwerter zwischen der AX/RX Schnittstelle geschehen, da der Arduino einen 5V Ausgang hat, das Board aber nur einen 3.3V-Eingang. Die Recherche ergab allerdings, dass man diesen auch weglassen könne.
<a href="www.instructables.com/id/How-to-use-the-ESP8266-01-pins/">Diese Seite<a/> gibt einen relativ guten Überblick über die verschiedenen Sachen, die das Wifi-Modul machen kann. Allerdings war bereits der Einstieg ein wenig unklar, da nicht einheitlich aus den Quellen hervorging, wie das Wifi-Modul angeschlossen werden sollte. Auch war anfangs unklar, wie die Pinbelegung auf dem Adapter war. Ein kurzer Blick in die Produktbeschreibung der Bestellung klärte aber zumindest in diesem Punkt ein wenig auf. Ich schloss also alles nach der Variante an, die mir am sinnvollsten erschien. Problematisch war, dass die Pins des Adapters nicht fest waren, sondern nur aufgesteckt wurden, sodass ich diese erst noch festlöten musste. Wenn kein Adapter mitgeliefert wird, muss man sich stattdessen einen <a href="https://www.youtube.com/watch?v=AlI3osIHkbU"> selber bauen <a/>, um ihn auf der Steckplatte zu befestigen. Die Richtigkeit der Lötstellen überprüfte ich mit einem Voltmeter.
Ich öffnete also den Seriellen Monitor und bekam beim Einstecken des Boards jeweils eine Abfolge an Zeichen angezeigt, die ich nicht entziffern konnte. Nach ein wenig hin und her erwies sich der Baud 115200 als der richtige für die Eingabe von Befehlen, sodass am Ende der Erstausgabe "ready" angezeigt wurde. Ein Text-Befehl "AT" mit der Antwort "OK" bestätigte dies. Am Zeilenanfang und Zeilenende mussten die Befehle "CR" als auch "LN" eingestellt werden. Die unbekannte Zeilenfolge der Ersteausgabe zu Beginn des Codes ließ sich über den Baud 74880 entziffern. Sie offenbarte spezifische Angaben des ESP-Moduls 
   
   <img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/erste%20AT%20Befehle.PNG" alt="image" width="400"> 
   <img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/erste%20AT%20Befehle%202.PNG" alt="image" width="400"> 



#### Firmwareupdate zuerst!? <a name="8"></a>  

Der erste Erfolg war also erreicht. Ich schaffte es sogar den ESP8266 mit den verschiedensten AT-Befehlen <a href="https://www.youtube.com/watch?v=AlI3osIHkbU">anzusteuern<a/>. Zunächst wollte ich allerdings ein Firmware-Update machen, wie es auf verschiedensten Seiten empfohlen wurde. Dazu recherchierte ich auf verschiedensten Internetseiten, die auch mit einem Firmwareupdate begannen. Ich wollte damit beginnen, um sicherzustellen, dass auch alles funktionierte. Dazu probierte ich verschiedenste Software aus. Die Prozesse schlugen zum großen Teil fehl, was aber keine Seltenheit war, wie sich nach einiger Recherche herausstellte. Als ein einfach gestaltetes Programm, mit dem man leicht ein Firmwareupdate machen konnte kristallisierte sich der ESP8266Flasher heraus, mit dem auch auf <a href="http://www.instructables.com/id/Intro-Esp-8266-firmware-update/">dieser<a/> Website gearbeitet wird.

Ich probierte auch verschiedene weitere Methoden/Programme aus um den ESP8266 zu flashen, da dieser nicht wirklich den Anschein machte, zu funktionieren, unabhängig davon, wie ich ihn mit dem Arduino zusammensteckte. Diese Methoden sind unter anderem auf folgenden Seiten beschrieben:  

<a href="www.gunook.com/die-erste-verwendung-von-esp8266-mit-arduino-uno/">  
<a href="<a href="https://ukhas.net/wiki/esp8266_firmware_update">ukhas.com<a/>  
<a href="https://os.mbed.com/users/sschocke/code/WiFiLamp/wiki/Updating-ESP8266-Firmware">os.mbed.com<a/>  
<a href="https://www.gunook.com/senden-sie-e-mail-mit-esp8266-und-arduino-uno/">gunook.com<a/>  
<a href="fkainka.de/wlan-modul-verbindung-aufbauen/">fkainka.de<a/>  
<a href="https://www.allaboutcircuits.com/projects/update-the-firmware-in-your-esp8266-wi-fi-module/">allaboutcircuits.com<a/>  


#### Die verschiedenen Modi <a name="9"></a>  

Ich betone an dieser Stelle besonders, dass die Möglichkeiten den ESP8266 (kurz: ESP) anzuschließen von verschiedenen Quellen ganz unterschiedlich aufgefasst werden, was mich sehr durcheinander gebracht hat und sehr viel Zeit gekostet hat, da die Quellen sich auch häufig wiedersprechen. Aus diesem Grund habe ich mir eine Übersicht gemacht, die aufzeigt, was die am meisten zu findenden Varianten sind:

Pin am ESP | Pin am UNO normal | Pin am UNO Firmware-Update  
---------- | ----------------- | ---------------
RxD(GPIO3) | D4 | RX  
VCC(3.3V) | 3.3V | 3.3V  
GPIO0 | offen oder 3.3V | GND  
RST (auch als /RESET) | D8 3.3V mit Wiederstand oder offen | _  
GPIO2 | 3.3V mit Wiederstand oder offen | _  
CH_PD (auch als CHIP_EN, CHIP_PU, EN oder ENABLE) | 3.3V | 3.3V  
GND(mit GPIO15 verbunden) | GND | GND  
TxD(GPIO1) | D3 3.3V mit Wiederstand oder offen | TX  

Informationsquellen sind unter anderem vor allem:  
<a href="https://arduino-hannover.de/2014/12/11/wifi-kochbuch-mit-esp8266/">arduino-hannover.de<a/>  
<a href="http://yaab-arduino.blogspot.de/2015/03/esp8266-wiring-schemas.html">yaab-arduino.blogspot<a/>  
<a href="http://web.archive.org/web/20150502082616/http://defcon-cc.dyndns.org/wiki/ESP8266#Update">web.archive.org<a/>  
<a href="www.gunook.com/die-erste-verwendung-von-esp8266-mit-arduino-uno/">gunook.com<a/>  
<a href="https://ukhas.net/wiki/esp8266_firmware_update">ukhas.net<a/>  
<a href="https://os.mbed.com/users/sschocke/code/WiFiLamp/wiki/Updating-ESP8266-Firmware">os.mbed.com<a/>  
<a href="https://www.gunook.com/senden-sie-e-mail-mit-esp8266-und-arduino-uno/">gunook.com<a/>  
 

Es wird zwischen verschiedenen Modi unterschieden, mit denen der ESP beispielsweise geflasht werden konnte. Im großen und Ganzen stachen dabei der Flash und der normale Modus heraus. Diese waren offensichtlich von besonderer Bedeutung und Relevanz für das Projekt. Eine gute Übersicht über die Modi bieten auch folgende beide Seiten:  
  
https://github.com/espressif/esptool/wiki/ESP8266-Boot-Mode-Selection  
https://github.com/esp8266/esp8266-wiki/wiki/Boot-Process#esp-boot-modes  

#### Defekt? <a name="10"></a>  
  
Trotz Stundenlanger Beschäftigung mit ein und demselben Thema konnte ich den ESP aber nicht mehr dazu bringen mit einer lesbaren Antwort auf die AT Befehle zu Antworten. Es stellte sich die Frage, ob dies daran lag, dass die Firmware fehlerhaft war, oder ob der Chip des ESP's bei den vielen Versuchen mit den verschiedenen Anschlussmöglichkeiten beschädigt worden war. Laut den verschiedensten Quellen, wovon ich ja bereits einige aufgelistet habe konnte der ESP nämlich auch direkt am Arduino betrieben werden. Dabei herschte die allgemeine Ansicht, dass der ESP grundsätzlich mit 3.3V betrieben werden sollte, aber die RX/TX-Pins auch die 5V des Arduinos vertragen würden und man nicht zwangsläufig einen so genannten Level-Shifter braucht, der die 5V-Spannung des Arduinos in 3.3V umwandelt. Es wurde allerdings auch erwähnt, dass dies keine sichere Versprechung ist. Trotzdem gab es wohl beide Möglichkeiten und beide Möglichkeiten der Verkabelung sollten auch zum Erfolg führen. Auch in den Foren konnte ich noch einige Diskussionen darüber finden. Die Möglichkeit, dass das Wifi-Modul nicht funktionierte, weil es beim Start zu viel Strom verbrauchte, den der Arduino gar nicht zur Verfügung stellte konnte ich ausschließen. Einen Stromversorungsmangel konnte ich ausschließen, weil ich, trotz der tatsache, dass ich keinen Kondensator in die Schaltung eingebaut hatte, denn ich hatte zusätzlich zu dem USB-Kabel das 2A Netzteil an den Arduino angeschlossen.  

Das Problem konnte ich aber trotz hartnäckiger Fehlersuche nicht mehr richtig lösen. Ich entschloss mich aus zeitlichen Gründen einfach einen neuen ESP zu bestellen, was angesichts des geringen Preises von wenigen Euros deutlich effizienter war. Dafür bestellte ich gleich drei Stück, um nicht wieder in Notlage zu kommen. Meiner Ansicht nach konnten ein paar mehr auch nicht schaden, denn es gab noch viele weitere Möglichkeiten den ESP auch eigenständig zu betreiben, sodass ich über kurz oder lang wahrscheinlich sowieso noch mehr als einen benötigen würde.  


#### Mit dem Level Shifter auf Nummer Sicher <a name="11"></a>  

Mit dem neuen ESP wollte ich dann auf Nummer Sicher gehen. Ich schaute in der Schule nach, ob wir einen Levelshifter hatten , der auch die 5V Signale des Arduinos für den ESP umwandeln sollte und umgekehrt. Ich bekam von unserem Kurslehrer auch gleich zwei verschiedene davon zur Verfügung gestellt, die einfach unbenutzt herumlagen. Ich war offenbar der erste, der diese verwendete:  
  
1. 4-Bit Level Converter  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/4-bit%20Level%20Converter.jpg" alt="image" width="350">  
  
2. 8-Channel Level Shift  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/8%20channel%20level%20shifter.png" alt="image" width="350">  
  
Die entsprechenden Pins waren bei dem 4-Bit Lvel Converter bereits beigelegt sodass ich ihn direkt auf das Steckbrett stecken konnte. Die Konstruktion war etwas wackelig, aber wenn man nicht daran rüttelte, reichte es aus, um damit erste Versuche starten zu können. Ich recherchierte und eignette mir reltiv schnell die Funktionsweise der Wandler an. Der neue ESP ließ sich darüber allerdings auch nicht richtig ansteuern. Um meine Kenntnisse zu überprüfen nahm ich ein Voltmeter zur Hilfe. Ich schloss es entsprechend an den Arduino UNO an und machte verschiedenste Tests dazu. Es schien so, als wenn der Spannungswandler die Signale auf ALLE Pins der gegenüberliegenden Seite (mit je 6 Pins) übertragen würde. Meine Zweifel daran, dass dieser wirklich funktionierte, wie er es sollte veranlassten mich erst einmal dazu einen Versuch mit dem 8-Channel Level Shift zu starten. Auch hier waren die aufgesteckten Pins zum Verbinden mit dem Steckboard sehr wackelig, leider zu wackelig, um damit zu arbeiten. Kurzerhand entschied ich mich also dazu das ganze entsprechend zusammenzu löten. Pins waren dem Shift zwar nicht beigelegt, allerdings hatte ich bei meinen Bestellungen einige Pin-Leisten extra zugesandt bekommen, sodass ich von diesen nur zweimal die entsprechende Länge von acht abknipsen musste. Der Level Shifter tat seine Dienste auch nach den Tests mit dem Voltmeter und dem ESP.  
Es funktionierte alles einwandfrei, endlich!  

#### ESP AT-Befehle und Telnet <a name="12"></a>  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/arduino%20und%20ESP.JPG" alt="image" width="400">  

Nach all den Versuchen wollte ich mich also nun an die wirkliche Programmierarbeit begeben. Mein Ziel war es ja eine Benachrichtigung auf das Handy zu senden , um benachrichtigt zu werden, wenn der Briefkasten befüllt und geleert wird. Dafür probierte ich einige Möglichkeiten aus, mit dem dem ESP zu kommunizieren. Dies ging zum einen über den seriellen Monitor der Schnittstelle über USB. Weitere Informationen zu den AT-Befehlen fand ich vor allem hier:  

<a href="http://web.archive.org/web/20150502082616/http://defcon-cc.dyndns.org/wiki/ESP8266#Update">web.archive.com<a/>  
<a href="http://fkainka.de/wlan-modul-verbindung-aufbauen/">fkainka.de<a/>  
<a href="http://thomaspfeifer.net/esp8266_wlan_seriell_modul_at_kommandos.htm">thomaspfeifer.net<a/>  
<a href="https://github.com/espressif/ESP8266_AT/wiki/AT_Description">github.com<a/>  
<a href="https://www.espressif.com/sites/default/files/documentation/4a-esp8266_at_instruction_set_en.pdf">espressif.com<a/>  
<a href="https://arduino-hannover.de/2014/12/11/wifi-kochbuch-mit-esp8266/">arduino.hannover.de<a/>  

Zum anderen konnte ich das Wifi-Modul im cmd des Computers anpingen (wie zum Beispiel <a href="https://de.wikihow.com/Eine-IP-Adresse-anpingen">hier<a/> und <a href="https://www.allaboutcircuits.com/projects/update-the-firmware-in-your-esp8266-wi-fi-module/">hier<a/> beschrieben), nachdem ich eine Verbindung zum Router mit Hilfe der AT-Befehle hergestellt hatte. Darüber konnte auch die Verbindungsgeschwindigkeit ausfindig gemacht werden.  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/W-Lan-Verbindung.PNG" alt="image" width="350">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/anpingen.PNG" alt="image" width="350">  
   
Auch gelang es mir eine TCP Verbindung herzustellen und mit PUTTY im Telnet direkte Nachrichten an den seriellen Monitor zu übertragen, wie es unter anderem auch in https://www.youtube.com/watch?v=MH-nlpQwDN8">diesem Video<a/> beschrieben wird. Das gab mir dann wieder die nötige Motivation, da dies aufgrund meiner bisherigen Erfahrungen mit Netzwerken dieser Art, ohne Umwege klappte.

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/telnet%20putty.PNG" alt="image" width="350">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/telnet%20putty2.PNG" alt="image" width="350">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/telnet%20putty3.PNG" alt="image" width="350">  
  
  
#### Mail versandt? <a name="13"></a>  

Als nächtes befasste ich mich mit <a href="https://www.gunook.com/senden-sie-e-mail-mit-esp8266-und-arduino-uno/">verschiedenen Möglichkeiten<a/> mit dem Arduino in Verbindung mit dem ESP eine <a href="https://www.youtube.com/watch?v=n5WZ_BNRvRY">Mail an einen SMTP-Server<a/> (verlinkt ist die erste Wahl, der ich später weiter nachgegangen bin) zu versenden. Die Grundprinzipien zur Verwendung der Bibliotheken (<a href="https://github.com/AllAboutEE/Adafruit_ESP8266">hier<a/> ein Codebeispiel zu Bibliothek Nr.2), die dem ganzen zur Hilfe genommen werden sollten waren auch relativ schnell klar.:

1. https://github.com/sleemanj/ESP8266_Simple
2. https://github.com/adafruit/Fritzing-Library

Auch die Grundlagen zur <a href="http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol">Kommunikation mit einem SMTP-Server<a/> und der <a href="www.samlogic.net/articles/smtp-commands-reference.htm">SMTP-Kommandos<a/> erfasste ich relativ schnell. Dennoch bekam ich nach dem Upload des zum Teil vorgefertigten Codes immer wieder Fehlermeldungen, dass Modul nicht antwortete. Auch andere Versuche mit verschiedenen Bibliotheken brachten mich nicht weiter vorran. Insgesamt waren die Vortschritte bis hierher sehr ernüchternd. Der Fehler konnte eigentlich überall liegen. Ich probierte verschiedene Möglichkeiten aus, das Modul mit dem Arduino über den Level Shifter zu verbinden, was ich ja in Vorherigen Versuchen ebenfalls etliche Male getan hatte, um den Fehlern auf den Grund zu gehen. Auch die RX und TX Anschlüsse vertauschte ich, da in verschieden Foren unterschiedliche Angaben gemacht wurden. Ich probierte es also selber aus, was alles funktionieren könnte. Dank des Level-Shifters musste ich mir nämlich keine Sorgen mehr darüber machen, dass der ESP beschädigt wird. Auch stellte sich für mich die Frage, was RX/TX überhaupt sei. Letztendlich führte mich das immer wieder auf die <a href="https://de.wikipedia.org/wiki/Universal_Serial_Bus">USB Schnittstelle<a/> die schließlich ähnlich funktioniert.  
   
   
#### Reedkontakte <a name="14"></a>  

Trotz all der Bemühungen gelang es trotzdem nicht, eine einfache Mail zu versenden. Auch, wenn ich dafür extra verschiedene unkonventionelle Anbieter ausfindig machte und ausprobierte, die einen unterschlüsselten Versandt möglich machten, etc. Ich entschied mich also dazu mir einen Rat von etwas erfahreneren Programmierern einzuholen und stieß dabei auf verschiedene Arduino Foren. Darunter war auch ein deutsches Forum, auf dem ich mein Problem einfach beschrieb und veröffentlichte, in der Hoffnung, konstruktive Vorschläge zu meiner Problemstellung zu erhalten.
Die Zeit, in der ich nun hatte, bis ich eine Antwort bekam, nutzte ich dafür, mir die Reedkontakte genauer von innen und von außen anzuschauen. Auch ihre <a href="https://de.wikipedia.org/wiki/Reedschalter#/media/File:Reed-relais-ani.gif">Funktionsweise<a/> des Reedschalters wurde dadurch klarer und noch einmal bestätigt.  
   
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/Reedkontakt%20außen.JPG" alt="image" width="200">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/Reedkontakt%20innen.JPG" alt="image" width="200">  

Ich versuchte mich erst an einem kleinen Programm, welches ausgibt, ob die Reedkontakte offen oder geschlossen sind. Dabei viel auf, dass ich Wiederstände, wie bei vorherigen Projekten bei einem Knopf, einbauen musste, um die Genauihgkeit zu erhöhen und äußeren Einflüssen entgegenzuwirken.
```javascript
int in = 12;
int stat = 0; //Null heißt, dass der Kontakt geschlossen ist, es fließt Strom

void setup()
{
  Serial.begin(9600);
  pinMode(in, INPUT);
}

void loop()
{
  stat = digitalRead(in);
 if (stat == LOW){
  Serial.println(0);
 }else{
  Serial.println(1);
 }
  delay(100);
}
```
Darauf folgte dann der Grundaufbau meines Programmes in der ArduinoIDE, was die Kontakte auswertet und später entsprechende Nachrichten versenden soll. Dazu sollten dann später weitere Ideen ergänzt werden.  
```javascript
int count = 0;

void setup() {
  
  Serial.begin(57600);
  pinMode(13, OUTPUT);
  digitalWrite(13, LOW);
}

void loop() {
  
  int sensorValue1 = digitalRead(10);
  int sensorValue2 = digitalRead(11);
  
  if (count == 0){
  Serial.print("Sensor 1: ");
  Serial.print(sensorValue1);
  Serial.print("   ");
  Serial.print("Sensor 2: ");
  Serial.println(sensorValue2);
  Serial.println();
  count = 1;
  }
  if (sensorValue1 == 0){
    Serial.println("Briefkasten gefüllt");
    Serial.println("E-mail 1 senden");
    Serial.println();
    delay(10000);
    count = 0;
  }
  
  if (sensorValue2 == 0){
    Serial.println("Briefkasten gelehrt");
    Serial.println("E-mail 2 senden");
    Serial.println();
    delay(10000);
    count = 0;
  }
  delay(1);
}
```  

#### von Grund auf neu <a name="15"></a>  
  
Schließlich bekam ich eine Antwort auf meinen <a href="https://www.arduinoforum.de/arduino-Thread-ESP8266-E-Mail-Versandt-mit-Library">Post im Arduino-Forum<a/>. Von einer Person wurde mein Problem falsch und von einer anderen richtig erfasst. So bekam ich nach einiger Zeit einen Vorschlag, der im ersten Moment etwas radikal wirkte, aber mich zum Nachdenken brachte. Darin wurde mein bisheriges Konzept der Benachrichtigung über E-Mail mit einem Arduino und einem ESP komplett über den Haufen geworfen. Stattdessen wurde mir empfohlen die entsprechenden Nachrichten per Pushnachricht über ein NodeMCU direkt aufs Handy zu senden.  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/nodemcu.jpg" alt="image" width="400">  

Das <a href="https://www.amazon.de/IZOKEE-Internet-Development-Wireless-Kompatibel/dp/B01N4OYOKD/ref=sr_1_2?ie=UTF8&qid=1523553725&sr=8-2&keywords=esp8266+node">NodeMCU<a/> ist ein Board, welches ebenfalls einen ESP8266 verbaut hat und über alle weiteren Komponenten verfügt, die es für den alleinigen Betrieb benötigt, wenn man ihn alleine über einen USB-Anschluss flashen und mit Strom versorgen möchte. Dazu <a href="https://alexbloggt.com/esp8266-erste-erfahrungen/">hier<a/> einmal eine kurze Übersicht von Alex.Bloggt, der auch weitere gute Projekte veröffentlicht hat, nicht nur speziell zu NodeMCU. Zudem ist er deutlich stromsparender als der Arduino UNO zusammen mit dem ESP und braucht auch kein zusätzliches Netzteil bei der Stromversorung über den USB-Anschluss, auch bei Verwendung des ESP's. Die räumliche Größe ist für den Betrieb in einem Briefkasten deutliche besser geeignet.  
Ich bestellte also kurzerhand ein solches Board. Dadurch wurden die restlichen Teile, die ich dann nicht mehr brauchen würde, aber nicht als unnötig abgestempelt und weggelegt, denn ich bin mir sicher, dass ich diese später noch bei anderen Projekten brauchen werde und möglicherweise eine eigene Bibliothek für den alleinigen Betrieb des ESP erstelle? Wer weiß...?
Das Board habe ich dann einfach mit dem Micro-USB-Kabel einer Powerbank am PC angeschlossen.  
   
Sehr schwierig bis unmöglich war es, den NodeMCU auf das Steckbrett zu stecken, da das Board etwas zu breit dafür war. Außerdem waren die Steckplätze in dem Steckboard so konstruiert, dass sich das innere leicht verschieben konnte, was diese manchmal unbrauchbar machte.  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/steckplatte.JPG" alt="image" width="400">  

Es wurde so unmöglich, Sachen darauf zu stecken, ohne die Metallteile im Inneren zu beschädigen und umzuknicken. So ließen sich natürlich ganze Reihen von Pins oder Boards, wie zum Beispiel der NodeMCU, unmöglich daraufstecken, da diese alle gleich ausgerichtet waren. Ich hätte die Kabel natürlich auch direkt auf die Rückseite des NodeMCU aufstecken können, bevorzuge aber eine stabilere und flexiblere Langzeitlösung. Mit Hilfe eines Messers kratzte ich also die Kleberschicht auf der Rückseite des Steckboards ab, um an das innere des Boards zu kommen.  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/steckplatte%20von%20unten%20Kleber.JPG" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/steckplatte%20von%20unten.JPG" alt="image" width="400">  

Die seitlichen leisten benötigte ich für mein Vorhaben nicht mehr, weshalb ich die klebeschicht mit dem Messer durchtrennte und die Abschnitte wie vorgesehen ausklinkte. Danach hebelte ich die einzelnen Metallteile heraus und bog sie mit einer entsprechenden Zange so zurecht, dass ich das NodeMCU Board später einfach darauf stecken konnte. Dies gelang auch sehr gut, es war nur übermäßig viel Arbeit, jedes einzelne Teil zu bearbeiten und dann wieder in den Schlitz hinein zu schieben.  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/Metallteilchen%20aus%20Steckplatte.JPG" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/metallteilchen.JPG" alt="image" width="400">  
vorher - nachher

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/zange.JPG" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/Steckplatte%20von%20unten%20mit%20klebeband.JPG" alt="image" width="400">  

Nachdem alles wieder an seinem Platz war versiegelte ich die Rückseite des Steckboards mit Klebeband, damit nichts heraus fiel. Ich stellte das Board wieder richtig herum auf den Tisch, damit ich nun das NodeMCU darauf befestigen konnte. Mit etwas stärkerem Druck auf die Pins von außen und von oben war es schnell fest mit dem Board verbunden.  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/nodemcu%20mit%20steckplatte.JPG" alt="image" width="400">  
  
#### Pushnotification <a name="16"></a>  

Es fehlten nur noch die Kabel, Netzteil und Reed Sensoren. Ich hatte allerdings noch keine Ahnung, welche Belegung die einzelnen Pins des NodeMCU's hatten und wie diese mit dem ESP8266 darauf verbunden waren. Deswegen begann ich mit der Recherche.

Ich schaute mir die Empfehlung der Forum-Gemeinschaft zu Pushbullet genau an. Fand dann aber relativ schnell heraus, dass die Funktionen davon nur sehr begrenzt waren und ab einer bestimmten Zhal von Benachrichtigungen eine Gebühr anfällt. Deshalb schaute ich mich noch weiter um und stieß auf ganz verschiedene Wege Pushbenachrichtigungen mit einem ESP oder genauer einem NodeMCU einzurichten. Im folgenden einmal die Beiträge, die ich mir zu dem Thema anschaute:  
  
https://dzone.com/articles/iot-push-notifications-arduino  
https://community.blynk.cc/t/nodemcu-esp8266-dht11-temperature-push-message/9215  
https://www.youtube.com/watch?v=Ki5t_-Jjpjg  
https://myelectronicslab.com/door-sensor-with-push-notification-using-esp8266-nodemcu/  
www.instructables.com/id/Send-Notifications-to-Your-Phone-From-an-ESP8266/  
https://steve0hh.github.io/2016/12/04/how-to-send-push-notifications-using-esp8266.html  
https://github.com/witnessmenow/push-notifications-arduino-esp8266  
www.instructables.com/id/IoT-Push-Notification-Using-Nodemcu-on-PhoneFor-An/  
https://simplepush.io/blog/2017/01/29/esp8266-encrypted-notifications/  
https://www.geekstips.com/android-push-notifications-esp8266-arduino-tutorial/  
https://www.youtube.com/watch?v=nVdR0Ryr12k  
https://alexbloggt.com/esp8266-pushover/  

Der zuletzt aufgelistete <a href="https://alexbloggt.com/esp8266-pushover/">Beitrag<a/> traf das Vorhaben meines Erachtens am besten und bot eine gute Beschreibung, mit der ich schnell etwas anfangen konnte, wie ich es bereits vorher von Alex gewohnt war. Außerdem war die App mittlerweile kostenlos und das Benachrichtigungslimit lag monatlich bei 7500, sodass ich keine Zusatzkosten zu befürchten hatte. Ich probierte beschriebenes direkt aus. Auch das Codebeispiel half mir dabei. Für das Einrichten der Pushbenachrichtigungen muss nur eine Bibliothek in die Arduino IDE implementiert werden und in den Code eingebunden werden. Dann kann die Pushnachricht mit Hilfe einer API, die einem Bei der Erstellung und Einrichtung des Kontos bei Pushover zugewiesen wird, ganz einfach versendet werden. Natürlich nur unter der Vorraussetzung, dass bereits eine Internetverbindung besteht. Mit dem erstellten Konto muss man sich dann nur noch bei der App des Anbieters anmelden und kan direkt Pushnachrichten empfangen. Wichtig ist, dies in den Benachrichtigungseinstellungen des Handys zu aktivieren und der App die Rechte dafür zu geben.  
   
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/image%20registration.PNG" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/image%20API%20creation.PNG" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/image%20user%20key.PNG" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/image%20API.PNG" alt="image" width="400">  

Das funktionierte bei mir auch sehr gut, bis ich nach ein wenig Spielerei am Code eine Fehlermeldung von der Arduino IDE bekam, dass der ESP nicht mehr geflasht werden könne. Auch ein wiederholter Versuch änderte daran nichts.  

#### Fehlerbehebung/Firmwareupdate <a name="17"></a>  

Auch weitere Fehlerdetails gaben keinen genügenden Aufschluss um daraus schlau zu werden. Die Firewall hatte ich wie immer für diesen Zweck deaktiviert. Könnte es vielleicht daran liegen, dass ich den Flash Button betätigt hatte? Ich hatte bemerkt, dass der serielle Monitor bei dem <a href="https://blog.thesen.eu/esp8266-reset-probleme-loesen-und-relais-stabil-schalten/">Reset<a/> nur noch wirre Zeichen ausspuckte und der NodeMCU alle paar Sekunden neu startete. Eine kurze Recherche ergab die Antwort: Nein, der Flash Button hat keine größeren Auswirkungen auf die Firmware, sofern er nicht während des Flash-Vorgangs betätigt würde.
Trotzdem ließ mich das Gefühl nicht los, dass etwas bei der Firmware nicht stimmte. So führte ich ein <a href="https://www.youtube.com/watch?v=Af9UCSM0Ic8">Firmwareupdate<a/> durch, mit dem Risiko, dass dies alles nur noch viel schlimmer machen würde, aber mir blieb ja keine Wahl. Angesichts der vorherigen Erfahrungen war dies natürlich gewagt. Es funktionierte aber einwandtfrei. Und dafür brauchte ich nicht einmal neue Software installieren, da ich den ESP8266Flasher ja bereits vorher verwendet hatte.  
Trotzdem funktionierte das neue Laden des Codes auf das NodeMCU nicht wie gewollt. Ich probierte in den IDE Einstellungen die Option aus, nicht nur den Sketch zu laden, wie es vorher der Fall war, sondern alle Flas-Inhalte zu entfernen. Nach einem erneuten Versuch damit funktionierte alles hervorragend. Das Problem war gelöst.  
   
#### Hinzufügen weiterer Features <a name="18"></a>  
   
Aber natürlich war das noch nicht alles. Die While Funktion war mir neu und so suchte ich nach einer kurzen Erklärung zu dieser Funktion. Ich fand ein optimales <a href="https://www.youtube.com/watch?v=QlDH2SApocM">Video<a/> dazu, sodass ich die Funktion auch in meinem späteren Code für die "Warten"-Anzeige bei der Verbindungsherstellung zum Router einbinden wollte.
Nun war ja bereits ein wichtiges Ziel erreicht. Das System sollte stromsparend sein. Der NodeMCU war auch deutlich effizienter als der vorherige Aufbau. Mir kam die Idee den NodeMCU in den SleepModus zu versetzen, sodass dieser noch weniger Strom verbrauchte. Das war allerdings nicht zielführend, wie meine <a href="https://github.com/esp8266/Arduino/issues/644">Recherche<a/> ergab. Alternativ wollte ich aber das Wifi ausschalten, wenn es nicht gebraucht wurde. Das sollte Strom sparen, die dauerhafte Strahlung vermindern, die von dem ESP ausging und Sicherheitsrisiken vermindern, sofern das NodeMCU keine Aktivität am Briefkasten warnahm. Unsinnig war der Schlafmodus des ESP's deshalb, weil er in der Zeit keine Messungen aufnehmen kann und somit für den Zweck der Aktivitäterfassung unbrauchbar wäre. Aus diesem Grund fällt auch die Möglichkeit weg, des ESP im <a href="https://tutorials-raspberrypi.de/monatelanger-esp8266-batteriebetrieb-mittels-deep-sleep/">Akkubetrieb<a/> zu nutzen.  

Eine weitere Möglichkeit den Funktionsumpfang des ESP's zu erweitern bestand darin die Zeit zur Verfügung zu haben, um entsprechende Informationen im Seriellen Monitor anzeigen zu lassen, eine Entsprechende Nachricht an das Mobilgerät zu senden oder möhlicherweise in der Zukunft Statistiken in einer datenbank zu führen. Dazu sollte die Zeit von einem öffentlichen NTP (Zeitserver) abgefragt werden und in bestimmte Bedingungen im Code eingefügt werden. Mein <a href="https://www.arduinoclub.de/2016/05/07/arduino-ide-esp8266-ntp-server-timezone/">erster Versuch<a/> mit zwei verschiedenen "Time"-Libraries funktionierte nicht wie erwartet und stellte sich im Code auch als ziemlich unhandlich heraus. Deshalb suchte ich nach einer <a href="https://www.youtube.com/watch?v=qzkNXhubWLg">Alternative<a/> und fand diese schließlich auch. Dazu gehörte die <a href="https://github.com/SensorsIot/NTPtimeESP">NTPtimeESP-Librarie<a/>, die schon deutlich vielversprechender aussah. Sie funktionierte auch relativ schnell und ließ sich gut in meinen bereits vorhandenen Code einbinden. So konnte ich auch ein RTC-Modul außer Acht lassen.  

Ich versuchte die <a href="https://www.arduino.cc/reference/en/language/structure/control-structure/else/">if else/else-Funktion<a/> einzubauen. Dies funktionierte allerdings nicht wie erwartet, sondern wurde aus unerklärlichen Gründen nur in einzelnen if-Funktionen akzeptiert.  
  
Eine weitere Funktion die ich implementierte war die millis Funktion, die ich dazu verwendete, dass der Briefkasten beim wiederholten Öffnen des Einwurfschlitzes innerhalb von 30 Sekunden nicht reagierte, sodass ein Nachwerfen des Postbooten nicht zu einer Doppelten Benachrichtigung führt und Missbrauch der Funktion entgegengewirkt wird. Die Benachrichtigungsfunktion für die Lehrungsklappe bleibt davon unberührt, da diese ohnehin nur ausgelöst wird, wenn Post vorhanden ist, sodass darauf keine Rücksicht genommen werden muss. Diese Funktion implementierte ich mit dem "Millis()"-Befehl. Eine gut zusammengefasste Erklärung dazu ist <a href="https://www.youtube.com/watch?v=YP9xQWqFOKg">hier<a/> zu finden.  

Jetzt fehlten nur noch die Reed-Kontakte. Überraschenderweise brauchte ich hierbei keine Wiederstände für eine Erdung, um dessen Status zuverlässig auszumachen. Anhand des Schaltplans des NodeMCU leitete ich mir her, welche Pins frei waren (D1 und D2), an denen ich die Reedkontakte anschließen konnte, um einen INPUT zu definieren.  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/Reedkontakt.JPG" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/schaltplan.png" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/Nodemcu%20im%20system.JPG" alt="image" width="400">  

Die Reedkontakte hatten keine richtigen Stecker am Ende ihrer Kabel, weshalb sie nicht stabil an ihrem Platz festgehalten wurden, wenn man sie in das Steckbrett steckte. Aus diesem Grund funktionierte ich einige Kabel zu Verbindungsstücken um. Diese ließen sich an deren Endstück am Metallteil mit Hilfe eines Spitzen Gegenstandes zusammendrücken. Das Kabel konnte so darin fixiert werden.  

<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/System.JPG" alt="image" width="400">  

#### Code für Smarten Briefkasten <a name="19"></a>  

Insgesamt ergab sich dann folgender Code daraus:
```javascript
#include <Pushover.h>
#include <ESP8266WiFi.h>

#include <NTPtimeESP.h>
#define DEBUG_OFF
NTPtime NTPch("ch.pool.ntp.org");
strDateTime dateTime;
 
#define REED1 4 //D2
#define REED2 5 //D3

int mailstate = 0;

int reedState1 = 1;
int reedState2 = 1;
 
const char* ssid = "SSID hier einsetzen";
const char* password = "Passwort hier einsetzen";
 
Pushover po = Pushover("user key","API");
WiFiClient espClient;

void setup() {
  Serial.begin(115200);
  pinMode(REED1, INPUT_PULLUP);
  pinMode(REED2, INPUT_PULLUP);
}
 
void setup_wifi() {
  delay(10);
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
}

unsigned long lastMillis;

int reedState11 = 0;
int reedState22 = 0;
 
void loop() {
  
  dateTime = NTPch.getNTPtime(1.0, 1);
  
  reedState1 = digitalRead(REED1);
  reedState2 = digitalRead(REED2);

if ((lastMillis + 30000) <= millis()) {

  if ((reedState1 == HIGH) && (reedState11 == 0) && (mailstate == 0)) {
    setup_wifi();
    mailstate = 1;
    
    Serial.print("Post wurde ");
    if (11 < dateTime.hour && dateTime.hour < 14) {
      Serial.print("heute pünktlich um ");
    }
    if (dateTime.hour <= 11) {
      Serial.print("heute außergewöhnlich früh um ");
    }
    if (dateTime.hour >= 15) {
      Serial.print("heute sehr spät um ");
    }
    Serial.print(dateTime.hour);
    Serial.print(":");
    Serial.print(dateTime.minute);
    Serial.print(" Uhr eingeworfen!");
    
    po.setDevice("iPhone");
    if (11 < dateTime.hour && dateTime.hour < 14) {
      po.setMessage("Post wurde heute pünktlich eingeworfen!");
    }
    if (dateTime.hour <= 11) {
      po.setMessage("Post wurde heute außergewöhnlich früh eingeworfen!");
    }
    if (dateTime.hour >= 15) {
      po.setMessage("Post wurde heute sehr spät eingeworfen!");
    }
    po.setSound("incoming");
    Serial.println(po.send());
    
    reedState11 = 1;
    WiFi.mode(WIFI_OFF);
    delay(50);
    lastMillis = millis();
  }
  if ((reedState1 == HIGH) && (reedState11 == 0) && (mailstate >= 1)) {
    setup_wifi();
    
    mailstate = mailstate + 1;
    
    Serial.print("Post zum ");
    Serial.print(mailstate);
    Serial.print(" mal um ");
    Serial.print(dateTime.hour);
    Serial.print(":");
    Serial.print(dateTime.minute);
    Serial.println(" Uhr. Du solltest ihn leeren!");

    po.setDevice("iPhone");
    po.setMessage("Schon wieder Post! Du sollltest deinen Briefkasten leeren!");
    po.setSound("incoming");
    Serial.println(po.send());

    reedState11 = 1;
    WiFi.mode(WIFI_OFF);
    delay(50);
    lastMillis = millis();
  }
}
  if ((reedState2 == HIGH) && (reedState22 == 0) && (mailstate != 0)){
    setup_wifi();
    
    mailstate = 0;
    
    Serial.print("Briefkasten um ");
    Serial.print(dateTime.hour);
    Serial.print(":");
    Serial.print(dateTime.minute);
    Serial.println(" Uhr geleert!");

    po.setDevice("iPhone");
    po.setMessage("Briefkasten geleert!");
    po.setSound("intermission");
    Serial.println(po.send());
    
    WiFi.mode(WIFI_OFF);
    reedState22 = 1;
    delay(50);
  }
  if ((reedState1 == LOW) && (reedState11 == 1)) {
    reedState11 = 0;
    delay(50);
  }
  if ((reedState2 == LOW) && (reedState22 == 1)) {
    reedState22 = 0;
    delay(50);
  }
}
```

#### Einbau des Endresultats <a name="20"></a>  

Zuletzt musste ich nur noch eine Verpackung finden. Ich nutzte eine leichte und kleine Plastikverpackung, die weitestgehend vor äüßeren Einflüssen schützte und innerhalb des Briefkastens allemal ausreichen sollte. Als Netzteil nutzte ich ein einfaches USB-Netzteil von einem Mobilgerät. Eine Steckdose ist außen am Haus bereits erhalten. Die Reedkontakte hatten bereits klebende Rückseiten, sodass diese einfach an den Klappenöffnungen befestigt werden konnten.  
  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/System%20in%20Verpackung.JPG" alt="image" width="400">  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/briefkasten.JPG" alt="image" width="400">  
  
Auch im Seriellen Monitor erfolgt eine Ausgabe. Dabei bedeutet die Null immer, dass die Pushnachricht von dem Pushover-Server mit TRUE beantwortet wurde.  
  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/image%20Serieller%20Monitor%202.PNG" alt="image" width="400">  
  
Pushnotification:  
<img src="https://github.com/lakgiter/Informatik-Projekt-3/blob/master/images/Status%20auf%20Mobilgerät.PNG" alt="image" width="400">  


### Schlusswort <a name="Schlusswort"></a>  

Damit wurde mein erstes Smarthome-Projekt fertiggestellt und der Alltag um eine weitere Kleinigkeit erleichtert. Möglicherweise lässt sich die NTP-Bibliothek auch zukünftig in das Wecker-Projekt integrieren. Auch die millis-Funktion könnte zukünfig dabei helfen parallele Aufgaben auszuführen.
Der Github Blog wurde mit Hilfe der <a href="https://guides.github.com/features/mastering-markdown/Mardown-Übersicht">Markdown-Übersicht<a/> erstellt.  
   
<a href="https://github.com/lakgiter/Projektpraesentation-3">Präsentation meines Projektes<a/>

