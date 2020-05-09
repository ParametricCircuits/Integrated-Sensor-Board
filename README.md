# Integrated-Sensor-Board
ATmega328 + accelerometer + light sensor + temperature sensor + barometer + SPI flash + microSD + WS2812 + USB serial<br/>
This is the github repo for the Integrated Sensor Board, which can be found at [tindie.com/products/parametriccircuits/customizable-integrated-sensor-board/](https://www.tindie.com/products/parametriccircuits/customizable-integrated-sensor-board/)

# Tested libraries

## 16MB SPI flash
[SPIMemory](https://github.com/Marzogh/SPIMemory) by Marzogh

## Accelerometer 
[SparkFun_MMA8452Q_Arduino_Library](https://github.com/sparkfun/SparkFun_MMA8452Q_Arduino_Library) by Sparkfun

## Barometer
Strictly speaking, this isn't a library, it's just example code that directly uses the arduino Wire (I2C) library. 
However, it does provide code to read altitude, pressure, and temperature, and the code is quite simple and easily modified.<br/>
[HP203B](https://github.com/ControlEverythingCommunity/HP203B) by ControlEverythingCommunity

## MicroSD
For simple use, Arduino's build in library works great.<br/>
For more advanced use, try the [SdFat](https://github.com/greiman/SdFat) library by Greiman

## Phototransistor
Due to the nature of ambient light, especially indoor lighting which can multiple different 
spectra depending on the type of light source, it is difficult to provide a properly quantifiable number 
(eg lumens, mcd, or other light/brightness measurements). This is a limitation present in phototransistors in general.
As such, you will likely want to calibrate the sensor for the specific use case that you have for it.<br/>
This can be as simple as calling `Serial.print(analogRead(A2));` repeatedly, and recording the output voltage produced at 
different light levels.

## Temperature sensor 
As the conversion is so simple, a full library is overkill. This one liner works well to get degrees C:
```
float tempMCP = ((analogRead(A3)*5/1024.0)- 0.5 )/ 0.01;
```

## Ws2812 RGB Led
[fastLED](https://github.com/FastLED/FastLED) by fastled.io<br/>
[Neopixel](https://github.com/adafruit/Adafruit_NeoPixel) library by Adafruit 
