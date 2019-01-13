# octoprint controlled power relay


This guide details how you can use an inexpensive 5v relay to turn a 3d printer off automatically when a print job finishes.


## hardware reqirements
- raspberry pi
- 5v relay module
- electrical outlet
- some 24 awg wire
- 2 power cords
- soldering iron
- solder
- heatshrink
- heat source (gun, lighter, torch, whatever)


## software requirements
- a working octopi / octoprint installation
- octoprint automatic shutdown plugin
- octoprint PSU control plugin


## relay to pi wiring
- wire GPIO 14 on raspberry pi to signal pin on relay
- wire 5v on raspberry pi to positive pin on relay
- wire ground on raspberry pi to negative on relay


## relay electrical wiring
- cut off female end of power cable and expose 6 inches or so of wire
- wire green ground wire from electrical cord to green ground screw on electrical outlet
- wire white neutral wire from electrical cord to white neutral side of electrical outlet
- wire black hot wire from electrical outlet to center post on relay
- wire from relay normally open post to black hot side of electrical outlet


## software configuration
- install printer_off.py and printer_on.py scripts in /home/pi on raspberry pi
- set permissions on scripts - chmod 750 /home/pi/printer_*.py
- configure octoprint shutdown command to run /home/pi/printer_off.py - settings > pctoprint > server < system shutdown
- configure PSU control plugin to run /usr/bin/python /home/pi/printer_on.py for on system command
- configure PSU control plugin to run /usr/bin/python /home/pi/printer_off.py for off system command


## putting it all together
- plug in the male end of the power connector to an outlet
- plug the printer into the electrical outlet connected to the relay
- leave printer power supply in the on position


## note
- The PSU control plugin is not aware of an uttomatic shutdown, so when this occurs you will need to toggle the printer off (even though it is already off) in order to turn it on via the PSU control button.
- Use the PSU control button in octoprint to turn printer on / off


## scripts
- [printer on script](scripts/printer_on.py)
- [printer off script](scripts/printer_off.py)


## images
