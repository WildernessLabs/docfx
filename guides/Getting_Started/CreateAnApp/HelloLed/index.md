# HelloLed App

Here we'll create an application for the Meadow F7 board. The application will control the onboard RGB led and write text to the console.

## Before you start
1. Make sure you've setup your (development environment)[../Setup/index.html]
1. (Create a new Meadow application)[../index.html] named **HelloLed** (Create a Meadow application)[../index.html] 
- create a .NET 4.7.1 console application
- change the assembly name to **app**
- add the Meadow.Core NuGet package
3. Open your **HelloLed** project in Visual Studio if you haven't already

## Add the App class
Wilderness Labs recommends placing your logic in an application class that's instantiated in the `Program` class when the app starts.

1. Create a new `public` class named `App`
1. Add `using` statements to `Meadow`, `Meadow.Devices`, and `Meadow.Hardware`
1. Change the class signature to derive from `AppBase<F7Micro, App>`
1. Add a `void` returning method named `InitializeHardware`
1. Call `InitializeHardware` from the constructor

```csharp
using Meadow;
using Meadow.Devices;

namespace HelloLED
{
    public class App : AppBase<F7Micro, App>
    {
        public App()
        {
            InitializeHardware();
        }

        void InitializeHardware()
        {
        }
    }
}
```

## Control the Onboard LED
Now we'll add fields to control the onboard leds and toggle them off and on periodically.

1. Add three (3) fields of type `DigitalOutputPort` named `redLed`, `greenLed`, and `blueLed`
1. In the `InitializeHardware method, instantiate each output port using `Device.Pins` to reference the onboard internal pins to control each color of the led
```csharp
DigitalOutputPort redLed;
DigitalOutputPort greenLed;
DigitalOutputPort blueLed;
...

void InitializeHardware()
{
    redLed = new DigitalOutputPort(Device.Pins.OnboardLEDRed, false);
    blueLed = new DigitalOutputPort(Device.Pins.OnboardLEDBlue, false);
    greenLed = new DigitalOutputPort(Device.Pins.OnboardLEDGreen, false);
}
```

Now we'll add a method to toggle the leds. We do this by controlling the `DigitalOutputPort`'s boolean `State` property. Within the while loop, we'll write the current state to the Console and toggle the leds in sequence. 

We'll need two (2) additional `using` statements, add `System` and `System.Threading` if there not their already.

Add the code below:
```csharp
using System;
using System.Threading;
...

public void ToggleLeds()
{
    bool state = false;
    int sleepTime = 150; //in ms

    while(true)
    {
        state = !state;

        Console.WriteLine($"State: {state}");

        blueLed.State = state;
        Thread.Sleep(sleepTime);
        redLed.State = state;
        Thread.Sleep(sleepTime);
        greenLed.State = state;
        Thread.Sleep(sleepTime);
    }
}
```

Finally, call `ToggleLeds` from the constructor after `InitializeHardware`
```csharp
public App()
{
    InitializeHardware();
    ToggleLeds();
}
```

## Instantiate the App class
The last thing we need to do is create an instance of the `App` class when the application starts.
1. Open Program.cs
1. A `using` statement for `Meadow`
1. Create a static field of type `IApp` named **app**
1. In the constructor, instantiate an `App` instance and assign it to **app**

```csharp
using Meadow;

namespace HelloLED
{
    class Program
    {
        static IApp app;
        static void Main(string[] args)
        {
            app = new App();
        }
    }
}
```

## Compile and run the application
You're now ready to build and deploy your Meadow app. 
1. Build the application
1. Using Finder or the File Explorer, navigate to the folder that contains your application 
1. Open the **bin->Debug** folder, you should see **app.exe** and **Meadow.Core.dll** - you'll need both to deploy your app to Meadow
1. Follow the (Deployment instructions here)[../Deployment/index.html] to deploy your app
