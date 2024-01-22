## Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU

# Introduction 
If you have a pet in your home and you don’t have anyone to feed it when you are away from home then you need some kind of machine to do this job. So here we are building an IoT Pet Feeder machine that is simple, efficient, and cost-effective. Using this machine you can feed your Pet by Google Assistant from anywhere in the world. You just have to say "Okay Google. Feed my pet" and the rest of the things will be done by this machine. You can also set a specific time using Google Assistant to feed your Pet. For example, Say "Okay Google. Feed my pet Today Morning" and it will feed your pet at the previously specified time. Like this, you can also set a specific time for noon and evening.
In this project, we are using a NodeMCU ESP8266 as the main controller, a Servo motor to open & close the feeding bottle, and a 16*2 LCD to display the time. We will get the time from the NTP servers. Instead of using the RTC module for Time and Date, here we used the NTP server to reduce the hardware components. NTP servers are a better solution for getting time compared to RTC as it is more accurate and can provide the time of any geographical area in the world.

# Components Required 
<br>1. NodeMCU ESP8266
<br>2. 16x2 LCD Module
<br>3. LCD I2C Module
<br>4. Servo Motor

# Circuit Diagram 
<br>1. The circuit diagram for this IoT-based Pet Feeder project is given below. In this circuit diagram, a servo motor and LCD module are connected with NodeMCU ESP8266.
![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/2894137f-34ab-46ee-905f-3794f78b6c9b)

<br>2. The Vcc & GND pin of the Servo motor and LCD I2C module are connected with the Vin & GND pin of NodeMCU. While the SCL and SDA pins of the I2C module are connected with the D1 and D2 pins of NodeMCU respectively.
![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/502cda76-1479-49a3-9df5-de57da7b51ac)

<br>3. Here we have used a plastic bottle for the pet food container:
![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/b39fb7c6-0cf1-4d07-97b9-48995244ae1e)

# Adafruit IO Setup for IoT Pet Feeder
Adafruit IO is an open data platform that allows you to aggregate, visualize, and analyze live data on the cloud. Using Adafruit IO, you can upload, display, and monitor your data over the internet, and make your project IoT-enabled. You can control motors, read sensor data, and make cool IoT applications over the internet using Adafruit IO. For testing and trying, with some limitations, Adafruit IO is free to use. We have also used Adafruit IO with Raspberry Pi previously.
<br>1. For Adafruit IO setup, the first thing you will need to do is to sign up for Adafruit IO. To sign up go to Adafruit IO’s site https://io.adafruit.com and click on ‘Get started for Free’ on the top right of the screen.<br>
![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/f8620b07-359e-4045-adcf-f35d8fa3b8d6)

<br>2.  After this, a window will pop up where you need to fill your details.
![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/6798589b-7b38-4871-9cdd-6e1a1bcbfa81)

In sign up window fill your details like your name, mail id, username, etc. Then click on save settings, and your account is created. To get your AIO key click on ‘View AIO Key.’
![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/c3c47a33-a08d-4087-ac98-3c7a26a70c70)

<br>3.  A window will pop up with your Adafruit IO AIO Key. Copy this key you'll need it later in your code.
![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/1a3db4ef-69ff-46ad-b917-b5bf70fcbb85)

<br>4. Now, after this, you need to create a feed. To create a feed click on ‘Feed.’ Then click on ‘Actions,’ you will see some options from them click on ‘Create a New Feed.’
![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/0b5b3fa3-7108-42ca-953d-6f67600d5ff6)

<br>5. After this a new window will open where you need to input:

**Name** – In name, option write a short descriptive name of your feed. You can use

Letters, numbers, and spaces.

**Description** - A long-form description of your data. This field is not required, but you    

can write a description of your data.

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/1a3024c1-4709-49af-a134-f31cfb8b7c3f)

<br>6. Click on ‘Create,’ you will then be redirected to your new feed.

# IFTTT Setup for IoT Pet Feeder
IFTTT also known as, **‘If This Then That’** is a free web-based service to create chains of simple conditional statements, called applets. IFTTT allows users to create triggers and execute actions based on the triggers.
<br>1. In this IoT cat feeder project, we are using IFTTT to create a trigger when we say a specific line using Google Assistant. For that we have to create an applet in which we will integrate the Google Assistant with Adafruit IO. We previously used Google assistant to build IoT projects.
First of all, we created an account on IFTTT. To do so we navigated to IFTTT website and click on signup. Then filled out the required details and clicked on create an account.
Now, as we are signed in to your account,we click on "my profile" and then click on ‘Create.’>

NOTE: Sign in to IFTTT using the same Email ID as used in your Android phone’s Google account. For example, if your phone is signed using the xyz@gmail.com Email ID, then sign in to IFTTT using the same Email ID.

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/59d337e2-6332-49a5-87ae-86b7ae3e07e2)

<br>2. Now create an applet using If ‘This’ Than ‘That.’ Here ‘This’ is the service name by which we will give input and ‘That’ will generate trigger according to input. So in this project we will use Google Assistant as ‘This’ and Adafruit IO as ‘That.’
So to create an applet, click on the ‘This’ icon. And search for ‘Google Assistant.’ Here IFTTT will ask for permission for using your Google account.

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/9773c54f-2f84-49f8-ac7b-e0b9c0cfe947)

<br>3. Now in Google Assistant click on ‘Say a simple phrase.’

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/a39d3a5c-a059-4d31-85d8-f4662d26aa41)

<br>4. Now in the next window, it will ask you about the phrase that you want to say your Google Assistant and what you want to hear in response to that phrase. You can also add some optional phrases. Now click on Create Trigger.

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/c7269b1a-8045-46d3-8548-b61066678d21)

<br>5. Now one part of this applet is complete. For the second part click on the ‘That.’

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/7858440f-4cc8-4c80-8b67-3830409b9973)

<br>6. Now in the search window, search for ‘Adafruit’.

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/ab555dcd-939d-4823-b6c1-7add46615501)

<br>7. In the next window choose the feed name for which you want to create trigger and then enter the word/Data that you want to send to the feed when you say your specified phrase. After that click on ‘Create Action.’ After this it will ask you to finish the setup by clicking on the finish button. Now your applet is ready to use.

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/7310782e-3987-48d4-bc92-d7e50581efe1)

<br>8. This applet was to feed the pet when we say a phrase to Google Assistant.

Now we will create another applet by which we can feed our pet at a specific time by saying a phrase with the text, for example, “Ok Google Feed My Pet Today Morning.” By using this applet we can send a trigger to ESP8266 at a specific time. For this applet follow the same steps: click on profile and then ‘Create.’ After that in ‘This’ option choose ‘Google assistant’. Now in google assistant click on ‘Say phrase with a Text ingredient’.

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/64c448f9-10ea-4b40-866c-ba6779de50b8)

<br>9. In the next window click on ‘That’ and choose Adafruit. In Adafruit select the same feed name as previous applet. Then click on ‘Create action’ and ‘Finish’ to finish the process

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/80069460-cc97-4752-b4f2-b77cacfeb661)

# Code

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/572fe860-fb02-4262-a6ad-99c4d18a829b)
(Screenshot of Arduino IDE)

# Code Explanation 

Begin the code by including all the required libraries for this project. Arduino IDE has pre-installed libraries for servo motor and LCD module. But you have to download and install the rest of the libraries such as: Adafruit MQTT, NTP Client, Wire.h. 

**<br>#include <ESP8266WiFi.h>
<br>#include "Adafruit_MQTT.h"
<br>#include "Adafruit_MQTT_Client.h"
<br>#include<Servo.h>
<br>#include <NTPClient.h>
<br>#include <WiFiUdp.h>
<br>#include <LiquidCrystal_I2C.h>
<br>#include <Wire.h>**
 

To get accurate time from NTP server initialize the server location. Here I am using “pool.ntp.org” which is a pool of worldwide servers.

**<br>WiFiUDP ntpUDP;
<br>NTPClient timeClient(ntpUDP, "pool.ntp.org", 19800,60000);**

Here in this part of code, we are defining the Adafruit server address, port number, Adafruit account username and unique AIO key that you copied from your Adafruit account. This is used to establish the MQTT connection between ESP and Adafruit IO.

**<br>#define MQTT_SERV "io.adafruit.com"
<br>#define MQTT_PORT 1883
<br>#define MQTT_NAME "Username"
<br>#define MQTT_PASS "AIO Key"**

In this part of code, set up the MQTT and WiFi clients using previous information, i.e. adafruit username, AIO key, server address, and port no.

**<br>WiFiClient client;
<br>Adafruit_MQTT_Client mqtt(&client, MQTT_SERV, MQTT_PORT, MQTT_NAME, MQTT_PASS);**
 

Now here we set up the feed with a name “onoff” and subscribing to it.

**Adafruit_MQTT_Subscribe onoff = Adafruit_MQTT_Subscribe(&mqtt, MQTT_NAME "/f/onoff");**
 

timeClient.begin(); function is used to start the NTP client so the it can send data to ESP8266.

**timeClient.begin();**
 

Inside the void loop, timeClient.update() function is used to update the date and time whenever we request to NTP servers. After getting the data, we store the hour, minute and second in three different integers. 

**<br>timeClient.update();
<br>hh = timeClient.getHours();
<brmm = timeClient.getMinutes();
<br>ss = timeClient.getSeconds();**
 

Here we are directly checking for a specific word in our subscribed feed and if the word matches with our specified word, i.e. ‘ON’ it will call the open_door() and close_door() function.
The loop is shown below : 
   _<br>if (!strcmp((char*) onoff.lastread, "ON"))
      <br>{
        <br>open_door();
        <br>delay(1000);
        <br>close_door();
       <br>}_


By using the if condition assign a specific time to the “Morning”, “Afternoon” and “Evening” strings. After that use another if condition to match the current time and feed time. So whenever we say “Feed My Pet Today Morning” it will call the open_door() and close_door() function when the current time is equal to 10:30. It will follow the same procedure for “Evening” and “Afternoon” strings.

_<br>if (!strcmp((char*) onoff.lastread, "Morning"))
      <br>{
        <br>feed_hour = 10;
        <br>feed_minute = 30;
      <br>}
     <br>}
   <br>}
   <br>if( hh == feed_hour && mm == feed_minute &&feed==true) //Comparing the current time with the Alarm time
    <br>{
      <br>open_door();
      <br>delay(1000);
      <br>close_door();
      <br>feed= false;
      <br>}
<br>}_
 

void open_door() and void close_door() function are used to send the command to the servo motor to open the trap door. Open angle is defined as 60° while the close angle is defined as 0°.

**<br>void open_door(){
    <br>servo.write(OPEN_ANGLE)
<br>void close_door(){
    <br>servo.write(CLOSE_ANGLE);**

# Working of the IoT Pet Feeder
After uploading the code to the NodeMCU, the current time and Feed time will be displayed on the 16*2 LCD. Initially, it will show 0:0 in feed time as we didn’t enter any feed time. Now Say "Okay Google. Feed my pet" to your Google Assistant. Google Assistant will recognize the phrase and respond with "Feeding your pet." After that it rotates the servo motor from its initial position 0⁰ to 60⁰ and after a delay, it returns to its initial position. You can also feed your pet at a specific time. For that we have used three strings i.e., “Morning”, “Afternoon” and “Evening”. These strings are assigned with different times, so when you say “Feed My Pet Today Morning” it will take the time assigned to “Morning” string as feeding time and when the entered time matches with current time it rotates the servo motor from its initial position 0⁰ to 60⁰ and after a delay it returns to its initial position.

![image](https://github.com/PriyanshaNayak/Google-Assistant-controlled-IoT-based-Pet-Feeder-using-NodeMCU/assets/87187181/da5281e3-b573-458f-a558-1e49f2cd7cf3)

This is how you can feed your pet using Google Assistant. If you want to feed your pet at a specific time instead of morning, afternoon and evening, go to IFTTT and change the Google assistant settings from ‘Say a phrase with text ingredient’ to ‘Say a phrase with a number’.

