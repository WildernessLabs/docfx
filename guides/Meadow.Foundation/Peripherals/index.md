# Meadow.Foundation Peripherals Library

The Meadow.Foundation peripherals library is an [open source](https://github.com/WildernessLabs/Meadow.Foundation) repository of drivers for various peripherals such as sensors, motors, displays, cameras, and other peripherals which make it easy to add hardware to your Meadow application.

The peripherals are split into two groups; the first group is general, core peripherals that are included in the main [Meadow.Foundation](https://www.fuget.org/packages/Meadow.Foundation) Nuget package. The second group are additional drivers that are available via separate Nuget packages to keep the core size to a minimum.

**Note:** While nearly all Meadow.Foundation drivers have been ported from our earlier [Netduino.Foundation](http://Netduino.Foundation) work, few are up and working right now, and this page will be updated as we test and write samples for them.


## Core Peripherals

### LEDs

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.LEDs.Led"             | Simple LED. | Yes | |
| @"Meadow.Foundation.LEDs.PwmLed"          | Pulse-Width-Modulation powered LED. | | Blocked on PWM |  
| @"Meadow.Foundation.LEDs.RgbPwmLed"       | Pulse-Width-Modulation powered RGB LED. | | Blocked on PWM |
| @"Meadow.Foundation.LEDs.LedBarGraph"     | Generic segmented LED bar. | Yes | |

### Motors

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Motors.HBridgeMotor" | Generic h-bridge motor controller. | | |

### Relays

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Relays.Relay" | Electrically isolated switch. | Yes | |

### Speakers

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Audio.PiezoSpeaker" | A 2 pin piezo-electric speaker capable of generating tones. | | |

### Sensors

#### Buttons

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Sensors.Buttons.PushButton" | Simple push-button. | | |

#### Rotary Encoders

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Sensors.Rotary.RotaryEncoder" | A simple rotary encoder. | | |
| @"Meadow.Foundation.Sensors.Rotary.RotaryEncoderWithButton" | A rotary encoder that includes a push button. | | |

#### Switches

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Sensors.Switches.SpstSwitch" | A simple single-pole, single-throw (SPST) switch. | | |
| @"Meadow.Foundation.Sensors.Switches.SpdtSwitch" | A simple single-pole, dual-throw (SPDT) switch. | | |
| @"Meadow.Foundation.Sensors.Switches.DipSwitch"  | A multi-pole dip switch. | | |

#### Temperature

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Sensors.Temperature.AnalogTemperature" | Analog temperature sensor (TMP35 / TMP36 / TMP37 / LM35) | | |

#### Hall Effect

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Sensors.HallEffect.LinearHallEffectTachometer" | Hall Effect Linear Tachometer sensor. | | |

## Additional Peripherals

### Display and Graphics Drivers

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| [Graphics Library](/api/Meadow.Foundation/Meadow.Foundation.Displays.GraphicsLibrary.html)  | General purpose graphics library. |
| [Lcd2004](/api/Meadow.Foundation/Meadow.Foundation.Displays.LCD.Lcd2004.html)               | LCD display | | |
| [Seven Segment Display](/api/Meadow.Foundation/Meadow.Foundation.Displays.LCD.Lcd2004.html) | Seven Segment Display | | |
| [PCD8544](/api/Meadow.Foundation/Meadow.Foundation.Displays.PCD8544.html)                   | PCD8544 LCD driver (Nokia 5110) | | |
| [Serial LCD](/api/Meadow.Foundation/Meadow.Foundation.Displays.SerialLCD.html)              | SparkFun serial LCD backpack driver.|
| [SSD1306](/api/Meadow.Foundation/Meadow.Foundation.Displays.SSD1306.html)                   | SSD1306 OLED Display.  Currently supports 128x64 and 128x32 pixel I2C displays. |
| [Text Display Menu](/api/Meadow.Foundation/Meadow.Foundation.Displays.TextDisplayMenu.html) | Text Display Menu for LCD displays. |
| [TFTSPI](/api/Meadow.Foundation/Meadow.Foundation.Displays.html)                            | Thin Film Transistor (TFT) SPI Library. |
| [WaveShare ePaper](/api/Meadow.Foundation/Meadow.Foundation.Displays.html)                  | Electronic paper display. |

### Integrated Circuits (ICs)

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.ICs.EEPROM.AT24Cxx" | AT24Cxx Family of EEPROMs including AT24C32. |
| @"Meadow.Foundation.ICs.IOExpanders.x74595"                                         | 74595 shift register for digital output expansion. |
| @"Meadow.Foundation.ICs.IOExpanders.MCP23008"                                       | MCP23008 for digital output expansion.           |
| [DS323x RTCs](/api/Meadow.Foundation/Meadow.Foundation.RTCs.DS323x.html)            | Real Time Clock modules. |

### Sensors

#### Atmospheric (Temperature, Humidity, Barometer, Altitude) Sensors

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| [BME280](/Library/Sensors/Atmospheric/BME280)      | Combined I2C/SPI temperature, humidity, and pressure sensor. |
| BMP085                                             | In development |
| GroveTH02                                          | In development |
| [HIH6130](/Library/Sensors/Atmospheric/HIH6130)    | Combined I2C temperature and humidity sensor. |
| HTU21DF                                            | In development |
| [SHT31D](/Library/Sensors/Atmospheric/SHT31D)      | Combined I2C temperature and humidity sensor. |
| [SiI7021](/Library/Sensors/Atmospheric/SI7021)     | Combined I2C temperature and humidity sensor. |
| @"Meadow.Foundation.Sensors.Barometric.MPL115A2"   | MPL115A2 Barometric sensor. |
| @"Meadow.Foundation.Sensors.Barometric.MPL3115A2"  | MPL3115A2 Barometric sensor. |
| [DS18B20](/Library/Sensors/Temperature/TMP102)     | DS18B20 temperature sensor. |
| [TMP102](/Library/Sensors/Temperature/TMP102)      | TMP102 temperature sensor. |

#### Distance Sensors

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Sensors.Distance.HCSR04" | HCSR04 distance sensor. |
| @"Meadow.Foundation.Sensors.Distance.HYSRF05" | HYSRF05 distance sensor. |
| SharpGP2D12               | In Development |

#### GPS Sensors & Libraries

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| [NMEA GPS Decoder](/Library/Sensors/GPS/NMEA)      | Generic GPS sentence decoder library. |

#### Light Sensors

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| [ALS-PT19](/Library/Sensors/Light/ALSPT19315C)     | Analog light sensor. |
| [SI1145](/Library/Sensors/Light/SI1145)            | I2C infrared, ultraviolet, and ambient light sensor. |
| [TSL2561](/Library/Sensors/Light/TSL2561)          | I2C infrared-compensated light sensor. |

#### Soil Moisture Sensors

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| @"Meadow.Foundation.Sensors.Moisture.Capacitive" | Capacitive Soil Moisture Sensor |
| @"Meadow.Foundation.Sensors.Moisture.FC28" | FC-28 Soil Moisture Sensor |

#### Motion and Orientation Sensors

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| [ADXL335](/Library/Sensors/Motion/ADXL335)         | Analog triple axis, +/-3g accelerometer. |
| [ADXL345](/Library/Sensors/Motion/ADXL345)         | I2C triple axis accelerometer, +/-16g accelerometer. |
| ADXL362 Accelerometer     | In Development |
| [BNO055](/Library/Sensors/Motion/BNO055)           | I2C 9-Axis absolute orientation sensor. |
| FXAS21002                 | In Development |
| FXOS8700CQ                | In Development |
| [MAG3110](/Library/Sensors/Motion/MAG3110)         | I2C three axis magnetometer. |
| Memsic2125                | In Development |
| MPU6050                   | In Development |
| @"Meadow.Foundation.Sensors.Motion.ParallaxPIR" | Parallax PIR Rev B digital motion detector. |

### Shields

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| Adafruit Motor Shield     | In Development |
| SparkFun Weather Shield   | In Development |

### Servos

| Driver           | Description | Tested Working      | Notes                             |
|------------------|-------------|---------------------|-----------------------------------|
| [ServoCore](/Library/ServoCore/)                | Generic servo library. |

