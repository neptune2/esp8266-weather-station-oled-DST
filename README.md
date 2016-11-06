# esp8266-weather-station-OLED-DST

Daylight Saving Time and other customizations of Squix78 ESP8266 OLED Weather Station.
Uses SSD1306 128x64 OLED display with with either SPI or I2C interface

## Specific customizations include:

*  Added Wifi Splash screen and credit to Squix78
*  Modified progress bar to a thicker and symmetrical shape
*  Replaced TimeClient with built-in lwip sntp client (no need for external ntp client library)
*  Added Daylight Saving Time Auto adjuster with DST rules using simpleDSTadjust library
 * https://github.com/neptune2/simpleDSTadjust
*  Added Setting examples for Boston, Zurich and Sydney
 * Selectable NTP servers for each locale
 * DST rules and timezone settings customizable for each locale
  * See https://www.timeanddate.com/time/change/ for DST rules
 * Added AM/PM or 24-hour option for each locale
*  Changed to 7-segment Clock font from http://www.keshikan.net/fonts-e.html
*  Added Forecast screen for days 4-6
 *   >>> Need to change WundergroundClient.h in ESP8266_Weather_Station library
 *    #define MAX_FORECAST_PERIODS 12  // Was 7
*  Added support for DHT22 Indoor Temperature and Humidity
*  Fixed bug preventing display.flipScreenVertically() from working
* Slight adjustment to overlay


## Hardware Requirements

This code is made for an 128x64 SSD1603 OLED display with code running on an ESP8266.
Either the SPI or I2C version can be used.
You can buy the original Squix78 Weatherstaion Kit here: 
[https://shop.squix.ch/index.php/esp8266.html](https://shop.squix.ch/index.php/esp8266.html)

## Software Requirements/ Libraries

* Arduino IDE with ESP8266 platform installed
* [Weather Station Library](https://github.com/squix78/esp8266-weather-station) or through Library Manager
* [ESP8266 OLED SSD1306 Library](https://github.com/squix78/esp8266-oled-ssd1306)
* [WifiManager](https://github.com/tzapu/WiFiManager)

### Additional required library for automatic Daylight Saving Time adjust
* [simpleDSTadjust](https://github.com/neptune2/simpleDSTadjust)

You also need to get an API key for the Wunderground data: https://www.wunderground.com/

## Wemos D1R2 Wiring
![Wemos](https://github.com/neptune2/esp8266-weather-station-oled-DST/raw/master/resources/wemos_oled_weatherstation.jpg)

See code for pin configurations

| SSD1306 SPI | Wemos D1R2 |
| ----------- |:----------:|
| CS          | D8         |
| DC          | D2         |
| RST         | D0         |
| D1          | D7         |
| D0          | D5         |
| GND         | GND        |
| VCC         | 3V3        |

| DHT22 | Wemos D1R2 |
| ----- |:----------:| 
| DATA  | D4         |
| GND   | GND        |
| VCC   | 3V3        |
