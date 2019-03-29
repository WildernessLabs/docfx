# Deploy a Meadow test App

To verify that your Meadow OS is installed correctly and everything is setup, you should deploy a known working test app. We've provided an app that controls Meadow's onboard RGB led.

The steps in this guide have been tested on Ubunutu 18.10 and should work on any current version of Ubunutu or Debian.

To deploy an app to Meadow you'll need several things:

1. A copy of [mscorlib.dll](http://downloads.wildernesslabs.co/Meadow_Beta/binaries/mscorlib.dll)
1. A copy of [Meadow.Core.dll](http://downloads.wildernesslabs.co/Meadow_Beta/meadow.core.dll)
1. A .NET 4.7.1 console application that references Meadow.Core.dll (your app) - to validate your setup, you can download the provided sample [app.exe](http://downloads.wildernesslabs.co/Meadow_Beta/app.exe)

## Setup

1. Follow the steps in the [Setup](/guides/Getting_Started/Setup/index.html) 
1. Open the terminal


## Prepare your app for deployment
1. Copy the provided **app.exe**, **Meadow.Core.dll**, and **mscorlib.dll** into into the **/tmp** root folder on your Linux PC. 
 * [Meadow.Core.dll](http://downloads.wildernesslabs.co/Meadow_Beta/Meadow.Core.dll)
 * [Sample App](http://downloads.wildernesslabs.co/Meadow_Beta/app.exe)
 * [mscorlib.dll](http://downloads.wildernesslabs.co/Meadow_Beta/binaries/mscorlib.dll)

## Compile ST-Util
You'll need to download the source code and compile a customized version the software used to communicate the ST-Link V2 USB device.

### Setup
You'll need several packages installed to compile ST-Util.
To install, call `apt-get install` followed by the package name.

Open the terminal and enter the following commands to install each package:
* `sudo apt-get install libusb-1.0.0`
* `sudo apt-get installgdb-multiarch`
* `sudo apt-get installmake`
* `sudo apt-get installcmake`
* `sudo apt-get installdfu-util`
* `sudo apt-get git`

### Compile ST-Link
```bash
git clone https://github.com/adrianstevens/stlink
git checkout semi
make release
```

## Connect Meadow to your PC
1. Follow this instructions to [connect your ST-Link V2 to Meadow](/guides/Getting_Started/Setup/stlink/index.html)
* Insert your ST-Link V2 into a free USB port on your host PC
* Open the terminal
* Navigate to the folder where you compliled ST-Link
* Start st-util using the following command - you should see **Listening at \*:4242...** (the **&** is used to run the script in the background)
```bash
.stlink/build/Release/src/gdbserver/st-util --semihosting -v -m 
```

## Start the application
1. Open a second terminal
1. Enter `gdb` to start a gdb debug session (no debug symbols are currently available)
1. From the gdb prompt, enter `target remote :4242`
1. Enter `c` to start the application

The application may take several minutes to deploy. You'll see periods appear in the terminal indicating progress. Once the app is fully deployed, it will start running on Meadow. Any *console.WriteLine* commands will appear in the terminal.

If you ran the provided sample app, you should see the RGB led changing color!

## Stop the application
1. Press control-C to stop debugging
1. Enter `quit` to close gdb
1. st-util will continue listening on port 4242 - you can now update the application in the tmp folder and start restart gdp to deploy your new or updated app

## [Next - Hello, World](/guides/Getting_Started/Hello_World/index.html)