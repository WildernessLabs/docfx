---
uid: Meadow.Foundation.LEDs.PwmLed
remarks: *content
---

Represents an LED whose voltage (and brightness) is controlled by the duty-cycle of a PWM signal. Can be used both with LEDs that have been current limited with in-series resistors, or LEDs without resistors.

Controlling an LED via a PWM signal is more power efficient than using a current-limiting resistor, and it provides more control; allowing multiple grades of brightness. However, it uses a PWM channel.

To use without resistors, pass in the forward voltage (voltage drop) of the LED to the `forwardVoltage` constructor parameter, and the class will limit its output to the maximum forward voltage rating of the LED.

To use with an LED that has a resistor in series, pass `0.0` or `TypicalForwardVoltage.ResistorLimited` for the `forwardVoltage` parameter.

---
uid: Meadow.Foundation.LEDs.PwmLed
example: [*content]
---

The following example alternates between blinking and pulsing an LED:

```csharp
using System.Threading;
using Meadow;

namespace PwmLedSample
{
    public class Program
    {
        public static void Main()
        {
            // create a new PwmLed on pin 8
            var pwmLed = new Meadow.Foundation.LEDs.PwmLed(
                Device.Pins.D08,
                LEDs.TypicalForwardVoltage.Green
            );

            // alternate between blinking and pulsing the LED 
            while (true)
            {
                pwmLed.StartBlink();
                Thread.Sleep(5000); // 5 seconds

                pwmLed.StartPulse(lowBrightness: 0.2F);
                Thread.Sleep(10000); // 10 seconds
            }
        }
    }
}
```

##### Example Circuit

![](/API_Assets/Meadow.Foundation.LEDs.PwmLed/PwmLed.svg)