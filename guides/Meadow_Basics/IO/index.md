# IO

![](/Common_Assets/Meadow_F7_Micro_Pinout.svg)

## General-Purpose Input/Output (GPIO)

# Pin vs. Port vs. Channel

* **Pin** - Represents a physical connection point on a device.
* **Port** - Represents the underlying IO feature that allows communication.
* **ChannelInfo** - Describes the capabilities of a particular port.



Can interrogate the capabilities of a pin via the channel interface:

```
var maxFreq = PwmPin.MaximimumFrequency;
```


Can get the underlying channel info from a port:

```
var minFreq = PwmPort.ChannelInfo.MaximumFrequency;
```