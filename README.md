# Intro2BCI_Workshop
An Introduction to Brain Computer Interfacing in a workshop format

## Introduction

The following is a basic instructional towards integrating a simple Brain Computer Interface with external hardware.

For this workshop you will need:

### Hardware: 

- OpenBCI Bioamplifier, some examples include
    * [OpenBCI Ganglion (4 Channels)](https://docs.openbci.com/Ganglion/GanglionLanding/)
    * [OpenBCI Cyton (8 - 16 Channels)](https://docs.openbci.com/Cyton/CytonLanding/)
- Electrodes for EEG
    * [OpenBCI Ultracortex MK IV](https://docs.openbci.com/AddOns/Headwear/MarkIV/)
    * [OpenBCI Headband](https://docs.openbci.com/AddOns/Headwear/HeadBand/)
    * [Misc. Electrodes](https://docs.openbci.com/AddOns/Electrodes/ElectrodesLanding/)
- Arduino Microcontroller
    * [Arduino Uno](https://store.arduino.cc/products/arduino-uno-rev3)
    * [Arduino Nano](https://store.arduino.cc/products/arduino-nano)
- Arduino-Compatible Relay
    * [Example Relay](https://www.sparkfun.com/products/15093) 
- [Compatible Jumper Cables](https://www.amazon.com/MCIGICM-Breadboard-Jumper-Cables-Arduino/dp/B081GMJVPB/ref=asc_df_B081GMJVPB?tag=bngsmtphsnus-20&linkCode=df0&hvadid=80127030278136&hvnetw=s&hvqmt=e&hvbmt=be&hvdev=c&hvlocint=&hvlocphy=&hvtargid=pla-4583726557157680&psc=1) 

- [Lamp Base (Optional)](https://www.amazon.com/Polished-Desktop-Sockets-Replacement-Holding/dp/B0BDM3Y3S5/ref=sr_1_1_sspa?crid=RGSH59K9K3ID&keywords=lamp+base&qid=1693161128&s=industrial&sprefix=lamp+bas%2Cindustrial%2C121&sr=1-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1)

- [Lightbulb E26 (Optional)](https://www.amazon.com/s?k=lightbulb+e27+e26&i=industrial&crid=14BXHBH7BHJPS&sprefix=lightbulb+e27+e%2Cindustrial%2C1549&ref=nb_sb_noss)
    * Edison bulbs look cooler

- USB ports on your computer *or* compatible adapter to USB

## Software

- [OpenBCI GUI](https://docs.openbci.com/Software/OpenBCISoftware/GUIDocs/)
- [Arduino IDE](https://www.arduino.cc/en/software)

## Setting Up

### Setting up arduino

1. Install the required software listed above for your device version
2. Open the code located in [arduino_code/BCI_StateMachine.ino](https://github.com/Union-Neurotech/Intro2BCI_Workshop/blob/main/arduino_code/BCI_StateMachine.ino) with the Arduino IDE
3. Plug in your Arduino and upload the code. Follow [this tutorial](https://support.arduino.cc/hc/en-us/articles/4733418441116-Upload-a-sketch-in-Arduino-IDE) for troubleshooting.

### Linking hardware to arduino

1. Wire the relay up to the arduino as according to [this tutorial](https://www.makerguides.com/how-to-use-a-relay-with-arduino/). Make sure the data pin on the relay is connected to **pin 12** on the arduino.

2. Separate the cables of the lamp base. **(Exercise caution and make sure lamp base is unplugged)** Using a wire stripper, cut one of the cords and strip some of the coating so that just enough metal is exposed to attatch to the relay.

3. Wire ends of the lamp cord to the relay. One should go through **NO** for *Normally Open* and the other should be wired to **COM**.

4. **[Optional]** Wire the LED to the arduino. Make sure the jumper from **pin 3** goes to a roughly 220 Ohm resistor that connects to the positive connector for the LED. The negative end should be wired to GND on the arduino.

5. You should be able to evaluate that this setup works even without plugging in the lamp base to an outlet. This can be accomplished by uncommenting the segment under '**// For communciating over serial command using "1" and "0" as a manner of debugging functionality**' in the arduino code and commenting the lines above it underneath '**// For communicating with OpenBCI**'

### Linking to OpenBCI

1. With the arduino setup, open the OpenBCI GUI and attatch electrodes and connectors according to [the 'getting started' section of OpenBCI](https://docs.openbci.com/GettingStarted/GettingStartedLanding/) for your respective board.

2. With the OpenBCI GUI open the [focus widget](https://docs.openbci.com/Software/OpenBCISoftware/GUIWidgets/#focus-widget). Toggle it for focus by using the **Metric** dropdown. You can play around with classifiers / thresholds / windows (the amount of seconds data considered for an estimation of brain state) to see what works best. 

3. In another box of the GUI, select the dropdown and find the [**Networking Widget**](https://docs.openbci.com/Software/OpenBCISoftware/GUIWidgets/#networking). Select **Serial** and from the drop downs, select **focus** as the data type, and for the serial port select the same port that your arduino is connected to. 

    * Data is communicated according to these format guidelines (https://docs.google.com/document/d/e/2PACX-1vR_4DXPTh1nuiOwWKwIZN3NkGP3kRwpP4Hu6fQmy3jRAOaydOuEI1jket6V4V6PG4yIG15H1N7oFfdV/pub)

4. Try consciously focusing and seeing how this affects the focus widget. It may takes some tweaking of thresholds and other parameters to get a configuration that works for each user.

## Usage 

With everything linked up, ensure that:

- The lamp on the arduino setup is linked to a wall outlet with the only disconnection being the relay.
- The OpenBCI is connected to you whatever electrodes you have hooked up and is actively streaming.
- The arduino is connected to a USB port.
- A Focus Widget and Networking Widget are open and Serial is selected in the networking widget with a stream started. If the setup is connected the arduino correctly and actively streaming data, you should see a constantly blinking light on the arduino indicating it is recieving data.
- From here you should be able to properly control the state of the light bulb by concentrating!




