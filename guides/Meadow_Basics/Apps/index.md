# Meadow Applications

Meadow applications are basically just .NET console applications. In fact, for now, to create a new Meadow application, you'll create a regular console application and in `static void Main`, launch a [`Meadow.IApp`](xref:Meadow.IApp):

```csharp
using System;
using Meadow;

namespace HelloLED
{

    class MainClass
    {
        static IApp _app;

        static void Main(string[] args)
        {
            // instantiate and run new meadow app
            _app = new LEDApp();
            _app.Run();
        }
    }
}
```

## Meadow Package

Once the console application is created, the `Meadow` core package should be installed via Nuget:

```
> nuget install Meadow
```

## `AppBase` Class

The main Meadow application class should inherit @"Meadow.AppBase", which provides a way for Meadow OS to notify the application of system events such as going to sleep, or waking up.

Currently, we don't enforce the use of `AppBase`, but in a future build of Meadow, it'll scan your Meadow application assembly for a class that implements `IApp` and launch that automatically, so it's a good practice to use the pattern now.

The `AppBase` declaration requires two generic parameters; `D`, and `A`, representing the device type and the application class type, respectively. For `D`, you'll need to pass an @"Meadow.IDevice` that represents the board you're using, such as `F7Micro`. For `A`, you should pass the typename of your application class itself. 

For example, if your app class is called `LEDApp`, and you're using a Meadow F7 Micro board, your `LEDApp` declaration would look like the following:

```csharp
public class LEDApp : AppBase<F7Micro, LEDApp>
```

[why D,A]

## Sample Meadow Application

Here is a complete example of an application that cycles through some colors on the onboard LED:


```csharp
using System;
using System.Threading;
using Meadow;
using Meadow.Devices;
using Meadow.Hardware;

namespace HelloLED
{
    class LEDApp : AppBase<F7Micro, LEDApp>
    {
        private DigitalOutputPort _redLED;
        private DigitalOutputPort _blueLED;
        private DigitalOutputPort _greenLED;

        public override void Run()
        {
            CreateOutputs();
            ShowLights();
        }

        public void CreateOutputs()
        {
            _redLED = new DigitalOutputPort(Device.Pins.OnboardLEDRed, false);
            _blueLED = new DigitalOutputPort(Device.Pins.OnboardLEDBlue, false);
            _greenLED = new DigitalOutputPort(Device.Pins.OnboardLEDGreen, false);
        }

        public void ShowLights()
        {
            var state = false;

            while(true)
            {
                state = !state;

                Console.WriteLine($"State: {state}");

                _redLED.State = state;
                Thread.Sleep(200);
                _greenLED.State = state;
                Thread.Sleep(200);
                _blueLED.State = state;
                Thread.Sleep(200);
            }
        }
    }
}
```