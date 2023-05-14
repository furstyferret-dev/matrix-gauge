# matrix-gauge
A simple display of any battery level availabe to Home Assistant using a cheap 32x8 LED matrix.



## Required equipment:
- Home Assistant instance with some kind of battery connected.
- MAX7219 LED matrix
- Any microcontroller compatible with ESPHome.
- 3D printer for case (not essential)

## Getting started
Only five pins are required and all can be taken directly from the ESP8266 or ESP32. 

Use a pin-out diagram for your board to work out the best ones to use. ESPhome does not always have the silkscreen pin definitions loaded (ie "D1-D9") so you may need to refer directly to the GPIO pins in the code. Connections below are for the ESP8266 (Wemos D1 Mini). 

- VCC -> VCC (5V or 3.3V is fine)
- GND -> GND
- DIN -> MOSI (D7 / GPIO13)
- CS -> CS (D8 / GPIO15) 
- CLK -> SCLK (D5 / GPIO14) 

## Add to ESPHome / Home Assistant
This guide assumes you're familiar with doing this already. Create a new device in ESPHome, flash it via the browser, and let it connect to the network. 

Remember to add it to Home Assistant via the Integrations page or you won't get any data.

Now you can copy the code from the source.yaml file into your own project in ESPHome. You will need to provide your own sensors and modfiy the code appropriately:

- A sensor providing battery charge level (as a percentage).
- A sensor providing charge rate in kW (if you want the blinking charge animation).

Once it's up and running (ESP8266 can take up to 30 seconds to start receiving data) you will find an intensity control for the matrix in your Home Assistant entities tab.

## Modifications
Remove the slashes if you want the battery shape to be contiguous. 

There are multiple 3D printable cases for the MAX7219 arrays on Thingiverse. Choose an appropriate one. Any kind of diffuser over the grid will make it look better.

## License
You may use this code for any personal use or integration in any larger project provided that attribution is given. You MAY NOT use it in a commercial project or resell it in any form, including pre-loaded onto a microcontroller or with Home Assistant.
