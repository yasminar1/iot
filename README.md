# SipSmart

This Manual is made for SipSmart. You can control SipSmart with an app, voice commands, the coffee machine itself. SipSmart can be integrated with a Ring doorbell and with Philips Hue lights. In this manual I will show you how to connect to Philips Hue to get the full coffee experience.

# What you'll need

Hardware:
- NodeMCU ESP8266
- Ledstrip
  
![IMG_2861 normaal](https://github.com/user-attachments/assets/ef680cab-a0a3-480f-98b1-008f6ffd1827)

Software:
- Arduino IDE

# Connecting the NodeMCU
First, download and open Arduino IDE installer: https://www.arduino.cc/en/software

After downloading and opening Arduino IDE its time to install the NodeMCU Board.
1. Start Arduino IDE
2. Open Preferences in ArduinoIDE (macOS) or File (Windows) menu.
3. Paste http://arduino.esp8266.com/stable/package_esp8266com_index.json after'Additional Boardmanager URL's'.
4. Press OK'

Adding the board
1. Open Arduino IDE
2. Press' Tools; → 'Board' → 'Boards manager...'
3. In the searchfield, type: “esp8266”
4. Select “esp8266 by ESP8266 Community”
5. Select the newest version and press‘Install’
6. If this worked you'll see REMOVE next to the version number.
7. Close Arduino IDE

Installing the board settings
1. Connect the NodeMCU with USB to your computer
2. Start Arduino IDE.
3. Select Tools > Board > ESP8266 Boards> Select NodeMCU 1.0 (ESP12E module)
4. For macs: Press Tools > Port > /dev/cu.SLAB_USBtoUART
5. Windows: Press Tools > Port > COMx (try a number for 'x' until it works)
   For new Macs: usbserial-10 or something remotely like this.

The NodeMCU will blink if it is connected.
![IMG_2854](https://github.com/user-attachments/assets/b1771e09-37b4-4e8e-bb8c-59104967624b)

# Is the port no longer available?

A: Try a different USB port

B: Press the reset button

C: Put the board manually in program mode
-  Keep the 'Flash' button pressed.
- Keep the reset button pressed.
- Release the flash button.
- Release the reset button.

# Now it's time to connect our ledstrip to the NodeMCU!
- The brown wire = +5V
- The black wire = DIN
- The white wire = GND

1. Connect +5 to 3v3
2. Connect DIN to D5
3. Connect GND to GND
![IMG_2855](https://github.com/user-attachments/assets/4c619ad1-4130-487e-8e65-b61a31af5698)

Installing the library
1. Sketch > include library > Manage Libraries…
2. Install Neopixel - By Adafruit

Uploading Code
1. File -> examples -> adafruit Neopixel ->  Strandtest
2. Change the value after PIN  to D5 
3. Put the number 
of leds in your strip after NUMPIXELS.
4. Run the code
![IMG_2859](https://github.com/user-attachments/assets/ba6ef005-ecd6-441b-a78b-177f2ba893f5)

And there you have your rainbow!!

# Now it's time to create your own Philips Hue

Installeer de Arduino IO libraries: 
1. Press the third tap in Arduino (Library Manager).
2. Search for Adafruit IO Arduino (by Adafruit).
3. Install (press Install All).

Adafruit IO Setup:
1. To use Adafruit IO, we have to set up an account and create a dashboard.
2. Go to https://io.adafruit.com/ , press “Get Started for Free” and create an account.
3. After creating an account press the yellow key in the Adafruit IO menu. <img width="1000" alt="Scherm­afbeelding 2024-10-15 om 23 49 12" src="https://github.com/user-attachments/assets/f3c35a64-1ae2-4278-944b-576b6863823a">
4. Copy your key and username.

Adafruit IO Feed and create Colorpicker:
1. In adafruit IO go to dashboards > New Dashboard (create a new dashboard)
2. Ga to the dashboard
3. Create New Block
4. Choose color Picker
5. Create feed name: color
6. Create Block
7. Select a color with the Color Picker
<img width="1000" alt="Scherm­afbeelding 2024-10-15 om 23 49 23" src="https://github.com/user-attachments/assets/b4aabc7b-d1d4-448e-ac06-c1a00f53a80b">

Changing the code:
1. In Arduino: File > Examples > Adafruit IO Arduino > Adafruitio_14_neopixel
2. In tab ‘config.h’: paste your Adafruit IO username and Key
3. In tab ‘config.h’: put your wifi netwerk and password
4. in de Tab adafruit_14_Neopixel.ino change: #define PIXEL_PIN 5 to #define PIXEL_PIN D5

Upload code:
Activate ‘Serial Monitor’ 
Open serial monitor (tab on the bottom)
Change the serial monitor op 115200 baud
If everything worked, the serial monitor will display that you're connected

Now change the color in Adafruit IO, you will see this in the Serial monitor
If the ledstrip is connected, you'll be able to change the LED color with the colorpicker.

# You created your own Philips HUE!

# Errors
The connecttion between Adafruit IO and Arduino didn't work correctly.
<img width="955" alt="Scherm­afbeelding 2024-10-15 om 21 37 54" src="https://github.com/user-attachments/assets/a02fbdb3-1154-4b17-aec3-16349a372b67">

The first problem that my Serial monitor was just showing a string of dots.
After looking at different manuals I added Wifi.begin to the code. 
When I used that code the dots dissappeard and instead showed this:

<img width="950" alt="Scherm­afbeelding 2024-10-15 om 22 08 29" src="https://github.com/user-attachments/assets/bc8400a7-0c57-4bf0-bf65-7ba1a6d3b9e2">

Eventhough the baud was the same in the serial.monitor as it was in the code it still didn't change. I was also not able to change the lights via Adafruit IO. I searched a lot on Arduino forum, stackoverflow and different websites, the slides on DLO and other manuals, but I couldn't find the solution to this problem. I am alsno NOT great with tech which makes this an even bigger challenge..






