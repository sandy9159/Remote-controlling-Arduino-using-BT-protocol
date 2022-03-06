# Remote-controlling-Arduino-using-BT-protocol

# ABOUT THIS PROJECT

In this project, we will use Windows Remote Arduino to turn an LED on and off. It is a simple example, but will reveal the power that the library can give you to create many more advanced projects. Let’s get started!

You can download the "samples" repository here. This sample is "RemoteBlinky" inside the appropriate platform folder, either Win10 or Win8.1. Make sure to clone the repository recursively so that you also obtain a copy of the library (more info in the readme)! The downloadable sample includes code for both USB and Bluetooth connections, while this guide mainly covers Bluetooth (with some short USB asides) since it involves extra hardware steps and is just so much more awesome.

It is also possible to connect to your Arduino through the network, but you'll require a WiFi shield or Ethernet shield. Further instructions can be found on the Windows Remote Arduino repository page, linked directly below.

If you'd prefer to create your own project, follow the project set up guide here

You can find the Windows Remote Arduino repository here


# Program the Arduino

First thing's first, let's program the Arduino. 

> Download and install the Arduino software from http://arduino.cc.

> Connect your Arduino device to the computer using USB.

> Launch the Arduino application.

> Verify that you have the correct Arduino board selected under Tools > Board

> Verify that you have the correct COM Port selected under Tools > Port

> In the Arduino IDE, navigate to File > Examples > Firmata > StandardFirmata

> Verify that StandardFirmata will use the correct baud rate for your connection. (See note on baud rate below)

> Press “Upload” to deploy the StandardFirmata sketch to the Arduino device.



# Baud Rate

 StandardFirmata uses the Serial lines to talk to a Bluetooth device or over USB. By default, it uses a baud rate of 57,600 bps. Depending on the configuration of your Bluetooth device, you may need to modify that rate. It can be found in the setup method and looks like this:

Firmata.begin(57600);

Change this value to the correct baud rate. For USB, this value is configurable on both the device and in the Windows Remote Arduino connection parameters. If you are using Bluetooth, the baud rate depends on the device you are using.



Before moving fuurther I would like to tell you something about PCB

Yes PCB are the heart of the electronics based project usually we hesitate to try custom PCB and opt to homemade solutions

like breadboard or Zero PCB earlier I also was in the same boat, I hesitate to try custom PCB my belief was they are much expensive.

but then I came to know about [JLCPCB.com](https://jlcpcb.com/IAT) and I was totally surprised how low price PCB's are they offering 
not only PCB [JLCPCB.com](https://jlcpcb.com/IAT) is one-stop service from  PCB design and PCB prototype to PCB assembly to PCB enclosures,
SMT Assembly service of [JLCPCB.com](https://jlcpcb.com/IAT) is cherry on top now get your PCB fully assembled and save our time and money
Select components for your PCB from there Parts Library of 200k+ in-stock components (689 Basic components and 200k+ Extended components)
they are offering $27 valued New User coupon  & $24 SMT coupons every month
$8.00 setup fee, and $0.0017  per joint
Now no need to order components 
separately for you PCB and get free from stress of soldering them on PCB just try PCB SMT assembly service and get you PCB with components pre assembled ready for the project
Foe more detials & offers please visit [JLCPCB.com](https://jlcpcb.com/IAT)


![image](https://user-images.githubusercontent.com/19898602/134224512-bea8d1c8-9ebe-448d-bbba-0cbecb42d528.png)![image](https://user-images.githubusercontent.com/19898602/130722585-b5268db1-5f17-428f-ba60-b823140f2a70.png)




![image](https://user-images.githubusercontent.com/19898602/156910379-64f60624-b0a7-4f0f-b7f9-5195693d074c.png)


# Hardware Set Up

You can always use a USB, WiFi, or Ethernet connection to get started, but let’s cover simple hook up of a Bluetooth device and an LED that we will turn on and off over Bluetooth using the Windows Remote Arduino library!

Connect the power and ground rails on the breadboard to the 5V and GND pins, respectively, on the Arduino. Using color coded wires (red and black) will make it easy to keep track of the power connections.


![image](https://user-images.githubusercontent.com/19898602/156910968-c9515dd1-d3d5-4194-a441-ecdbe07e22e9.png)


Plug your bluetooth device on the breadboard and connect the VCC and GND pins to the power and ground rails, respectively, on the breadboard.


![image](https://user-images.githubusercontent.com/19898602/156910980-b68d569c-2bc1-4e47-a330-e61c469441a0.png)


Connect the TX-0 pin on the bluetooth device to the RX pin on the Arduino. Similarly, connect the RX-1 pin on the bluetooth device to the TX pin on the Arduino.


![image](https://user-images.githubusercontent.com/19898602/156910993-8b6eddcb-9bfc-4714-b2d5-f22258736c05.png)


Notice the yellow wire in the image goes from the transmit pin of the bluetooth device to the receive pin of the Arduino and vice versa for the orange wire. This step is critical to establish serial communication between the bluetooth device and the Arduino, allowing the messages transmitted from one device to be received by the other.


![image](https://user-images.githubusercontent.com/19898602/156910998-afb149ea-6fbd-4f8a-81c7-d80554f6e8e4.png)



![image](https://user-images.githubusercontent.com/19898602/156911001-78d1a860-635f-43c8-9887-6f7a06e5da67.png)


Make sure that your code is already uploaded on the Arduino before making this connection. The Arduino Uno uses the same serial (TX and RX) pins for flashing the device, which prevents any code from being uploaded to it when another device is connected to these serial pins.
Add an LED to the breadboard. Note that the longer (or bent) leg is the anode (positive) and the shorter leg is the cathode (negative).


![image](https://user-images.githubusercontent.com/19898602/156911008-9620ecb2-6a33-4f2e-86bc-d33a95b451e7.png)



Connect the cathode of the LED to the ground rail of the breadboard using a 330Ω resistor. A 330Ω resistor is striped orange, orange, brown, gold as shown in the image.



Connect the cathode of the LED to the ground rail of the breadboard using a 330Ω resistor. A 330Ω resistor is striped orange, orange, brown, gold as shown in the image.


Connect the anode of the LED to any digital I/O pin on the Arduino. We are using pin 13 in the example.

![image](https://user-images.githubusercontent.com/19898602/156911017-bfd8f0e8-4048-4f05-b1f2-607c8fb16707.png)


You setup is now ready! It should look similar to the setup shown in the image below.

You setup is now ready! It should look similar to the setup shown in the image below.


# Code

Install Arduio Firmata Library:


Install Arduio Firmata Library:



Goto Sketch menu / Include Library / Manage Library and search for "Firmata" and install latest version of the library.

Now open & upload "StandardFirmata" example from File / Examples / Firmata / StandardFirmata.

It's done at Arduino side. Now we will see for Windows Universal Platform App.

Windows Universal Platform App

Download the sample repository here. If you'd prefer to create your own project, follow the project set up guide here.

Now that we’re all set up, let’s get into some code!

Create your project
I’ve set up a project called RemoteBlinky by following the steps in the setup guide. In the screenshot below, you will see the code-behind file MainPage.xaml.cs which simply creates a Bluetooth connection object and passes it to the RemoteDevice class in the constructor. You’ll see that I’ve specified my device name in this example. You may also enumerate the available devices by invoking the static .listAvailableDevicesAsync() function on BluetoothSerial (and USBSerial) class before constructing your object.



![image](https://user-images.githubusercontent.com/19898602/156911046-bb93ed00-a35d-4fde-bb47-133da79a5e38.png)


# Note for USB:

USBSerial has many options available to specify your device. In the constructor, you can provide the VID and PID of your device, the VID only, or a DeviceInformation object (obtained from the above mentioned listAvailableDevicesAsync function). Similarly, BluetoothSerial allows you to provide a device id (as a string), device name (also a string), or the DeviceInformation object.

You can obtain the VID & PID combination of your USB device by following these steps:

> Open Device Manager through the Control Panel or by pressing both Windows + Pause keys and choosing the Device Manager link on the left.

> Expand the Ports (COM & LPT) menu

> Right-click your Arduino Device and select Properties

> On the Details tab, select Hardware Ids from the drop-down menu.

> You may see multiple entries in the Value box, but any entries will have matching PID and VID.

> The entries will have the format "USB\VID_****&PID_****" where **** are the numeric ID values.

> USBSerial usb = new USBSerial( "VID_2341", "PID_0043" ); is guaranteed to work only for the following hardware device:




![image](https://user-images.githubusercontent.com/19898602/156911058-09966ae5-8e7b-4198-a255-b1eb6b33299b.png)


Next, I’m going to add a callback function to the DeviceReady event on the RemoteDevice object. This function will automatically be called when the Bluetooth device is connected and all necessary settings have been initialized. You’ll notice that I haven’t implemented anything in that function at this time. Last, call .begin() on the connection object to tell it to connect


Build and deploy! Your buttons will be enabled when the connection is established, and you can freely toggle your LED on and off at will! Here is a screenshot of this basic example running on Windows Phone 10.


![image](https://user-images.githubusercontent.com/19898602/156911074-012f66e1-0cb0-4a71-aa36-bf9127b631fd.png)


I really hope you enjoy replicating this project and using it as a baseline for an incredible new set of Maker projects!



