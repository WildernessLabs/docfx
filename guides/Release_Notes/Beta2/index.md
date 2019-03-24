# Meadow Beta 2

## New Core Features

### New IO APIs

One of the big things we’ve been working on is a major rewrite of how IO is handled between the underlying OS and Mono (the managed runtime) where we’ve been able to simplify a lot of the underpinning there and make it much more efficient. 

Along the way, we’ve also done a lot of thinking and reworking of the API. Specifically, we’ve added two new features. The first, is that the IO Devices are self describing with a mapping of `Device` > `Pins` > `Channels`. For instance, the following Meadow code enumerates all the pins and what type of IO is possible for each pin:

```csharp
foreach(var pin in Device.Pins.AllPins) {
   Console.WriteLine("Found pin: " + pin.Name);
   foreach (var channel in pin.SupportedChannels) {
            Console.WriteLine("Contains a " + channel.GetType() 
            + "channel called: " + channel.Name + ".");
   }
}
```

[you can find this example here - need to copy to the samples repo]

Here’s an excerpt from the output the above code returns:

```bash
Found pin: A05
Contains a Meadow.Hardware.DigitalChannelInfochannel called: PC1.
Contains a Meadow.Hardware.AnalogChannelInfochannel called: ADC1_IN11.

Found pin: D00
Contains a Meadow.Hardware.DigitalChannelInfochannel called: PI9.
Contains a Meadow.Hardware.UartChannelInfochannel called: UART4_RX.

Found pin: D01
Contains a Meadow.Hardware.DigitalChannelInfochannel called: PH13.
Contains a Meadow.Hardware.PwmChannelInfochannel called: TIM8_CH1N.
Contains a Meadow.Hardware.UartChannelInfochannel called: UART4_TX.

Found pin: D02
Contains a Meadow.Hardware.DigitalChannelInfochannel called: PC6.
Contains a Meadow.Hardware.PwmChannelInfochannel called: TIM3_CH1.

Found pin: D03
Contains a Meadow.Hardware.DigitalChannelInfochannel called: PB8.
Contains a Meadow.Hardware.PwmChannelInfochannel called: TIM4_CH3.
Contains a Meadow.Hardware.CanChannelInfochannel called: CAN1_RX.
```

An astute observer familiar with the STM32F7 might notice that the analog port in the excerpt also exposes digital IO. We’re now much more flexible in what types of IOs are exposed on which pins; which provides more options for you. In fact, now there's 25 possible digital IOs. With these [`IChannelInfo`](xref:Meadow.Hardware.IChannelInfo) objects, the IO is also self-documenting, and you can see what kind of ports are available from each pin without having to refer to the IO pinout diagram.

#### Device-Centric API

Additionally, we made the API more device-centric. So instead of instantiating ports out of thin air (which was always just a little off); ports our now created via an [`IIODevice`](xref:Meadow.Hardware.IIODevice).

```csharp
IDigitalOutputPort redLED = Device.CreateDigitalOutputPort(Device.Pins.OnboardLEDRed);
```

The great thing about this, is that it doesn’t matter whether the ports are on the Meadow, or on external IO expanders, the API is the same. So we could also create a Digital Output Port from an MCP230xx IO expander, the same way:

```csharp
var ledPort = mcp.CreateDigitalOutputPort(mcp.Pins.D04);
```

This provides a more intuitive mental map of the hardware and also simplifies the IO control under the hood.

### New Meadow Samples Repo

It occurred to us recently that our Meadow core samples were locked behind a source code auth wall. Not anymore! We've moved them to their own repo at [github.com/WildernessLabs/Meadow_Samples](http://github.com/WildernessLabs/Meadow_Samples).

Check them out and see how to use the new APIs!

### Analog Input

It's time to break out your [analog temp sensors](xref:Meadow.Foundation.Sensors.Temperature.AnalogTemperature), because we've got analog input!

In the process we’ve got Analog inputs up, and we’re in the process or wiring up the Digital Input Events, as well as our new `IObservable`/Reactive pattern.


### Interrupts, Notifications + `IObservable` Reactive Pattern

## New Meadow.Foundation Features

### SoftPwm

### Analog Peripherals

### Eventing Peripherals


## Fixed Bugs

* [Threads Fail](https://github.com/WildernessLabs/Meadow_Issues/issues/1) - W00t! We haz multithreading!

## Known Issues

* `DebounceDuration` and `GlitchFilterCycleCount` are not implemented in `DigitalInputPort`. These are coming soon.
* [Tasks Behave Strangely](https://github.com/WildernessLabs/Meadow_Issues/issues/2) - Workaround is to use `Thread`, as seen in the [Basic_Threading](https://github.com/WildernessLabs/Meadow_Samples/blob/master/Source/MeadowSamples/Basic_Threading/ThreadingApp.cs) sample app.
* [`Debug.Write` calls don't output to the console](https://github.com/WildernessLabs/Meadow_Issues/issues/3) - Workaround is to use `Console.Write` calls.