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
- cut off femal end of power cable and expose 6 inches or so of wire
- wire green ground wire from electrical cord to green ground screw on electrical outlet
- wire white neutral wire from electrical cord to white neutral side of electrical outlet
- wire black hot wire from electrical outlet to center post on relay
