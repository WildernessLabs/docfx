---
uid: Meadow.Foundation.Sensors.Distance.HYSRF05
remarks: *content
---

Distance Sensor Remarks section!

---
uid: Meadow.Foundation.Sensors.Distance.HYSRF05
example: [*content]
---

The application below uses a ShiftRegister74595 object to cycle through the bits on the shift register and light the appropriate LED.

```csharp
using System.Threading;
using Meadow;
using Meadow.Foundation.Sensors.Distance;

namespace HYSRF05_Sample
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

        }
    }
}
```

##### Example Circuit

![](/API_Assets/Meadow.Foundation.Sensors.Distance.HYSRF05/HYSRF05.svg)