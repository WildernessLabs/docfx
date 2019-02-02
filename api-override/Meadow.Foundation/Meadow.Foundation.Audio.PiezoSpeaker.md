---
uid: Meadow.Foundation.Audio.PiezoSpeaker
remarks: *content
---

Piezo speakers (or piezoelectric speaker) is a loudspeaker that uses the piezoelectric effect for generating sound. The initial mechanical motion is created by applying a voltage to a piezoelectric material, and this motion is typically converted into audible sound using diaphragms and resonators.

---
uid: Meadow.Foundation.Audio.PiezoSpeaker
example: [*content]
---

The following example shows how to initialize a PiezoSpeaker and play a melody using an array of notes:

```csharp
using System.Threading;
using Meadow;
using Meadow.Foundation.Audio;

namespace PiezoSpeaker_Sample
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
        const int NUMBER_OF_NOTES = 16;
        float[] melody;

        public App ()
        {
            melody = new float[NUMBER_OF_NOTES] 
            {
                NoteFrequencies.NOTE_A3,
                NoteFrequencies.NOTE_B3,
                NoteFrequencies.NOTE_CS4,
                NoteFrequencies.NOTE_D4,
                NoteFrequencies.NOTE_E4,
                NoteFrequencies.NOTE_FS4,
                NoteFrequencies.NOTE_GS4,
                NoteFrequencies.NOTE_A4,
                NoteFrequencies.NOTE_A4,
                NoteFrequencies.NOTE_GS4,
                NoteFrequencies.NOTE_FS4,
                NoteFrequencies.NOTE_E4,
                NoteFrequencies.NOTE_D4,
                NoteFrequencies.NOTE_CS4,
                NoteFrequencies.NOTE_B3,
                NoteFrequencies.NOTE_A3,
            };

            var piezo = new PiezoSpeaker(Device.Pins.D10);

            while (true)
            {
                for(int i = 0; i < NUMBER_OF_NOTES; i++)
                {
                    //PlayTone with a duration in synchronous
                    piezo.PlayTone(melody[i], 600);
                    Thread.Sleep(50);
                }
                
                Thread.Sleep(1000);

                //PlayTone without a duration will return immediately and play the tone
                piezo.PlayTone(NoteFrequencies.NOTE_A4);
                Thread.Sleep(2000);

                //call StopTone to end a tone started without a duration
                piezo.StopTone();

                Thread.Sleep(2000);
            }
        }
    }

    public static class NoteFrequencies
    {
        public const float NOTE_A3  = 220;
        public const float NOTE_B3  = 247;
        public const float NOTE_CS4 = 277;
        public const float NOTE_D4  = 294;
        public const float NOTE_E4  = 330;
        public const float NOTE_FS4 = 370;
        public const float NOTE_GS4 = 415;
        public const float NOTE_A4  = 440;
    }
}
```

##### Example Circuit

![](/API_Assets/Meadow.Foundation.Audio.PiezoSpeaker/PiezoSpeaker.svg)