# Input/Output (IO)

IO is a big part of what makes Meadow magical. Meadow boards expose a wide variety of ways to control and interact with external peripherals and hardware via _General Purpose I/O_ (GPIO) ports.

GPIO ports can be accessed from your application to read sensors, listen to button presses, light LEDs, drive motors, communicate with other systems, and lots more.

## Types of IO

Meadow GPIO ports are divided into two categories; _Digital_ and _Analog_. 

Digital and analog refer to the type of electrical signal used; either `HIGH`/`LOW` for digital, or a range of voltage for analog, and they're used for different things.

### Digital IO

Digital ports can be set to be `HIGH` (powered at `3.3V`), or `LOW` (grounded at `0V`) which correspond to digital `1` and `0`, respectively. Additionally, the digital ports have built-in support for a host of different types of common digital communication protocols including:

* I2C (Inter Integrated Circuit)
* SPI (Serial Peripheral Interface)
* UART (Serial)
* PWM (Pulse Width Modulation)
* CAN (Car Area Network)
* I2S (Integrated Inter-IC Sound Bus)

| Protocol | Characteristics                                                |
|----------|----------------------------------------------------------------|
|   I2C    | Two wires<br/>Short distance<br/>Low speed<br/>Can support multiple devices. |
|   SPI    | Minimum of two wires, often more<br/>High speed<br/>Can support multiple devices. |
|  Serial  | Low speed<br/>Used for communication between boards<br/>Can be used to communicate with on board devices<br/>Generally supports only one device per COM channel.  |

### Analog IO

Analog ports can operate at a range of voltages between `0V` and `3.3V`, which is especially useful when reading analog sensors that supply their data as a voltage reading, rather than a digital signal. For instance an analog temperature sensor that is able to detect temperatures from `0ºC` to `100ºC` might output a voltage of `1.6V` (halfway between `0V` and `3.3V`) for `50º`.

### F7 Micro IO Pinout

GPIO ports are available via pins (as well as the onboard LED) on the Meadow F7 Micro, and many of these pins are actually overloaded to support multiple functions, as shown below:

![](/Common_Assets/Meadow_F7_Micro_Pinout.svg)

The function that they serve depends on how they are configured when a _port_ is instantiated on one of them. For instance, pin `D00` can be configured to be used a digital input or output, or as the `RX` (receive) half of a Serial UART port available as "COM4".

#### Pins, Ports, and ChannelInfo

When working with GPIO in Meadow, there are three different terms/concepts to be aware of:

* **Pin** - Represents a physical connection point on a device, such as pin `D01`.
* **Port** - Represents the underlying IO feature that allows communication, such as a @"Meadow.Hardware.DigitalInputPort" which reads digital input signals.
* **ChannelInfo** - Describes the capabilities of a particular pin or port, for instance, whether or not a pin supports digital interrupts (notification on change).


[Pins are available on the Device class, and are used to created ports]

Can interrogate the capabilities of a pin via the channel interface:

```
var maxFreq = PwmPin.MaximimumFrequency;
```


Can get the underlying channel info from a port:

```
var minFreq = PwmPort.ChannelInfo.MaximumFrequency;
```

## Meadow.Foundation

[simplifies much of this, but you still need to know which pins can support which functions]

## [Next - Meadow.Foundation](/guides/Meadow.Foundation/index.html)


### IO Function Reference Table (TODO: move this to advanced IO docs)

```
SCHEMATIC       CPU PIN   MDW NAME  ALT FN
DAC_OUT1        PA4         A0
DAC_OUT2        PA5         A1
ADC1_IN3        PA3         A2
ADC1_IN7        PA7         A3
ADC1_IN10       PC0         A4
ADC1_IN11       PC1         A5
SPI3_CLK        PC10        SCK
SPI3_MOSI       PB5         MOSI    AF6
SPI3_MISO       PC11        MISO    AF6
UART4_RX        PI9         D00     AF8
UART4_TX        PH13        D01     AF8
PC6             PC6         D02         
CAN1_RX         PB8         D03     AF9
CAN1_TX         PB9         D04     AF9
PE3             PE3         D15
PG3             PG3         D14
USART1_RX       PB15        D13     AF4
USART1_TX       PB14        D12     AF4
PC9             PC9         D11
PH10            PH10        D10
PB1             PB1         D09
I2C1_SCL        PB6         D08     AF4
I2C1_SDA        PB7         D07     AF4
PB0             PB0         D06
PC7             PC7         D05
```