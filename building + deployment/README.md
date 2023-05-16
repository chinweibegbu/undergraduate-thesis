# Building & Deployment

This project uses [Edge Impulse](https://www.edgeimpulse.com/) and the Arduino IDE to help build this project and facilitate deployment. The `classifier_esp32cam_arduino.ino` file contains the end result of the process below and will *not* function on independent of following all the other steps involved. It is adviced to view this file as a guide rather than a source to directly deploy onto your device.

**NOTE:** This series of steps does *not* contain the inclusion of a switch which is done using a rocker switch with:
1. A GND terminal to connect the GND of the battery holder and the GND of the microcontroller
2. A voltage terminal to connect the voltage output of the battery holder
3. A accessory terminal to connect the 5V terminal of the microcontroller 

## Steps
1. Test the ESP32-CAM microcontroller
   * Connect the camera module to the ESP32-CAM
   * Connect the ESP32-CAM to the baseboard
   * Connect the baseboard to the laptop via a data-power cable
   * Open the Arduino IDE
   * Add the necessary links to the "Additional Board Manager URLs field" in `File > Preferences`:
     * https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
     * http://arduino.esp8266.com/stable/package_esp8266com_index.json
   * Download the ESP32 library in `Tools > Manage Libraries…` *(**NOTE:** See the full Arduino IDE ESP32 setup tutorial via this [link](https://randomnerdtutorials.com/getting-started-with-esp32/#esp32-upload-code))*
   * Restart the Arduino IDE
   * Open the CameraWebServer sketch in `File > Examples > ESP32 > Camera`
   * In the code, change the ssid (a.k.a. network name) and password in the code to that of your network *(**NOTE:** Make sure that you use a network which only requires a password such as a hotspot connection)*
   * Select the correct board (ESP32 AI Thinker) and port in the `Tools` menu
   * Click the "Upload" button
   * In the Arduino IDE, open the `Serial Monitor` tab by clicking on the icon in the top-right corner of the green bar
   * Select the port specified by the code in the dropdown
   * Once the microcontroller is assigned an IP address, copy it from the `Serial Monitor` tab and paste it in your browser, which should also be connected to the same network as the microcontroller
   * Click on the "Start Streaming" button to view what the microcontroller's camera module sees *(**NOTE:** See a full WiFi video streaming tutorial via this [link](https://randomnerdtutorials.com/esp32-cam-video-streaming-face-recognition-arduino-ide/))*
2. Supply power to the breadboard
   * Fill the AA battery holder with 4 batteries
   * Connect ground (black and -ve) and power supply (red and +ve) to the power rails of the breadboard
3. Upload the power supply test code
   * Connect the ESP32-CAM to the baseboard
   * Press the reset (RST) button on either the ESP32-CAM or the baseboard
   * Connect the baseboard to the laptop via a data-power cable
   * Open the Arduino IDE
   * Open the Blink sketch under `File > Examples > 01.Basics`
   * In the code, replace "LED_BUILTIN" with any unoccupied digital pin on the ESP32-CAM by utilising the terminal strips on either side of the microcontroller
   * Select the correct board (ESP32 AI Thinker) and port in the `Tools` menu
   * Click the "Upload" button
4. Connect the microcontroller to the breadboard
   * Disconnect ESP32-CAM from its baseboard
   * Place ESP32-CAM on the breadboard such that there is a track on each side to connect the pins
   * Connect pins for ground and power supply from the power rails to the ESP32-CAM via its adjacent 5V and ground (GND) pins on the left side of the microcontroller via the terminal strip on either side of the microcontroller *(**NOTE:** See a full ESP32-CAM breadboard connection tutorial via this [link](https://youtu.be/rRoOGV9fkfs))*
5. Test the power supply to the microcontroller
   * Connect an LED to the breadboard on an independent strip such that the positive and negative pins are on different rows
   * Connect the LED negative pin (shorter and GND) to the negative line of the power rails directly
   * Connect the LED positive pin (longer and input) to the digital pin specified in step 3
6. Connect the LCD display to the microcontroller
   * Connect 4 F-to-F jumper wires to the GND, VCC, SDA and SCL pins of the I2C adaptor connected to the LCD
   * Connect 4 M-to-M jumper wires to the F-to-F jumper wires such that each pin from the LCD can connect to a pinhole in the terminal strips on either side of the microcontroller
   * Connect the GND and VCC pins to the free and adjacent GND and VCC pins on the right side of the ESP32-CAM via the terminal strips with 2 of the 4 connected M-to-M jumper wires
7. Test the LCD screen
   * Connect the ESP32-CAM back to the baseboard
   * Open the Arduino IDE
   * Download the LiquidCrystal_I2C_Hangul library via `Tools > Manage Libraries…`
   * Restart the Arduino IDE
   * Open the printEnglish sketch from the newly downloaded library via `File > Examples > Examples from Custom Libraries > LiquidCrystal_I2C_Hangul`
   * Define the pins such that the LCD's SDA pin is connected to GPIO 14 of the ESP32-CAM and the LCD's SCL pin to GPIO 15 *(**NOTE:** See a full tutorial for defining an I2C LCD connection with regular IO pins via this [link](https://randomnerdtutorials.com/esp32-i2c-communication-arduino-ide/))*
   * In the code, set the I2C address to x27 *(**NOTE:** See how to determine the I2 address based on the LCD model via this [link](https://randomnerdtutorials.com/esp32-i2c-communication-arduino-ide/))*
   * Select the correct board (ESP32 AI Thinker) and port in the "Tools" menu
   * Click the "Upload" button
   * Disconnect the ESP32-CAM from the baseboard
   * Place it in its original position on the breadboard
   * Connect the remaining 2 M-to-M jumper wires to GPIO 14 and 15 via the terminal strips
8. Test the image classifier code
   * Go to http://edgeimpulse.com
   * Navigate to `Project > Deployment`
   * Select "Arduino library" under "Create library" 
   * Click on the "Build" button which will download a zip folder to your laptop
   * Go back to the Arduino IDE
   * Add the downloaded Arduino library to the Arduino IDE through `Sketch > Include Library > Add .ZIP Library…`
   * Restart the Arduino IDE
   * Open the ML edge code from `File > Examples > Examples from Custom Libraries > name-of-project_inferencing`
   * Select the correct board (ESP32 AI Thinker) and port in the `Tools` menu
   * Click the "Upload" button
   * Open the Serial Monitor at the port specified in the code
9. Incorporate visual display code
   * Include the LCD code libraries in the model code
   * Include the I2C_SDA and I2C_SCL code in the model code
   * Include the LCD code instance creation under function definitions in the model code
   * Include visual output on the LCD ordered by control statements in the section of the model code which prints out the predictions to the Serial Monitor
10. Deploy the consolidated classifier code to the system
   * Select the correct board (ESP32 AI Thinker) and port in the `Tools` menu
   * Click the "Upload" button
   * Disconnect the ESP32-CAM from the baseboard
   * Place it in its original position on the breadboard
