---
uid: Meadow.Foundation.Sensors.Moisture.FC28
remarks: *content
---

FC-28 Soil Moisture Sensor is a simple breakout for measuring the moisture in soil and similar materials. The sensor has two probes and measures the resistance between them. Since water is conductive, as moisture in the soil increases, the resistance decreases allowing the sensor to determine soil humidity.

---
uid: Meadow.Foundation.Sensors.Moisture.FC28
example: [*content]
---

The following example shows how read the soil moisture sensor every second:

```csharp
using System.Threading;
using Meadow;
using Meadow.Foundation.Sensors.Moisture;

namespace FC28_Sample
{
    public class Program
    {
        static IApp _app; 
        public static void Main()
        {
            _app = new App();
        }
    }
    
    public class App : AppBase<F7Micro, App>
    {
        FC28 _FC28;

        public App ()
        {
            // create a new FC-28 object connected to analog pin A01 and digital pin 14
            _FC28 = new FC28(Device.Pins.A01, Device.Pins.D14);

            Run();
        }

        async Task Run()
        {
            while (true)
            {
                float moisture = await _FC28.Read();
                Console.WriteLine($"Moisture: {moisture}");
                Thread.Sleep(1000);
            }
        }
    }
}
```

##### Example Circuit

![](/API_Assets/Meadow.Foundation.Sensors.Moisture.FC28/FC28.svg)