---
uid: Meadow.Foundation.Sensors.Barometric.MPL115A2
remarks: *content
---

The AT24Cxx series of chips provide a mechanism for storing data that will survive a power outage or battery failure.  These EEPROMs are available in varying sizes and are accessible using the I2C interface.

---
uid: Meadow.Foundation.Sensors.Barometric.MPL115A2
example: [*content]
---

The following example shows how to turn on and off the LED using the `IsOn` property, and uses a `StartBlink(onDuration, offDuration)` API method to make the LED blink staying on for 500ms (0.5s) and off for 1000ms (1s):

```csharp
using System.Threading;
using Meadow;
using Meadow.Foundation.ICs.EEPROM;

namespace LedSample
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
        public App ()
        {
            var eeprom = new AT24Cxx(0x57);

            var memory = eeprom.Read(0, 16);
            for (ushort index = 0; index < 16; index++)
                Console.WriteLine("Byte: " + index + ", Value: " + memory[index]);

            eeprom.Write(3, new byte[] { 10 });
            eeprom.Write(7, new byte[] { 1, 2, 3, 4 });
            
            memory = eeprom.Read(0, 16);
            for (ushort index = 0; index < 16; index++)
                Console.WriteLine("Byte: " + index + ", Value: " + memory[index]);
            

            Thread.Sleep(Timeout.Infinite);
        }
    }
}
```

##### Example Circuit

![](/API_Assets/Meadow.Foundation.Sensors.Barometric.MPL115A2/MPL115A2.svg)