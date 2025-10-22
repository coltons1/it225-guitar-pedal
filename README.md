# IT 225 Project Report

# Objective
This project was introduced to us at the start of the semester to make a project of our own idea using the Freenove ESP-32 Wrover Ultimate Starter Kit. 
<img width="347" height="503" alt="image" src="https://github.com/user-attachments/assets/0a36de24-c4fe-4494-85ca-f66990df3db2" />
Over discussions we came up with the idea of creating a clean boost guitar pedal using different sensors to manipulate the settings of the pedal. A clean boost guitar pedal amplifies the sound of the guitar more. The original idea to construct a guitar pedal stemmed from our deconstruction of this Behringer Chorus guitar pedal. We were interested in the components and did research to find a way to build a simpler pedal. 
# Initial Planning

Our project proposal we initially submitted discussed using the ESP-32 Wrover board’s camera to detect light levels (i.e., if the camera is covered by a hand, it would be darker). We also investigated using Google’s Teachable Machine using its image model to detect basic hand gestures. Additionally, we were suggested to look at a digital potentiometer, the MCP41100, however it ended up not serving the purpose of our project. After further discussion we decided on an initial plan.
Our initial planned features included:
•	A clean boost guitar pedal operated by a potentiometer and a switch.
•	An infrared motion sensor to turn the pedal on and off. 
•	A standard potentiometer to physically adjust the boost level. 
•	A variable speed kill switch function that would adjust how frequently the signal is cut based on values from a photoresistor.
In our preliminary research before starting the project we found some schematics for building a basic breadboard clean boost pedal from online creator, Barbarach1.

<img width="661" height="404" alt="image" src="https://github.com/user-attachments/assets/f0513461-9350-4829-a979-01c9af6fb50f" />

________________________________________
1.	https://barbarach.com/articles/building-a-simple-pedal/lets-build-a-simple-pedal/
 
# Building Process

The first objective we completed was building the main clean boost circuit first. Following the video and tutorial allowed us to work that section of the project out in one to two meetings. However, from this point we needed to start setting up our sensors such as our photoresistor. 

<img width="414" height="441" alt="image" src="https://github.com/user-attachments/assets/03014632-ff9b-4005-803e-b309bf8590d0" />

The photo on the left is of our breadboard with the circuit for the clean boost effect pedal along with a testing circuit for the photoresistor using the LED. The image on the right shows a schematic of only the clean boost effect pedal. Focusing on the left photo we were testing the photoresistor by adjusting the LED’s brightness based on the amount of light the photoresistor was detecting. Example code will be inserted below.

This code for our photoresistor allowed us to read out the value of how much light the sensor was receiving. With this information and testing code we were able to interface the photoresistor with our potentiometer and the motor we attached to it. With Dr. Rashid’s assistance we attached our potentiometer to our servo motor which will be included in the photo below. 

<img width="333" height="335" alt="image" src="https://github.com/user-attachments/assets/3191c4ac-352c-4d1c-b13e-9db1e1d00a1b" />

 
# Our Main Hurdles
One major problem that we encountered was due to a big error of ours. One group member investigated using an alternative power source rather than the USB cable through the ESP board. We attempted to use a 9V adapter plugged into the board, it was plugged in for a few seconds before the ‘magic smoke’ escaped the board. After consulting with the professor, we found out that a part of the breakout board had been burnt. We continued to test our ESP-32 chip, however it did not work. It still functioned to provide power to the board. 
	Another large problem we faced dealt with the original planned features. We intended to use the infrared motion sensor as a power switch for the pedal itself. The component seemed to work however whenever we tested it, it only output HIGH (detected motion). After more research into the piece we found that there was a delay timer on the component that was standardly set to about 3 minutes. After further testing it, we figured it was not the best component to use and scrapped the idea.
 
# Final Product
<img width="542" height="610" alt="image" src="https://github.com/user-attachments/assets/2ba97486-dee1-430a-927a-12a0d2aa5a82" />

Our final product ended up like the breadboards above. A standard clean boost effect pedal with the volume boost potentiometer that changed values based off how a servo motor rotates the attach potentiometer. The servo motor’s rotation was connected to how much light a photoresistor was detecting. Standardly, the photoresistor had an LDR value of 4096. This acted as our higher threshold, this was the maximum value and thus maximum rotation for the motor and potentiometer. At the value 4096, the boost effect was at its loudest. Our lower threshold, when the photoresistor detected very little light, around an LDR value of 2000, the motor was set to rotate in the opposite direction, making the effect quieter. Our final code is included on the next page. One issue that we still have due to the medium of the project is an occasional pop in the sound due to the unsecure connection caused by the servomotor rotating the potentiometer. 
