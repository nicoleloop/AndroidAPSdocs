# xDrip+ Einstellungen

(For additional information regarding xDrip+, please refer to https://xdrip.readthedocs.io/en/latest/)

If not already set up then download [xDrip+](https://jamorham.github.io/#xdrip-plus).

**This documentation is for xDrip+ for Android only.** There is an app "xDrip for iOS" that has nothing to do with the original xDrip+ for Android.

G6 Transmitter, die nach Herbst / Ende 2018 (z.B. Seriennummer starting with 80 or 81) you can use the [master](https://jamorham.github.io/#xdrip-plus) version.

Falls die Seriennummer Deines G6 Transmitters is starting with 8G..., 8H... or 8J... use one of the [latest nightly builds](https://github.com/NightscoutFoundation/xDrip/releases).

If your phone runs Android 10 and you have difficulties with xDrip+ master try [nightly build 2019/12/31 or later](https://github.com/NightscoutFoundation/xDrip/releases).

## Grundsätzliche Einstellungen für alle CGM & FGM-Systeme

* Stelle sicher, dass Du die Base URL korrekt eingibst - inkl. **S** am Ende von http**s**:// (nicht http://).
   
   z.B. https://API_SECRET@your-app-name.herokuapp.com/api/v1/
   
   -> Hamburger Menü (oben links auf dem Starbildschirm) -> Einstellungen-> Cloud Upload-> API Upload (REST) -> Basis-URL

* Deaktiviere `Automatic Calibration` Falls die Checkbox für `Automatic Calibration` ausgewählt ist, aktiviere `Download data` einmalig, entferne dann den Haken in der Checkbox für `Automatic Calibration` und deaktiviere `Download data` wieder. Sonst werden die Behandlungen (Insulin & Kohlenhydrate) doppelt in Nightscout eingetragen.

* Tippe auf `Extra Options`.

* Deaktiviere `Upload treatments` und `Back-fill data`.
   
   **Sicherheitshinweis: Du musst "Upload treatments" in xDrip+ deaktivieren, da sonst die Behandlungen in AAPS doppelt erscheinen können. Dies würde zu falschen COB und IOB führen.**

* Die Option `Alert on failures` sollte ebenfalls deaktiviert sein. Andernfalls erhältst Du alle 5 Minuten einen Alarm, falls das WLAN / Mobilfunknetz zu schlecht oder der Server nicht verfügbar ist.
   
   ![xDrip+ Grundeinstellungen 1](../images/xDrip_Basic1.png)
   
   ![xDrip+ Grundeinstellungen 2](../images/xDrip_Basic2.png)

* **InterApp-Einstellungen** (Broadcast) Wenn Du planst, AndroidAPS zu nutzen und die Daten an AndroidAPS weiterzugeben, musst Du den sogenannten 'Broadcast' in xDrip+ in den Inter-App Einstellungen einschalten.

* Damit die Werte übereinstimmen, solltest Du `Sende den angezeigten Glukosewert` aktivieren.

* Wenn Du zusätzlich `Behandlungen annehmen` und in AndroidAPS "Aktiviere lokale Broadcasts" auswählst, dann wird xDrip+ Insulinmengen, Kohlenhydrate und Basalrateninformationen aus AndroidAPS erhalten und kann so z.B. niedrige Werte vorhersagen. 
   
   ![xDrip+ Grundeinstellungen 3](../images/xDrip_Basic3.png)

### Identifiziere Empfänger

* If you discover problems with local broadcast (AAPS not receiving BG values from xDrip+) go to Settings > Inter-app settings > Identify receiver and enter `info.nightscout.androidaps` for AndroidAPS build (if you are using PumpControl build, please enter `info.nightscout.aapspumpcontrol` instead!!).
* Achtung: Die Auto-Korrektur neigt manchmal dazu, das i von info in einen Großbuchstaben zu ändern. You **must use only lowercase letters** when typing `info.nightscout.androidaps` (or `info.nightscout.aapspumpcontrol` for PumpControl). Capital I would prevent the App from receiving BG values from xDrip+.
   
   ![xDrip+ Basic Inter-App Einstellungen Identifiziere Empfänger](../images/xDrip_InterApp_NS.png)

## xDrip+ mit Dexcom G6

* Der Dexcom G6-Transmitter kann gleichzeitig mit einem Dexcom-Empfänger (oder alternativ mit der t:slim-Pumpe) und einer App auf dem Handy verbunden werden.
* Wenn Du xDrip+ zum Empfang der CGM-Daten verwendest, deinstalliere zuerst die Dexcom App. **Du kannst xDrip+ und die Dexcom App nicht gleichzeitig mit dem Transmitter verbinden!**
* Falls Du Clarity benötigst und trotzdem von den xDrip+ Alarmen profitieren willst, musst Du die ['Build Your Own Dexcom App](../Hardware/DexcomG6#g6-mit-build-your-own-dexcom-app) mit lokaler Datenübertragung zu xDrip+ verwenden.

### xDrip+ Version abhängig von der G6 Transmitter Seriennummer

* G6 Transmitter, die nach Herbst / Ende 2018 (z.B. Seriennummer beginnt mit 80 oder 81) hergestellt wurden, benötigen mindestens die [xDrip+ master](https://jamorham.github.io/#xdrip-plus) version. 
* Falls die Seriennummer Deines G6 Transmitters mit 8G, 8H oder 8J beginnt, verwende einen der letzten [nightly builds](https://github.com/NightscoutFoundation/xDrip/releases).

### Dexcom-spezifische Einstellungen

* Öffne G5 Debug Einstellungen (gilt auch für Dexcom G6!) -> Hamburger Menü (oben links auf dem Homescreen) -> Einstellungen -> G5 Debug Einstellungen ![xDrip+ Einstellungen öffnen](../images/xDrip_Dexcom_SettingsCall.png)

* Aktiviere die folgenden Einstellungen:
   
   * `Use the OB1 Collector`
   * `Native Algorithm` (wichtig, wenn Du SMB benutzen willst)
   * `G6 support`
   * `Allow OB1 unbonding`
   * `Allow OB1 initiate bonding`
* Alle anderen Optionen sollten deaktiviert werden.
* Passe die Warnschwelle für die Batterie ('Adjust battery warning level') auf 280 an. (Du findest diese ganz unten in der Liste der G5/G6 Debug Settings.)
   
   ![xDrip+ G5 Debugeinstellungen](../images/xDrip_Dexcom_DebugSettings.png)

### Preemptive restarts werden nicht empfohlen

**With Dexcom transmitters who's serial no. is starting with 8G, 8H or 8J preemptive restarts do not work and might kill the sensor completely!**

The automatic extension of Dexcom sensors (`preemptive restarts`) is not recommended as this might lead to “jumps” in BG values on day 9 after restart.

![xDrip+ Jump after Preemptive Restart](../images/xDrip_Dexcom_PreemptiveJump.png)

Die Nutzung des G6 kann vielleicht etwas komplexer sein, als zunächst vermutet. Mache Dir die folgenden Punkte bewusst, um das System sicher zu nutzen:

* Wenn Du mit nativen Daten und dem Kalibrierungscode in xDrip+ oder Spike arbeitest, ist es am sichersten, auf den "preemptive" Neustart des Sensors zu verzichten.
* Falls Du den "preemptive restart" verwendest, stelle sicher, dass dieser zu einer Tageszeit erfolgt, zu der Du die Änderungen verfolgen und ggf. durch eine Kalibrierung eingreifen kannst. 
* Falls Du Sensoren verlängerst, verzichte aus Sicherheitsgründen entweder auf die Werkskalibrierung an Tag 11 und 12 oder stelle sicher, dass Du die Abweichungen im Auge hast und evtl. durch Kalibrierung korrigieren kannst.
* Das sogenannte "Pre-soaking" (Sensor früher ohne Transmitter setzen, damit er sich an die Gewebsflüssigkeit "gewöhnt") mit Werkskalibrierung führt wahrscheinlich zu Abweichungen in den Glukosewerten. Falls Du mit "pre-soaking" arbeitest, wirst Du wahrscheinlich besser Ergebnisse erzielen, wenn Du den Sensor kalibrierst.
* Wenn Du nicht auf die Abweichungen, die stattfinden können, achten willst, wäre es evtl. besser bei der Verlängerung auf die Werkskalibrierung zu verzichten und das System wie den G5 (mit "Pflichtkalibrierung") zu nutzen.

To learn more about the details and reasons for these recommendations read the [complete article](https://www.diabettech.com/artificial-pancreas/diy-looping-and-cgm/) published by Tim Street at [www.diabettech.com](https://www.diabettech.com).

### G6 Transmitter das erste Mal verbinden

**For second and following transmitters see [Extend transmitter life](#extend-transmitter-life) below.**

G6 Transmitter, die nach Herbst / Ende 2018 (z.B. Seriennummer beginnt mit 80 oder 81) hergestellt wurden, benötigen mindestens die [xDrip+ master](https://jamorham.github.io/#xdrip-plus) version.

Falls die Seriennummer Deines G6 Transmitters mit 8G, 8H oder 8J beginnt, verwende einen der letzten [nightly builds](https://github.com/NightscoutFoundation/xDrip/releases).

* Schalte den Original Dexcom Empfänger aus (falls Du diesen verwendet).
* Drücke auf der Startseite lang auf den roten Blutstropfen des xDrip+ Logos, um den `Source Wizard Button` zu aktivieren.
* Benutze den Source Wizard Button. Damit wird sicher gestellt, dass Du die Standardeinstellungen inkl. OB1 & Native Mode verwendest. 
   * Du wirst durch die Grundeinstellungen geführt.
   * Wenn Du den Transmitter zum ersten Mal verbindest, benötigst Du die Transmitter-Seriennummer.

* Gib die Seriennummer des Transmitters, die Du auf der Transmitter-Verpackung und auf der Rückseite des Transmitters findest, ein. Achte darauf, `0` (null) und `O` (Großbuchstabe o) nicht zu verwechseln.
   
   ![xDrip+ Dexcom Transmitter Seriennummer](../images/xDrip_Dexcom_TransmitterSN.png)

* Setze den neuen Sensor (außer Du tauscht den Transmitter während einer laufenden Sensorsitzung).

* Klicke den Transmitter in die Halterung auf dem Sensorpflaster ein.
* Wenn eine Nachricht Pair with 'DexcomXX' (XX steht dabei für die letzten beiden Stellen der Transmitter-Seriennummer) erscheint, akzeptiere diese und drücke "Pair" (Verbinden).
* * Starte den neuen Sensor NICHT bevor eine der folgenden Informationen auf der Classic Status Page -> G5/G6 status -> PhoneServiceState angezeigt wird:
   
   * Transmitter Seriennummer beginnt mit 80 oder 81: "Got data hh:mm" (z.B. "Got data 19:04")
   * Transmitter Seriennummer beginnt mit 8G, 8H oder 8J: "Got glucose hh:mm" (z.B. "Got glucose 19:04") oder "Got no raw hh:mm" (z.B. "Got no raw 19:04")
   
   ![xDrip+ PhoneServiceState](../images/xDrip_Dexcom_PhoneServiceState.png)

* Starte den neuen Sensor (außer Du tauscht den Transmitter während einer laufenden Sensorsitzung).
   
   -> Am unteren Bildschirmrand nach einigen Minuten wird `Warm Up x,x Stunden left` angezeigt.

-> If your transmitter serial no. does not start with 8G, 8H or 8J and there is no time specification after a few minutes stop and restart the sensor.

* Starte den Datensammler neu (im Systemstatus und nur, wenn Du den Sensor neu gesetzt hast).
* Falls Du den Dexcom Empfänger nutzt, schalte diesen nicht ein, bevor xDrip+ die ersten BZ-Werte anzeigt.
* Drücke auf der Startseite lang auf den roten Blutstropfen des xDrip+ Logos, um den `Source Wizard Button` zu deaktivieren.
   
   ![xDrip+ Dexcom Transmitter 1](../images/xDrip_Dexcom_Transmitter01.png)
   
   ![xDrip+ Dexcom Transmitter 2](../images/xDrip_Dexcom_Transmitter02.png)
   
   ![xDrip+ Dexcom Transmitter 3](../images/xDrip_Dexcom_Transmitter03.png)
   
   ![xDrip+ Dexcom Transmitter 4](../images/xDrip_Dexcom_Transmitter04.png)

### Transmitter-Batteriestatus

* Der Batteriestatus kann im Systemstatus (Hamburgermenü links oben auf dem Startbildschirm) überwacht werden.
* Wische nach links, um den zweiten Status-Bildschirm zu sehen.![xDrip+ Erster Transmitter](../images/xDrip_Dexcom_Battery.png)

* Die genauen Werte, nach denen der Transmitter aufgrund niedrigem Batteriestand ausfällt, sind nicht bekannt. Die folgenden Informationen wurden online gepostet, nachdem der Transmitter die Arbeit endgültig eingestellt hatte:
   
   * Posting 1: Laufzeit: 151 Tage / Voltage A: 297 / Voltage B: 260 / Resistance: 2391
   * Posting 2: Laufzeit: 249 Tage / Voltage A: 275 (bei Auftritt des Fehlers)

### Transmitterlaufzeit verlängern

* Bisher kann die Laufzeit von Transmittern, deren Seriennummer mit 8G, 8H oder 8J beginnt, nicht verlängert werden. Das Gleiche gilt für Transmitter deren Seriennummer mit 81 beginnt und die die Firmware 1.6.5.**27** (siehe xDrip+ System Status - G5/G6 Status wie im [Screenshot oben beschrieben](../Configuration/xdrip#transmitter-batteriestatus)) haben).
* Um Schwierigkeiten beim Start von Sensoren zu vermeiden, wird dringend empfohlen, den Transmitter vor Ablauf des 100. Tags der ersten Nutzung zu verlängern.
* Die Verwendung von Transmittern deren Seriennr. 81 beginnt und Firmware 1.6.5.**27** haben nach Tag 100 ist nur möglich, wenn der 'engineering mode' eingeschaltet ist und 'native mode' deaktiviert wird (Hamburger Menü -> Einstellungen -> G5 Debugeinstellungen -> Native Algorithm).
* Eine laufende Sensorsitzung wird gestoppt, wenn Du die Transmitterlaufzeit verlängerst. Verlängere daher bei einem Sensorwechsel oder sei Dir bewusst, dass nach der Verlängerung eine neue zweistündige Warm-Up-Phase des Sensors beginnt.
* Stoppe den Sensor manuell über das Hamburger-Menü.
* Wechsle in den `engineering mode`: 
   * Klicke auf das Spritzen-Symbol rechts auf dem xDrip+ Startbildschirm.
   * Klicke dann auf das Mikrophon-Symbol in der unteren rechten Ecke.
   * Gib in das Textfeld, das geöffnet wird, "enable engineering mode" ein und klicken auf OK. 
   * Klicke auf "Done".
   * Falls Du die Google Speak engine nutzt, kannst Du auch das Sprachkommando "enable engineering mode" nutzen. 
* Wechsle zu den G5 Debugeinstellungen und stelle sicher, dass `Use the OB1 collector` is aktiviert ist.
* Benutze den Sprachbefehl: “hard reset transmitter”
* Beim nächsten Dateneingang vom Transmitter wird der Reset durchgeführt.
* Beobachte im Systemstatus (Hamburgermenü links oben -> Systemstatus) was passiert.
* Nach etwa 10 min. kannst Du auf die 'Classic Status Page' wechseln (nach rechts wischen) und 'Datensammler neu starten' klicken. Dadurch werden die Sensortage auf 0 gesetzt, ohne dass ein neuer Sensor gestartet werden muss.
* Alternative: Wenn auf dem zweiten Statusbildschirm der Hinweis "Phone Service State: Hard Reset maybe failed" angezeigt wird, kannst Du trotzdem einfach den Sensor starten. Danach sollte diese Meldung verschwinden.
   
   ![xDrip+ Hard Reset maybe failed](../images/xDrip_HardResetMaybeFailed.png)

* Die "Transmitter days" werden nach erfolgreicher Verlängerung und Start des Sensors auf 0 zurückgesetzt.

### Transmitter ersetzen

G6 Transmitter, die nach Herbst / Ende 2018 (z.B. Seriennummer beginnt mit 80 oder 81) hergestellt wurden, benötigen mindestens die [xDrip+ master](https://jamorham.github.io/#xdrip-plus) version.

Falls die Seriennummer Deines G6 Transmitters is starting with 8G, 8H or 8Juse one of the [latest nightly builds](https://github.com/NightscoutFoundation/xDrip/releases).

* Schalte den Original Dexcom Empfänger aus (falls Du diesen verwendet).
* Stoppe den Sensor (außer Du tauscht den Transmitter während einer laufenden Sensorsitzung).
   
   Stelle sicher, dass er tatsächlich gestoppt ist.
   
   Schaue auf dem zweiten "G5/G6 Status" Bildschirm nach `Queue Items` (etwa in der Mitte) - dort wird `(1) Stop Sensor` oder ähnlich angezeigt.
   
   Warte, bis diese Meldung verschwindet. Erfahrungsgemäß dauert dies einige Minuten. Beim Sensor Status muss "Stopped" stehen (siehe Screenshot).
   
   -> Eine Videoanleitung zum Wechsel des Transmitters ohne den Sensor zu stoppen findest Du unter <https://youtu.be/AAhBVsc6NZo>.
   
   ![xDrip+ Dexcom Sensor 1 stoppen](../images/xDrip_Dexcom_StopSensor.png)
   
   ![xDrip+ Dexcom Sensor 2 stoppen](../images/xDrip_Dexcom_StopSensor2.png)

* Gerät in den Bluetooth-Einstellungen von xDrip+ UND des Smartphones löschen (wird als Dexcom?? angezeigt, dabei steht ?? für die letzten beiden Zeichen der Seriennummer Deines Transmitters).
   
   ![xDrip+ Gerät löschen](../images/xDrip_Dexcom_ForgetDevice.png)

* Entferne den Transmitter (und den Sensor, falls Du auch diesen wechselst).

* Lege den alten Transmitter weit weg, um eine erneute Verbindung zu verhindern. Eine Mikrowelle bildet dafür einen hervorragenden Faraday'schen Käfig - ziehe aber den Stromstecker um 100% sicher zu sein, dass die Mikrowelle nicht versehentlich eingeschaltet wird.
* Drücke auf der Startseite lang auf den roten Blutstropfen des xDrip+ Logos, um den `Source Wizard Button` zu aktivieren.
* Benutze den Source Wizard Button. Damit wird sicher gestellt, dass Du die Standardeinstellungen inkl. OB1 & Native Mode verwendest. 
   * Du wirst durch die Grundeinstellungen geführt.
   * Wenn Du den Transmitter zum ersten Mal verbindest, benötigst Du die Transmitter-Seriennummer.
* Gib die Seriennummer des neuen Transmitters ein. Achte darauf, 0 (Null) und O (Großbuchstabe o) korrekt auseinander zu halten.
* Setze den neuen Sensor (außer Du tauscht den Transmitter während einer laufenden Sensorsitzung).
* Setze den Transmitter in die Aufnahme des Sensors - **starte den Sensor aber nicht sofort!**
* Die neuen "Firefly Transmitter" (Seriennr. beginnt mit 8G, 8H oder 8J) können nur im "nativ mode" verwendet werden.
* Die folgenden Optionen dürfen für neue "Firefly Transmitter" NICHT aktiviert werden (Seriennr. beginnt mit 8G, 8H oder 8J).
   
   * Preemptive Restart (Ausschalten!)
   * Restart sensor (Ausschalten!)
   * Fallback to xDrip+ (Ausschalten!)
   
   ![Einstellungen für Firefly Transmitter](../images/xDrip_Dexcom_FireflySettings.png)

* Prüfe, ob auf der Classic Status Page -> G5/G6 status -> PhoneServiceState eine der folgenden Informationen angezeigt wird:
   
   * Transmitter Seriennummer beginnt mit 80 oder 81: "Got data hh:mm" (z.B. "Got data 19:04")
   * Transmitter Seriennummer beginnt mit 8G, 8H oder 8J: "Got glucose hh:mm" (z.B. "Got glucose 19:04") oder "Got no raw hh:mm" (z.B. "Got now raw 19:04")
   
   ![xDrip+ PhoneServiceState](../images/xDrip_Dexcom_PhoneServiceState.png)

* Warte 15 Minuten. Der Transmitter sollte mehrfach mit xDrip kommunizieren, bevor Du einen neuen Sensor startest. Batteriedaten werden unterhalb der Informationen zur Firmware angezeigt, sobald es soweit ist.
   
   ![Firefly Transmitter Batteriedaten](../images/xDrip_Dexcom_FireflyBattery.png)

* Starte den Sensor OHNE RÜCKDATIERUNG! Wähle immer "Yes, today"!

* Starte den Datensammler neu (im Systemstatus und nur, wenn Du den Sensor neu gesetzt hast).
* Falls Du den Dexcom Empfänger nutzt, schalte diesen nicht ein, bevor xDrip+ die ersten BZ-Werte anzeigt.
* Drücke auf der Startseite lang auf den roten Blutstropfen des xDrip+ Logos, um den `Source Wizard Button` zu deaktivieren.
   
   ![xDrip+ Dexcom Transmitter 1](../images/xDrip_Dexcom_Transmitter01.png)
   
   ![xDrip+ Dexcom Transmitter 2](../images/xDrip_Dexcom_Transmitter02.png)
   
   ![xDrip+ Dexcom Transmitter 3](../images/xDrip_Dexcom_Transmitter03.png)
   
   ![xDrip+ Dexcom Transmitter 4](../images/xDrip_Dexcom_Transmitter04.png)

### Neuer Sensor

* Schalte den Original Dexcom Empfänger aus (falls Du diesen verwendet).
* Stoppe den alten Sensor - falls erforderlich.
   
   Stelle sicher, dass er tatsächlich gestoppt ist.
   
   Schaue auf dem zweiten "G5/G6 Status" Bildschirm nach `Queue Items` (etwa in der Mitte) - dort wird `(1) Stop Sensor` oder ähnlich angezeigt.
   
   Warte, bis diese Meldung verschwindet. Erfahrungsgemäß dauert dies einige Minuten.
   
   ![xDrip+ Dexcom Sensor 1 stoppen](../images/xDrip_Dexcom_StopSensor.png)
   
   ![xDrip+ Dexcom Sensor 2 stoppen](../images/xDrip_Dexcom_StopSensor2.png)

* Reinige die Kontakte (Transmitter-Rückseite) mit Alkohol und lasse sie an der Luft trocknen.

* Falls Du diese Funktionen verwendest: Deaktiviere `Restart Sensor` und `Preemptive restarts` (Hamburger Menü -> Einstellungen -> G5 Debugeinstellungen). Wenn Du diese Funktionen nicht deaktivierst, wird der neue Sensor nicht richtig starten.
   
   ![xDrip+ Preemptive Restart](../images/xDrip_Dexcom_Restart.png)

* Starte den Sensor
   
   ** Für neue Firefly-Transmitter ** (Seriennr. beginnt mit 8G, 8H oder 8J)** muss zwischen Stopp des alten Sensors und Start des neuen Sensors mind. 15 Minuten gewartet werden (bis `Sensor Status: Stopped` auf dem zweiten Systemstatus-Bildschirm angezeigt wird). Bei anderen Transmittern wird das Warten empfohlen. KEINE RÜCKDATIERUNG!**

* Gib die Zeit an, zu der der Sensor gesetzt wurde
   
   * Um den G6 im "native mode" zu nutzen, musst Du die 2-Stunden-Aufwärmzeit abwarten.
   * Wenn Du den xDrip+ Algorithmus verwendest, kannst Du eine Setzzeit von mehr als zwei Stunden in der Vergangenheit setzen, um die Aufwärmphase zu umgehen. Die angezeigten Werte können dann aber recht fehlerhaft sein. Deshalb wird dies nicht empfohlen.
* Gib den Sensorcode ein. Diesen findest Du auf der Abdeckfolie des Sensorpflasters. 
   * Bewahre diesen Code für künftige Nutzung auf (z.B. für einen Neustart nach Tausch des Transmitters).
   * Der Code ist auch in den [xDrip+ Logs](../Configuration/xdrip#sensorcode-in-den-logs-finden) zu finden: Klicke auf das 3-Punkte-Menü rechts oben auf dem xDrip+ Startbildschirm und wähle `Log anzeigen`.
* Kalibrierungen sind nicht notwendig, wenn Du den G6 im "native mode" verwendest. xDrip+ wird nach der zweistündigen Aufwärmphase automatisch die erste BZ-Werte anzeigen.
* Falls Du den Dexcom Empfänger nutzt, schalte diesen nicht ein, bevor xDrip+ die ersten BZ-Werte anzeigt.
   
   ![xDrip+ Sensor starten 1](../images/xDrip_Dexcom_SensorStart01.png)
   
   ![xDrip+ Sensor starten 2](../images/xDrip_Dexcom_SensorStart02.png)

### Sensorcode in den Logs finden

* Wenn Du den Master vom 18.05.2019 oder einen der letzten Nightly Builds verwendest, wird der Sensorcode im Systemstatus angezeigt (Hamburger Menü links oben auf dem Startbildschirm).
* Wische nach links, um den zweiten Status-Bildschirm zu sehen.
   
   ![xDrip+ Dexcom Sensorcode ermitteln (Status Bildschirm)](../images/xDrip_Dexcom_SensorCode2.png)

* Der Dexcom Sensorcode findet sich auch in den xDrip+ Logs.

* Tippe auf das 3-Punkte-Menü (oben rechts auf dem Homescreen).
* Wähle `Log anzeigen` und suche nach "code".
   
   ![xDrip+ Dexcom Sensorcode ermitteln (Log Files)](../images/xDrip_Dexcom_SensorCode.png)

## Fehlerbehebung Dexcom G5/G6 und xDrip+

### Problem beim Verbinden mit dem Transmitter

* Der Transmitter muss in den Bluetooth-Einstellungen Deines Smartphones angezeigt werden.
* Transmitter wird als Dexcom?? angezeigt, dabei steht ?? für die letzten beiden Zeichen der Seriennummer Deines Transmitters (z.B. DexcomHY).
* Öffne den Systemstatus in xDrip+ (Hamburger Menü oben links auf dem Startbildschirm).
* Überprüfe, ob der Transmitter auf der ersten Statusseite angezeigt wird ('classic status page').
* Wenn nicht: Lösche den Transmitter aus den Bluetooth-Einstellungen Deines Smartphones und starte den Datensammler neu.
* Warte etwa 5 Minuten bis der Transmitter wieder automatisch verbunden wird.

### Probleme beim Starten eines neuen Sensors

Please note that the following method might likely not work if your Dexcom G6 transmitter's serial no. is starting with 8G, 8H or 8J.

* Im 'native mode' wird der Sensor als "FAILED: Sensor Failed Start" gekennzeichnet.
* Sensor stoppen
* Starte dein Smartphone neu
* Starte den Sensor mit Code 0000 (viermal Null)
* Warte 15 Minuten
* Sensor stoppen
* Starte den Sensor mit dem "tatsächlichen" Code, den Du auf dem Schutzpapier des Pflasters findest.

Check in xDrip+ logs if xDrip+ starts counting "Duration: 1 minute" (and so on). Only in the xDrip+ logs you can detect at an early stage whether xdrip+ has stopped a sensor. Latest status is not always shown correctly on bottom of startscreen.

## xDrip+ mit Freestyle Libre

### Libre-spezifische Einstellungen

* Öffne die Bluetooth Einstellungen -> Hamburger Menü (oben links auf dem Startbildschirm) -> Einstellungen -> scrolle nach unten -> Erweiterte Einstellungen -> Bluetootheinstellungen
   
   ![xDrip+ Libre Bluetooth Einstellungen 1](../images/xDrip_Libre_BTSettings1.png)

* Aktiviere die folgenden Einstellungen:
   
   * `Schalte Bluetooth ein` 
   * `Verwende Scannen`
   * `Dienste immer ermitteln`

* Alle anderen Optionen sollten deaktiviert werden.
   
   ![xDrip+ Libre Bluetooth Einstellungen 2](../images/xDrip_Libre_BTSettings2.png)

### Batteriestand Libre Smart Reader

* Der Batteriestand eines Smart Readers wie z.B. des MiaoMiao 2 kann in AAPS angezeigt werden.
* Weitere Details auf der Seite [AndroidAPS Bildschirme](../Getting-Started/Screenshots#sensor-level-batterie).

### Libre Transmitter verbinden und Sensor starten

![xDrip+ Start Libre Transmitter & Sensor 1](../images/xDrip_Libre_Transmitter01.png)

![xDrip+ Start Libre Transmitter & Sensor 2](../images/xDrip_Libre_Transmitter02.png)

![xDrip+ Start Libre Transmitter & Sensor 3](../images/xDrip_Libre_Transmitter03.png)