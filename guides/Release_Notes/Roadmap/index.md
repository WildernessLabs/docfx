# Meadow V1.0 Roadmap

The current release of Meadow is [Beta2](../Beta2/index.md)

## Current Release - Beta 2

[Beta 2 Release Notes](/guides/Release_Notes/Beta2/)

## Future

### Beta 3 - April Target

* **PWM** - Hardware Pulse-Width-Modulation (PWM) support. Currently, in beta 2 we have a low frequency SoftPwmPort that can be used to test PWM Peripherals.
* **Digital Protocols**
	* **I2C**
	* **SPI**
	* **Serial (UART)**
* **Network** - Integrated WiFi support.
* **Flash Deploy** - Command line deployment to flash, so we can remove the dependency on semihosting (in which we load the app.exe from the attached computer's `/tmp` directory).
* **IDE Plugin** - First draft of the IDE plugin which will include a default Meadow application template and some basic deployment integration.

### Release Candidate 1 - May Target

* Meadow Board in-IDE Activation
* One touch deploy
* Mono Linking?
* Bluetooth
* CAN?
