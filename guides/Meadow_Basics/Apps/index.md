# Meadow Applications

Meadow applications are basically just .NET console applications. 

```csharp
using System;
using System.Threading;
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

Launches:

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
    	...
    }
}
```

## `IApp` Interface

Your main application class should implement @"Meadow.IApp"