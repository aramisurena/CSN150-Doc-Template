# Cybersecurity : CSN150
Project: ESP32 XXXXXXXX

## Purpose
Set up ESP32 and Arduino enviornment. Execute sketch " Wifiscanner". 

## Equipment
* [ESP32Cam](https://www.amazon.com/Aideepen-ESP32-CAM-Bluetooth-ESP32-CAM-MB-Arduino/dp/B08P2578LV/ref=sr_1_3?crid=4FY0ECFW0ZX7&keywords=ESP32+Cam&qid=1678902050&sprefix=esp32+cam%2Caps%2C240&sr=8-3)

* [USB Micro Data Cable](https://www.amazon.com/AmazonBasics-Male-Micro-Cable-Black/dp/B0711PVX6Z/ref=sr_1_1_sspa?keywords=micro+usb+data+cable&qid=1678902214&sprefix=Micro+USB+data+%2Caps%2C89&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFaU0NaUVZHU1RFUlAmZW5jcnlwdGVkSWQ9QTA3NTA4MDVFVERCS01HVlgxM1YmZW5jcnlwdGVkQWRJZD1BMDE4NTE1NTIwWUdONkdWSzU1M1Amd2lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl)

## Links to documentation and tools

##### Video 1: https://www.youtube.com/watch?v=I22uHf97EG4

##### Video 2: https://www.youtube.com/watch?v=HQBtwz5EBZM

##### AI GPTs used: none

## Steps I followed
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
   

## Problems and Solutions
At first I was unable to locate the Esp32 board even after installing the CH340 driver. This was solved by rebooting Arduino. I did not use google or any online resourse to solve this, just common trouble shooting procedure.  


### Example Problem
**Problem:** Arduino code will not load on ESP32 Cam.
**Solution:** Camera drivers were incorrect I needed to install the driver: [https://www.wch-ic.com/downloads/CH341SER_ZIP.html](https://github.com/martin-ger/esp32_nat_router).  I used file, "CH341SER.ZIP" and it worked.

## Final Report

I was successful in setting up the Blink script on my ESP32-Cam without much trouble. 
