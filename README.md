# 4SC3-Project

# Making a LoRa Gateway for Parking Lot Monitoring

Parking System Model



To simulate the ultrasonic sensor we ordered, a CubeCell board was paired with an ultrasonic distance sensor. This allows the sensor readings to be transmitted using the LoRa communication method. An image of the module and its wiring diagram are shown in the images folder of this repository. The code for these nodes are LoRaUltrasonic.ino and LoRaUltrasonic2.ino. Information on how to upload code to the CubeCell using the Arduino IDE can be found using this link: https://docs.heltec.org/en/node/cubecell/quick_start.html#use-arduino-board-manager

A gateway was then created by pairing the remaining CubeCell with an ESP32 Development board, which was connected to the internet using the Arduino Cloud IoT platform. This CubeCell receives and decodes the LoRa messages sent by the ultrasonic sensor modules and digitally transmits this information to the ESP32. The ESP32 then sends these values to the cloud, where they can be viewed by anyone. An image of the module and its wiring diagram are shown in the images folder of this repository. The code for the CubeCell module is LoRaGateway.ino and code for the ESP32 from the Arduino Cloud is called ESP32_Cloud. Information about connecting an ESP32 to the Arduino Cloud can be found using this link: https://docs.arduino.cc/arduino-cloud/getting-started/esp-32-cloud

The implementation of this communication is very simple. Each ultrasonic sensor node transmits a message when the sensor detects an object within its range. This message is in the form of only two numbers. The first number transmitted is the number of the node. This allows the network to be scalable. The second number is the binary status of the node, with 0 meaning no object detected and 1 meaning an object is within range. For example, if the first node did not detect an object, it would transmit the message “10”.

The Arduino Cloud implementation is also quite simple. The ESP32 reads digital values from the receiver CubeCell and sends these values to the cloud, where they can be visually displayed.
 
