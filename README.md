# Cybersecurity : CSN150
Project: ESP32 XXXXXXXX

## Purpose
Set up ESP32 and Arduino enviornment. Execute sketch " Wifiscanner". 
Set up ESP32 Cam Live Stream
Set up ESP32 Access Point Web Server

## Equipment
* [ESP32Cam](https://www.amazon.com/Aideepen-ESP32-CAM-Bluetooth-ESP32-CAM-MB-Arduino/dp/B08P2578LV/ref=sr_1_3?crid=4FY0ECFW0ZX7&keywords=ESP32+Cam&qid=1678902050&sprefix=esp32+cam%2Caps%2C240&sr=8-3)

* [USB Micro Data Cable](https://www.amazon.com/AmazonBasics-Male-Micro-Cable-Black/dp/B0711PVX6Z/ref=sr_1_1_sspa?keywords=micro+usb+data+cable&qid=1678902214&sprefix=Micro+USB+data+%2Caps%2C89&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFaU0NaUVZHU1RFUlAmZW5jcnlwdGVkSWQ9QTA3NTA4MDVFVERCS01HVlgxM1YmZW5jcnlwdGVkQWRJZD1BMDE4NTE1NTIwWUdONkdWSzU1M1Amd2lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl)

## Links to documentation and tools

##### Video 1: https://www.youtube.com/watch?v=I22uHf97EG4

##### Video 2: https://www.youtube.com/watch?v=HQBtwz5EBZM

##### Video 3: https://www.youtube.com/watch?v=4inE-n6kXSE

##### Guide: https://lastminuteengineers.com/getting-started-with-esp32-cam/#esp32cam-example-2-live-video-streaming-server

##### Guide 2: https://randomnerdtutorials.com/esp32-cam-access-point-ap-web-server/

##### AI GPTs used: GPT-5.3 model

## Steps I followed (Set + Blink Sketch)
1. Installed Arduino from their webpage: https://www.arduino.cc/en/software/
2. Connected ESP32Cam to USB port
3. Installed the driver for CH340 from: https://www.wch-ic.com/downloads/CH341SER_ZIP.html
4. Uploaded espressif's github package in link in Arduino's preferences (located under files)
5. In Arduino -> Boards Manager -> installed esp32 by espressif
6. Selected AI THINKER ESP32-CAM from drop down box in Arduino
7. In Arduino -> Files -> Examples -> Basics -> Blink
8. Updated script to Output 4
9. Changed time from 1000ms to 10000ms
10. Uploaded script and verified success

## Steps I followed (Live Stream Cam)
1. In Arduino -> Files -> ESP32 -> Camera -> CameraWebServer
2. From CameraWebServer.ino -> updated my ssid and password
3. from board_config.h -> removed // from #define CAMERA_MODEL_AI-THINKER to specify camera
4. Commented out other camera models by adding // at the begining of their line
5. Uploaded Sketch
6. Accessed video streaming server by Tools -> Serial Monitor -> Setting baud rate to 115200
7. Opened http link provided in Output
8. CLicked "Start Stream" to verify camera is on.

## Steps I followed (Access Point)
1. In Arduino -> Files -> Examples -> ESP32 -> Camera -> CameraWebserver.
2. From CameraWebServer.ino -> updated the ssid to Aramis U Accesspoint and password to 12345678Au
3. Removed lines:
  
   WiFi.begin(ssid, password);
while (WiFi.status() != WL_CONNECTED) {
  delay(500);
  Serial.print(".");
}
Serial.println("");
Serial.println("WiFi connected");

4. Added the following line under setup(): WiFi.softAP(ssid, password);
5. Changed Serial.print(WiFi.localIP()); to Serial.print(WiFi.softAPIP());
6. Replaced: WiFi.setSleep(false);

Serial.print("WiFi connecting");
Wifi.softAP(ssid, password);

startCameraServer();

Serial.print("Camera Ready! Use 'http://");
Serial.print(WiFi.localIP());
Serial.println("' to connect");

WITH: WiFi.setSleep(false);

Serial.println("Setting up Access Point...");
WiFi.softAP(ssid, password);

startCameraServer();

Serial.print("Camera Ready! Connect to WiFi network: ");
Serial.println(ssid);

Serial.print("Then go to: http://");
Serial.print(WiFi.softAPIP());
Serial.println("/");
7. In board_config.h -> removed // from #define CAMERA_MODEL_AI-THINKER to specify camera
8. Verified and uploaded sketch
9. Hard reset ESP32-CAM
10. Connected to Aramis U Access Point via iPhone and accessed ESP32-CAM through 192.168.4.1 in Safari
   

## Problems and Solutions
At first I was unable to locate the Esp32 board even after installing the CH340 driver. This was solved by rebooting Arduino. I did not use google or any online resourse to solve this, just common trouble shooting procedure.  

No issues while setting up camera

While setting up the access point I came across several hiccups. First was that I received E(44): Camera Detected not supported. This was sovled by going to board_config.h and defining the correct camera. The second was after verifiying and successfully uploading the sketch, I could not find the access point. I hard reset the ESP32-CAM and was able locate and connect.


### Example Problem
**Problem:** Arduino code will not load on ESP32 Cam.
**Solution:** Camera drivers were incorrect I needed to install the driver: [https://www.wch-ic.com/downloads/CH341SER_ZIP.html](https://github.com/martin-ger/esp32_nat_router).  I used file, "CH341SER.ZIP" and it worked.

## Final Report

I was successful in setting up the Blink script on my ESP32-Cam without much trouble. 
I was able to successfully set up a live stream with the ESP32.
I was able to successfully set up an Access Point using Arduino and the ESP32
