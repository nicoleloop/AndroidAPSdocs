# Ρυθμίσεις xDrip+

(For additional information regarding xDrip+, please refer to https://xdrip.readthedocs.io/en/latest/)

If not already set up then download [xDrip+](https://jamorham.github.io/#xdrip-plus).

**This documentation is for xDrip+ for Android only.** There is an app "xDrip for iOS" that has nothing to do with the original xDrip+ for Android.

Για τους πομπούς G6 που κατασκευάστηκαν μετά το πέρας / τέλος του 2018 (δηλ. με σειριακό αριθμό. starting with 80 or 81) you can use the [master](https://jamorham.github.io/#xdrip-plus) version.

Εάν ο σειριακός αριθμός του πομπού Dexcom G6. is starting with 8G..., 8H... or 8J... use one of the [latest nightly builds](https://github.com/NightscoutFoundation/xDrip/releases).

If your phone runs Android 10 and you have difficulties with xDrip+ master try [nightly build 2019/12/31 or later](https://github.com/NightscoutFoundation/xDrip/releases).

## Βασικές ρυθμίσεις για όλα τα CGM & FGM Συστήματα

* Βεβαιωθείτε ότι έχετε ορίσει σωστά τη διεύθυνση URL, συμπεριλαμβανομένου του ** S ** στο τέλος του http **s **: // (όχι http: //)
   
   π.χ https://API_SECRET@your-app-name.herokuapp.com/api/v1/
   
   -> Μενού Hamburger (επάνω αριστερά της αρχικής οθόνης) -> Ρυθμίσεις-> Ανεβάζουμε στο Cloud-> συγχρονισμός Nightscout (REST-API) -> βάση URL

* Απενεργοποίηστε την ` Αυτόματη βαθμονόμηση ` Εάν έχει επιλεγεί το πλαίσιο ελέγχου ` Αυτόματη βαθμονόμηση `, ενεργοποιήστε μία φορά ` Λήψη δεδομένων ` και αφαιρέστε το πλαίσιο ελέγχου ` Αυτόματη βαθμονόμηση ` / 0> ξανά, διαφορετικά οι θεραπείες (ινσουλίνη & υδατάνθρακες) θα προστεθούν δύο φορές στη Nightscout.

* Tap `Extra Options`

* Deactivate `Upload treatments` and `Back-fill data`.
   
   **Safety warning : You must deactivate "Upload treatments" from xDrip+, otherwise treatments can be doubled in AAPS leading to false COB and IOB.**

* Η επιλογή ` Ειδοποίηση για αποτυχίες ` θα πρέπει επίσης να απενεργοποιηθεί. Διαφορετικά, θα λάβετε ένα συναγερμό κάθε 5 λεπτά σε περίπτωση που το δίκτυο wifi / κινητής τηλεφωνίας είναι πολύ κακό ή ο διακομιστής δεν είναι διαθέσιμος.
   
   ![xDrip + Βασικές ρυθμίσεις 1](../images/xDrip_Basic1.png)
   
   ![xDrip + Βασικές ρυθμίσεις 2](../images/xDrip_Basic2.png)

* ** Ρυθμίσεις InterApp ** (Broadcast) Εάν πρόκειται να χρησιμοποιήσετε το AndroidAPS και τα δεδομένα πρέπει να προωθηθούν π.χ. στο AndroidAPS, πρέπει να ενεργοποιήσετε τη μετάδοση στο xDrip + στις ρυθμίσεις Inter-App.

* In order for the values to be equal, you should activate `Send the displayed glucose value`.

* If you have also activated `Accept treatments` and "Enable local Broadcasts" in AndroidAPS, then xDrip+ will receive insulin, carbs and basal rate information from AndroidAPS and can estimate the hypo prediction etc. με καλύτερη ακρίβεια.
   
   ![+xDrip Βασικές ρυθμίσεις 3](../images/xDrip_Basic3.png)

### Προσδιορίστε δέκτη

* If you discover problems with local broadcast (AAPS not receiving BG values from xDrip+) go to Settings > Inter-app settings > Identify receiver and enter `info.nightscout.androidaps` for AndroidAPS build (if you are using PumpControl build, please enter `info.nightscout.aapspumpcontrol` instead!!).
* Pay attention: Auto-correction sometimes tend to change i to capital letter. You **must use only lowercase letters** when typing `info.nightscout.androidaps` (or `info.nightscout.aapspumpcontrol` for PumpControl). Capital I would prevent the App from receiving BG values from xDrip+.
   
   ![+xDrip Basic Inter-app Ρυθμίσεις Προσδιορίζουν δέκτη](../images/xDrip_InterApp_NS.png)

## xDrip+ & Dexcom G6

* The Dexcom G6 transmitter can simultaneously be connected to the Dexcom receiver (or alternatively the t:slim pump) and one app on your phone.
* When using xDrip+ as receiver uninstall Dexcom app first. **You cannot connect xDrip+ and Dexcom app with the transmitter at the same time!**
* If you need Clarity and want to profit from xDrip+ alarms use the [Build Your Own Dexcom App](../Hardware/DexcomG6#if-using-g6-with-build-your-own-dexcom-app) with local broadcast to xDrip+.

### xDrip + έκδοση ανάλογα με τον σειριακό αριθμό του πομπού G6.

* Για τους πομπούς G6 που κατασκευάστηκαν μετά το πέρας / τέλος του 2018 (δηλ. με σειριακό αριθμό. starting with 80 or 81) you can use the [master](https://jamorham.github.io/#xdrip-plus). 
* Εάν ο σειριακός αριθμός του πομπού Dexcom G6. is starting with 8G, 8H or 8J try [nightly build 2019/07/28 or later](https://github.com/NightscoutFoundation/xDrip/releases).

### Dexcom συγκεκριμένες ρυθμίσεις

* Open G5/G6 Debug Settings -> Hamburger Menu (top left of homescreen) -> Settings -> G5/G6 Debug Settings ![Open xDrip+ Settings](../images/xDrip_Dexcom_SettingsCall.png)

* Enable the following settings
   
   * `Use the OB1 Collector`
   * `Native Algorithm` (important if you want to use SMB)
   * `G6 support`
   * `Allow OB1 unbonding`
   * `Allow OB1 initiate bonding`
* All other options should be disabled
* Adjust battery warning level to 280 (bottom of G5/G6 Debug Settings)
   
   ![xDrip+ G5/G6 Debug Settings](../images/xDrip_Dexcom_DebugSettings.png)

### Οι προληπτικές επανεκκινήσεις δεν συνιστώνται

**With Dexcom transmitters who's serial no. is starting with 8G, 8H or 8J preemptive restarts do not work and might kill the sensor completely!**

The automatic extension of Dexcom sensors (`preemptive restarts`) is not recommended as this might lead to “jumps” in BG values on day 9 after restart.

![xDrip+ Jump after Preemptive Restart](../images/xDrip_Dexcom_PreemptiveJump.png)

Αυτό που είναι σαφές είναι ότι η χρήση του G6 είναι ίσως λίγο πιο πολύπλοκη από ό, τι φαίνεται. Για να το χρησιμοποιήσετε με ασφάλεια, υπάρχουν μερικά σημεία που πρέπει να γνωρίζετε:

* If you are using the native data with the calibration code in xDrip+ or Spike, the safest thing to do is not allow preemptive restarts of the sensor.
* If you must use preemptive restarts, then make sure you insert at a time of day where you can observe the change and calibrate if necessary. 
* If you are restarting sensors, either do it without the factory calibration for safest results on days 11 and 12, or ensure you are ready to calibrate and keep an eye on variation.
* Pre-soaking of the G6 with factory calibration is likely to give variation in results. Αν κάνετε προ-εμβάπτιση, τότε για να έχετε τα καλύτερα αποτελέσματα, πιθανόν να χρειαστεί να βαθμονομήσετε τον αισθητήρα.
* If you aren’t being observant about the changes that may be taking place, it may be better to revert to non-factory-calibrated mode and use the system like a G5.

To learn more about the details and reasons for these recommendations read the [complete article](https://www.diabettech.com/artificial-pancreas/diy-looping-and-cgm/) published by Tim Street at [www.diabettech.com](https://www.diabettech.com).

### Συνδέστε το πομπό G6 για πρώτη φορά

**For second and following transmitters see [Extend transmitter life](#extend-transmitter-life) below.**

Για τους πομπούς G6 που κατασκευάστηκαν μετά το πέρας / τέλος του 2018 (δηλ. με σειριακό αριθμό. starting with 80 or 81) you can use the [master](https://jamorham.github.io/#xdrip-plus).

Εάν ο σειριακός αριθμός του πομπού Dexcom G6. is starting with 8G, 8H or 8J try [nightly build 2019/07/28 or later](https://github.com/NightscoutFoundation/xDrip/releases).

* Turn original Dexcom receiver off (if used).
* Long press the red xDrip+ blood drop icon on the main screen to enable the `Source Wizard Button`.
* Use the Source Wizard Button which ensures default settings including OB1 & Native Mode 
   * This guides you through the initial set up.
   * you will need your transmitter serial number if this is the first time you've used it.

* Put in serial number of new transmitter (on the transmitter packaging or on the back of the transmitter). Be careful not to confuse `0` (zero) and `O` (capital letter o).
   
   ![xDrip+ Dexcom Transmitter Serial No](../images/xDrip_Dexcom_TransmitterSN.png)

* Insert new sensor (only if replacing)

* Put transmitter into sensor
* If a message pops up asking to pair with "DexcomXX", where "XX" is the last two characters of the transmitter's serial no., accept it (tap "pair")
* Do not start new sensor before the following information is shown in Classic Status Page -> G5/G6 status -> PhoneServiceState:
   
   * Transmitter serial starting with 80 or 81: "Got data hh:mm" (i.e. "Got data 19:04")
   * Transmitter serial starting with 8G, 8H or 8J: "Got glucose hh:mm" (i.e. "Got glucose 19:04") or "Got no raw hh:mm" (i.e. "Got no raw 19:04")
   
   ![xDrip+ PhoneServiceState](../images/xDrip_Dexcom_PhoneServiceState.png)

* Start sensor (only if replacing)
   
   -> Near the bottom of the screen `Warm Up x,x hours left` must be displayed after a few minutes.

-> If your transmitter serial no. does not start with 8G, 8H or 8J and there is no time specification after a few minutes stop and restart the sensor.

* Restart collector (system status - if not replacing sensor}
* Do not turn original Dexcom receiver (if used) back on before xDrip+ shows first readings.
* Long press the red xDrip+ blood drop icon on the main screen to disable the `Source Wizard Button`.
   
   ![xDrip+ Dexcom Transmitter 1](../images/xDrip_Dexcom_Transmitter01.png)
   
   ![xDrip+ Dexcom Transmitter 2](../images/xDrip_Dexcom_Transmitter02.png)
   
   ![xDrip+ Dexcom Transmitter 3](../images/xDrip_Dexcom_Transmitter03.png)
   
   ![xDrip+ Dexcom Transmitter 4](../images/xDrip_Dexcom_Transmitter04.png)

### Κατάσταση μπαταρίας πομπού

* Battery status can be controlled in system status (Hamburger menu top left on homescreen)
* Swipe left once to see second screen. ![xDrip+ First Transmitter 4](../images/xDrip_Dexcom_Battery.png)

* The exact values when the transmitter “dies” due to empty battery are not known. The following information was posted online after the transmitter “died”:
   
   * Posting 1: Transmitter days: 151 / Voltage A: 297 / Voltage B: 260 / Resistance: 2391
   * Posting 2: Transmitter days: 249 / Voltage A: 275 (at time of failure)

### Επέκταση της διάρκειας ζωής του πομπού

* So far life cannot be extended for transmitters who's serial no. starts with 8G, 8H or 8J. Same is true for transmitters with serial no. starting with 81 and firmware 1.6.5.**27** (see xDrip+ System Status - G5/G6 status as shown in [screenshot above](../Configuration/xdrip#transmitter-battery-status)).
* To prevent difficulties starting sensors it is highly recommended to extend transmitter life before day 100 of first usage.
* Use of transmitters serial no. starting with 81 and firmware 1.6.5.**27** beyond day 100 is only possible if [engineering mode](../Usage/Enabling-Engineering-Mode-in-xDrip) is turned on and 'native mode' is deactivated (hamburger menu -> settings -> G5/G6 debug settings -> native algorithm) because a transmitter hard reset is NOT possible.
* Running sensor session will be stopped when extending transmitter life. So, extend before sensor change or be aware that there will be a new 2 h warm-up phase.
* Stop sensor manually via hamburger menu.
* Switch to the `engineering mode`: 
   * tap on the character on the right of the xDrip+ start screen that represents a syringe
   * then tap on the microphone icon in the lower right corner
   * In the text box that opens type "enable engineering mode" 
   * click "Done"
   * If Google Speak engine is enabled, you can also speak the voice command: "enable engineering mode". 
* Go to the G5 debug settings and make sure `Use the OB1 collector` is enabled.
* Use the voice command: “hard reset transmitter”
* The voice command will be executed with the next data receipt of the transmitter
* Look at the system status (Hamburger menu -> system status) and see what happens
* After approx. 10 min. you can switch to 'Classic Status Page' (swipe right) and click 'Restart collector'. This will set sensor days to 0 without the need to start a new sensor.
* Alternative: If you see a message "Phone Service State: Hard Reset maybe failed" on second system status screen just start the sensor and this message should go away.
   
   ![xDrip+ Hard Reset maybe failed](../images/xDrip_HardResetMaybeFailed.png)

* Transmitter days will be set to 0 after successful extension and start of sensor.

### Αντικατάσταση πομπού

Για τους πομπούς G6 που κατασκευάστηκαν μετά το πέρας / τέλος του 2018 (δηλ. με σειριακό αριθμό. starting with 80 or 81) you can use the [master](https://jamorham.github.io/#xdrip-plus).

Εάν ο σειριακός αριθμός του πομπού Dexcom G6. is starting with 8G, 8H or 8Juse one of the [latest nightly builds](https://github.com/NightscoutFoundation/xDrip/releases).

* Turn original Dexcom receiver off (if used).
* Stop sensor (only if replacing sensor)
   
   Ensure it really is stopped:
   
   On the second "G5/G6 Status" screen look at `Queue Items` about halfway down - It may say something like `(1) Stop Sensor`
   
   Wait until this goes - usually within a few minutes. Sensor Status must be "Stopped" (see screenshot).
   
   -> To remove transmitter without stopping sensor see this video <https://youtu.be/AAhBVsc6NZo>.
   
   ![xDrip+ Stop Dexcom Sensor 1](../images/xDrip_Dexcom_StopSensor.png)
   
   ![xDrip+ Stop Dexcom Sensor 2](../images/xDrip_Dexcom_StopSensor2.png)

* Forget device in xDrip+ system status AND in smartphone’s BT settings (Will be shown as Dexcom?? whereas ?? are the last two digits of the transmitter serial no.)
   
   ![xDrip+ Forget Device](../images/xDrip_Dexcom_ForgetDevice.png)

* Remove transmitter (and sensor if replacing sensor)

* Put the old transmitter far away to prevent reconnection. A microwave is a perfect Faraday shield for this - but unplug power cord to be 100% no one is turning the microwave on.
* Long press the red xDrip+ blood drop icon on the main screen to enable the `Source Wizard Button`.
* Use the Source Wizard Button which ensures default settings including OB1 & Native Mode 
   * This guides you through the initial set up.
   * You will need your transmitter serial number if this is the first time you've used it.
* Put in serial number of new transmitter. Be careful not to confuse 0 (zero) and O (capital letter o).
* Insert new sensor (only if replacing).
* Put transmitter into sensor - **Do not start sensor immediately!**
* New "Firefly Transmitters" (serial no. starting with 8G, 8H or 8J) can only be used in native mode.
* The following options must not be activated for new "Firefly Transmitters" (serial no. starting with 8G, 8H or 8J):
   
   * Preemptive Restart (disable!)
   * Restart sensor (disable!)
   * Fallback to xDrip+ (disable!)
   
   ![Settings for Firefly transmitters](../images/xDrip_Dexcom_FireflySettings.png)

* Check in Classic Status Page -> G5/G6 status -> PhoneServiceState if one of the following information is displayed:
   
   * Transmitter serial starting with 80 or 81: "Got data hh:mm" (i.e. "Got data 19:04")
   * Transmitter serial starting with 8G, 8H or 8J: "Got glucose hh:mm" (i.e. "Got glucose 19:04") or "Got no raw hh:mm" (i.e. "Got now raw 19:04")
   
   ![xDrip+ PhoneServiceState](../images/xDrip_Dexcom_PhoneServiceState.png)

* Wait 15 minutes as the transmitter should communicate several times with xDrip before new sensor is started. Battery data will be shown below Firmware information.
   
   ![Firefly transmitter battery data](../images/xDrip_Dexcom_FireflyBattery.png)

* Start sensor and DO NOT BACKDATE! Always select "Yes, today"!

* Restart collector (system status - if not replacing sensor)
* Do not turn original Dexcom receiver (if used) back on before xDrip+ shows first readings.
* Long press the red xDrip+ blood drop icon on the main screen to disable the `Source Wizard Button`.
   
   ![xDrip+ Dexcom Transmitter 1](../images/xDrip_Dexcom_Transmitter01.png)
   
   ![xDrip+ Dexcom Transmitter 2](../images/xDrip_Dexcom_Transmitter02.png)
   
   ![xDrip+ Dexcom Transmitter 3](../images/xDrip_Dexcom_Transmitter03.png)
   
   ![xDrip+ Dexcom Transmitter 4](../images/xDrip_Dexcom_Transmitter04.png)

### Νέος αισθητήρας

* Turn original Dexcom receiver off (if used).
* Stop sensor if necessary
   
   Ensure it really is stopped:
   
   On the second "G5/G6 Status" screen look at `Queue Items` about halfway down - It may say something like `(1) Stop Sensor`
   
   Wait until this goes - usually within a few minutes.
   
   ![xDrip+ Stop Dexcom Sensor 1](../images/xDrip_Dexcom_StopSensor.png)
   
   ![xDrip+ Stop Dexcom Sensor 2](../images/xDrip_Dexcom_StopSensor2.png)

* Clean contacts (transmitter backside) with alcohol and let air-dry.

* In case you use this function disable `Restart Sensor` and `Preemptive restarts` (Hamburger menu -> Settings -> G5/G6 Debug Settings). If you miss this step and have these functions enabled the new sensor will not start properly.
   
   ![xDrip+ Preemptive Restart](../images/xDrip_Dexcom_Restart.png)

* Start Sensor
   
   **For new Firefly transmitters** (serial no. starting with 8G, 8H or 8J) **it is mandatory, for all other transmitters it is recommended to wait approx. 15 minutes between stopping and starting the new sensor (until `Sensor Status: Stopped` is shown on second system status screen). DO NOT BACKDATE!**

* Set time inserted
   
   * To use G6 Native mode you must wait for the 2 hour warm up (i.e insertion time is now).
   * If you are using the xDrip+ algorithm then you can set a time more than 2 hours ago to avoid warm up. Readings may be very erratic. Therefore, this is not recommended.
* Enter Sensor code (on the peel-off foil of the sensor) 
   * Keep code for further reference (i.e. new start after transmitter had to be removed)
   * Code can also be found in [xDrip+ logs](../Configuration/xdrip#retrieve-sensor-code): Click 3-dots-menu on xDrip+ homescreen and choose `View Event Logs`.
* No calibration is needed if you use G6 in "native mode". xDrip+ will show readings automatically after 2 hour warm-up.
* Do not turn original Dexcom Receiver (if used) back on before xDrip+ shows first readings.
   
   ![xDrip+ Start Dexcom Sensor 1](../images/xDrip_Dexcom_SensorStart01.png)
   
   ![xDrip+ Start Dexcom Sensor 2](../images/xDrip_Dexcom_SensorStart02.png)

### Ανάκτηση κώδικα αισθητήρα

* In master dated 2019/05/18 and the latest nightly builds the sensor code is shown in system status (Hamburger menu top left on homescreen).
* Swipe left once to see second screen.
   
   ![xDrip+ Retrieve Dexcom Sensor Code2](../images/xDrip_Dexcom_SensorCode2.png)

* Dexcom sensor code can also be found in xDrip+ logs.

* Tap 3 dot menu (top right side on homescreen)
* Select `View Event Logs` and search for "code"
   
   ![xDrip+ Retrieve Dexcom Sensor Code](../images/xDrip_Dexcom_SensorCode.png)

## Αντιμετώπιση προβλημάτων Dexcom G5/G6 και xDrip+

### Πρόβλημα στη σύνδεση πομπού

* Transmitter must be shown in your smartphone's bluetooth settings.
* Transmitter will be shown as Dexcom?? whereas ?? represent the last two digits of your transmitter serial no. (i.e. DexcomHY).
* Open system status in xDrip+ (hamburger menu on top left side of home screen).
* Check if your transmitter is shown on first status page ('classic status page').
* If not: Delete device from your smartphone's bluetooth settings and restart collector.
* Wait about 5 min. until Dexcom transmitter reconnects automatically.

### Πρόβλημα κατά την εκκίνηση νέων αισθητήρων

Please note that the following method might likely not work if your Dexcom G6 transmitter's serial no. is starting with 8G, 8H or 8J.

* Native sensor is marked as "FAILED: Sensor Failed Start"
* Σταματήστε τον αισθητήρα
* Restart your phone
* Start sensor with code 0000 (four times zero)
* Wait 15 minutes
* Σταματήστε τον αισθητήρα
* Start sensor with "real" code (printed on the adhesive protector)

Check in xDrip+ logs if xDrip+ starts counting "Duration: 1 minute" (and so on). Only in the xDrip+ logs you can detect at an early stage whether xdrip+ has stopped a sensor. Latest status is not always shown correctly on bottom of startscreen.

## xDrip+ & Freestyle Libre

### Libre συγκεκριμένες ρυθμίσεις

* Open Bluetooth Settings -> Hamburger Menu (top left of homescreen) -> Settings -> scroll down -> Less common settings -> Bluetooth Settings
   
   ![xDrip+ Libre Bluetooth Settings 1](../images/xDrip_Libre_BTSettings1.png)

* Enable the following settings
   
   * `Turn Bluetooth on` 
   * `Use scanning`
   * `Always discover services`

* All other options should be disabled
   
   ![xDrip+ Libre Bluetooth Settings 2](../images/xDrip_Libre_BTSettings2.png)

### Libre smart reader battery level

* Battery level of smart readers such as MiaoMiao 2 can be displayed in AAPS.
* Details can be found on [screenshots page](../Getting-Started/Screenshots#sensor-level-battery).

### Connect Libre Transmitter & start sensor

![xDrip+ Start Libre Transmitter & Sensor 1](../images/xDrip_Libre_Transmitter01.png)

![xDrip+ Start Libre Transmitter & Sensor 2](../images/xDrip_Libre_Transmitter02.png)

![xDrip+ Start Libre Transmitter & Sensor 3](../images/xDrip_Libre_Transmitter03.png)