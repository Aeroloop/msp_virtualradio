#Radio Receiver Emulator

This project is a radio receiver emulation to be used to connect a radio
controller to SITL flight controller. 
This code originates from
[cs8425](https://gist.github.com/cs8425/51893e2f90812aa3831558503597fa1a) and
will provide a baseline implementation moving forward. At the core it seems this
has been pulled from the Betaflight Configurator.

# Pre-requirsts
1. Clone Betaflight and compile for SITL, make TARGET=SITL
2. Install NodeJS version > 8

# Configuration
 
By default Betaflight SITL opens a TCP port 5761 which can be used to connect with the
configurator. The first time you run betaflight_SITL.elf an eeprom.bin file is created  in the directory in which the executable is run. As you make modifications and save in the Configurator this bin will be updated. Be careful as it has been found some modifications will cause a Seg Fault. If this occurs delete your bin file and start over.

Before your radio can be connected to the Betaflight FC you must enable a second
UART port.
1. Start Betaflight SITL
1. Launch the configurator 
2. Select 'Manual Selection' enter tcp://localhost:5761 for the Port and click
   Connect.
3. Select the Ports tab
4. Enable UART2 for Configuration/MSP, Save and Reboot. Note this will stop
   betaflight_SITL.elf from executing. 



## Channel Input Configuration
Ensure your controller is mapped to the correct inputs. 
1. Start Betaflight SITL
2. Click the Receiver tab
3. On your radio create a new model
3. Ensure your inputs match those in the receiver tab. You may have to change
   your input (Page 5 on Taranis) and mixer (Page 6 on Taranis) on your radio to
AETR1234 for this to work.

## Setup modes
Now that your radio is connected add your flight modes.


1. Start Betaflight SITL
2. Click the Modes tab
3. At a minimum map an Aux input to Arm.
