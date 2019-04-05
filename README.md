## Context

The chosen context is the zoo, a public facility that maintains a collection of animals displayed to the public. It is a leisure space that often requires visitors to travel long distances walking to explore the establishment. The zoo offers a wheelchair service for visitors with walking difficulties. This smart wheelchair can sense if the user gets tired and can signal this to the user and bypassers. This way someone can maybe help the user a little by pushing. This is done by sensing the distance that someone covered, and whether the user is being pushed whilst doing this. When the wheelchair senses that the user is tired, a vibrating motor will let him know, and lit up leds on the handles of the wheelchair will make bypassers aware.

## Sensors

|Sensor|Variable|Usage|
|---|---|---|
|Orientation sensor|Rotation|Measures the amount of rotations made in order to know the total covered distance by the wheelchair|
|Proximity sensor|Distance|To know if the wheelchair is being pushed, we check if there is someone behind the wheelchair using the proximity sensor|

## Actuators

|Actuator|What it shows|Explanation|
|---|---|---|
|LED|Tiredness|Through LEDS on the handles the wheelchair will let bypassers know that the user could use some help since he is tired|
|Vibrating motor|Tiredness|The vibrating motors is a way of telling the user he should take a break, since he cannot see the LEDS|

## Used files

dcd-hub.py: 
This code is used to test whether the pi has a successful connection with the cloud.

serial_to_dcdhub.py:
This code is used to establish a connection between the dcd-hub and the pi. In order to do this it needs a thing-id and thing-token to access the dcd-hub. The data that is send through this connection will then be readable in grafana. 

Serial_command.py:
Used to send a command from the pi to the arduino through a serial port. 

.env:
To give this thing-id and token to the pi, a .env file which contains this data is uploaded. Since this file starts with a dot means that it is a hidden file. 

Subscribe_gatt_proximity_rotation.py:
This code is used to subscribe the pi to the Blue feather. The pi will read the data that the feather is gathering through its attached sensors and sends it to the cloud, in order to read the data in grafana. 

Led_actuators.ino:
Code that is being uploaded on the arduino and can read the signal that comes in from the pi. based on this signal being a 1 or a 0 it will light up the led strips in yellow or in green. when the ledstrips are yellow it will also enable the vibrating motors briefly. 


![IoT1 Exhibition](/docs/workshops/images/iot1_exhibition.jpg)

## Workshops

* [Getting started](/docs/workshops/GettingStarted.md)
* [Workshop 1: Building an Internet-Connected Wheelchair](/docs/workshops/Workshop1.md)
* [Workshop 2: Integrating and Visualising Sensor-Based Data](/docs/workshops/Workshop2.md)
* [Workshop 3: Developing Algorithms and Controlling Actuators](/docs/workshops/Workshop3.md)
* [Workshop 4: Developing and Conducting a Data Collection Campaign](/docs/workshops/Workshop4.md)
* [Workshop 5: Implementing a Machine Learning Pipeline](/docs/workshops/Workshop5.md)
* [Workshop 6: Developing a Product Analytics Dashboard](/docs/workshops/Workshop6.md)

## Resources

* This platform uses two programming languages, Python on computers and C on
micro-controllers. While descriptions and examples of code should help you
get started, you can find some additional resources
[here](/docs/resources/software.md "Python and C resources").

* Documentation of your project is key,
[here are some tips and examples](/docs/resources/documentation.md "Documentation tips and examples").

* [Git manipulation such as Pull Request](/docs/resources/git.md "Git manipulation").

## Main Components

__**Disclaimer:**__ the design of this platform focuses on flexibility and
technology exploration rather than optimisation.

The main design includes a Raspberry Pi 3 and an Arduino Mega 2560 on the wheelchair frame.

The Arduino Mega is the micro-controller of the platform. Fixed on the main frame of the wheelchair,
it can collect data from sensors (e.g. force sensors, accelerometers), and trigger actions from actuators
(e.g. LEDs, vibration motors).

More on the Arduino Mega can be found [here](https://github.com/datacentricdesign/wheelchair-design-platform/tree/examples/arduino "Arduino resources").

Raspberry Pi is a small computer. It is also fixed to the main frame of the wheelchair,
where it can:
* interact with the Arduino Mega via USB to receive data and transmit commands;
* interact with the Internet to transmit commands and receive data;
* store data locally in files;
* run (machine learning) algorithms.

More on the Raspberry Pi can be found [here](https://github.com/datacentricdesign/wheelchair-design-platform/tree/examples/raspberrypi "Raspberry Pi resources").

These components fit together as shown on the following diagram. A large powerbank
powers the Raspberry Pi. The Arduino Mega communicates and receives power from the
Raspberry Pi via USB. A Feather (Arduino-like development board) on the wheel connects to
the Raspberry Pi via Bluetooth to sense and actuate from the wheel.

![Main Wheelchair components](/docs/workshops/images/wheechair-components.png)

## List of suggested components:

On the frame:

* 1 Raspberry Pi 3B;
* 1 SD card (Some come directly with NOOBS installed);
* 1 Arduino Mega;
* 1 Large power bank;
* 1 large breadboard;
* 1 USB cable A/micro (Powerbank to Raspberry Pi);
* 1 USB cable A/B (Raspberry Pi to Arduino Mega).

On the wheel:

* 1 Feather (Bluetooth enabled);
* 1 small power bank;
* 1 small breadboard;
* 1 USB cable A/B (power bank to Arduino Uno).


## Contact and Existing projects

Feel free to contact us at jacky@datacentricdesign.org. We welcome feedback, pull requests
or links to your project.

