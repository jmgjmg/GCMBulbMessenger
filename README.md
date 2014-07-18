GCMBulbMessenger
================

Client to remotely control a Yeelight Blu light bulb controlled with GCMHelloWorld (https://github.com/jmgjmg/GCMHelloWorld)
It includes one activity:

- ControlLightActivity: used to define the light configuration (color and intensity) and to generate push notifications (GCM) accordingly. 


For security resasons, GCM key values are stored in a file in the src directory (Constant.java). The original file
is removed from the github repository, however a dummy Constant.java.txt file is available. Rename it to Constant.java and update its content with the right values obtained when creating the application in the Google Developers Console.

The configuration of the light bulb is updated by sending a JSON message over http POST to Google GCM server. This is done from the "Send" button.

Example (replace values of API-key XXXXXXXXXXXXXX and registration-id YYYYYYYYY with your own values)

```
POST https://android.googleapis.com/gcm/send HTTP/1.1
Authorization: key=XXXXXXXXXXXXXX
Content-Type: application/json
Host: android.googleapis.com
Content-Length: 272

{"data":{"Intensity":100,"Color":{"Blue":0,"Green":0,"Red":255}},"registration_ids":["YYYYYYYYY"]}

```

Intensity value is an integer between 0 and 100.

Red, Green and Blue values are integers between 0 and 255.

For more information about the format of this message, please read Google's documentation: 
https://developer.android.com/google/gcm/http.html

#### Further information
- Basic GCM tutorial (I have followed it to create the Google project with GCM API and my GCMHelloWorld Android app) http://hmkcode.com/android-google-cloud-messaging-tutorial/
- Yeelight Blue bulbs: http://www.yeelight.com/en_US/info/download
- More info on Bluetooth Low Energy, Android and Yeelight: http://wiki.makespacemadrid.org/index.php?title=Bombilla_LED_de_colores_con_Bluetooth_Low_Energy
- Home page of GCM: https://developer.android.com/google/gcm/index.html
