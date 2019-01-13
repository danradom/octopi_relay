# octoprint controlled power relay


This guide details how you can use an inexpensive 5v relay to turn a 3d printer off automatically when a print job finishes.


## hardware reqirements
- [raspberry pi](https://www.amazon.com/ELEMENT-Element14-Raspberry-Pi-Motherboard/dp/B07BDR5PDW/)
- [5v relay module](https://www.amazon.com/Tolako-Arduino-Indicator-Channel-Official/dp/B00VRUAHLE/)
- [electrical outlet](https://www.amazon.com/Leviton-W5320-T0W-Resistant-Receptacle-Grounding/dp/B002DQT5UK/)
- [24 awg wire](https://www.amazon.com/Houseables-Electrical-Electric-Assortment-Electronic/dp/B07CZT26DM/)
- [2 power cords](https://www.amazon.com/Cable-Matters-2-Pack-Heavy-Extension/dp/B0153T1LSM/)
- soldering iron
- solder
- heatshrink
- heat source (gun, lighter, torch, whatever)


## software requirements
- [working octopi / octoprint installation](https://octoprint.org/download/)
- [octoprint automatic shutdown plugin](https://plugins.octoprint.org/plugins/automaticshutdown/)
- [octoprint PSU control plugin](https://plugins.octoprint.org/plugins/psucontrol/)


## relay to pi wiring
- connect GPIO 14 on raspberry pi to signal pin on relay
- connect GPIO 5v on raspberry pi to positive pin on relay
- connect GPIO ground on raspberry pi to negative on relay


## relay electrical wiring
- cut off female end of power cable and expose 6 inches or so of wire
- wire green ground wire from electrical cord to green ground screw on electrical outlet
- wire white neutral wire from electrical cord to white neutral side of electrical outlet
- wire black hot wire from electrical outlet to center post on relay
- wire from relay normally open post to black hot side of electrical outlet


## software configuration
- install printer_off.py and printer_on.py scripts in /home/pi on raspberry pi
- set permissions on scripts - chmod 750 /home/pi/printer_*.py
- configure octoprint shutdown command to run /home/pi/printer_off.py - settings > octoprint > server > system shutdown
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
- [electrical outlet part](images/outlet.jpg)
- [relay part](images/relay.jpg)
- [raspberry pi pinout](images/pi_pinout.jpg)
- [raspberry pi GPIO wiring](images/pi_wiring.jpg)
- [wired relay 1](images/relay_wired-1.jpg)
- [wired relay 2](images/relay_wired-2.jpg)
- [wired relay 3](images/relay_wired-3.jpg)
- [completed project](images/project.jpg)


## STL files
- [relay box base](stl/relay_box-base.stl)
- [relay box top](stl/relay_box-top.stl)
