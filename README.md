# PS42ESP32
A project to use a PS4 Controller with esp32 board in ESP-IDF and Arduino Projects

This project are based on work of [aed3](https://github.com/aed3) to connect a ps4 controller to an ESP32 [Link of the repo](https://github.com/aed3/PS4-esp32), with some adjust to use this in ESP-IDF projects, in newest versions of the framework, and in Arduino IDE too.

This is heavily based on the work of Jeffery Pernis to connect a PS3 controller to an ESP32.
You can find that here: https://github.com/jvpernis/esp32-ps3

[Here's a video](https://youtu.be/BmlKBs27pgE) about how this library was made.

This repo can be downloaded as a zip file and imported into the Arduino IDE as a library


## Pairing the PS4 Controller:
When a PS4 controller is 'paired' to a PS4 console, it just means that it has stored the console's Bluetooth MAC address, which is the only device the controller will connect to. Usually, this pairing happens when you connect the controller to the PS4 console using a USB cable, and press the PS button. This initiates writing the console's MAC address to the controller.

Therefore, if you want to connect your PS4 controller to the ESP32, you either need to figure out what the Bluetooth MAC address of your PS4 console is and set the ESP32's address to it, or change the MAC address stored in the PS4 controller.

Whichever path you choose, you might want a tool to read and/or write the currently paired MAC address from the PS4 controller. You can try using [sixaxispairer](https://github.com/user-none/sixaxispairer) for this purpose.

If you opted to change the ESP32's MAC address, you'll need to include the ip address in the ```PS4.begin()``` function during within the ```setup()``` Arduino function like below where ```1a:2b:3c:01:01:01``` is the MAC address (**note that MAC address must be unicast**):
```
void setup()
{
    PS4.begin("1a:2b:3c:01:01:01");
    Serial.println("Ready.");
}
```
