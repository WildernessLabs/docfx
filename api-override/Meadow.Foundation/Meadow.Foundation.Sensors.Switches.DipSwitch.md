---
uid: Meadow.Foundation.Sensors.Switches.DipSwitch
remarks: *content
---

Represents a DIP-switch wired in a bus configuration, in which all switches are terminated to the same ground/common or high pin.

![](DIP_Switches.jpg)

---
uid: Meadow.Foundation.Sensors.Switches.DipSwitch
example: [*content]
---

```csharp
using Meadow;
using System.Threading;
using Meadow.Foundation.Sensors.Switches;

namespace Meadow.Foundation.Core.Samples
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
        public void App()
        {
            var dipSwitch = new DipSwitch(IDigitalPin[] {
                Device.Pins.D01, Device.Pins.D02, 
                Device.Pins.D03, Device.Pins.D04, 
                Device.Pins.D05, Device.Pins.D06, 
                Device.Pins.D07, Device.Pins.D08,  },
                CircuitTerminationType.CommonGround);

            dipSwitch.Changed += (object s, ArrayEventArgs e) =>
            {
                Debug.Print("Switch " + e.ItemIndex + " changed to " 
                    + (((ISwitch)e.Item).IsOn ? "on" : "off"));
            };

            Thread.Sleep(Timeout.Infinite);
        }
    }
}
```