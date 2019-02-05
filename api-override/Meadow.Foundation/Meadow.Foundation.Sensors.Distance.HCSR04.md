---
uid: Meadow.Foundation.Sensors.Distance.HCSR04
remarks: *content
---

Distance Sensor Remarks section!

---
uid: Meadow.Foundation.Sensors.Distance.HCSR04
example: [*content]
---

The application below uses a HCSR05 distance sensor.

```csharp
using System.Threading;
using Meadow;
using Meadow.Foundation.Sensors.Distance;

namespace HCSR04_Sample
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

![](/API_Assets/Meadow.Foundation.Sensors.Distance.HCSR04/HCSR04.svg)