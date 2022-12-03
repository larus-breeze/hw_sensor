# Concept change
- Enclosure change: 1455K1202 (120x78x43 space for DGNSS)  or 1455J1201 (120x78x27 for single GNSS)
- Replace HM-19 Bluetoothmodule with a ESP32-WROOM-32U with external Antenna. Could even be used to flash the STM32F4 via WIFI. Connect STM32 UART, Boot-0 and Reset for Wifi flashing option. Attention: 400mA peak consumption in Wifi Mode. Example for WIFI / TCP: https://github.com/AlphaLima/ESP32-Serial-Bridge Connection of two smartphones simultaneously in a double seater is possible. 
- Design milled static pressure hose connector. Concept Idea: Mounting holes 4x in 11.5mm distance square on the edge so that inner hoses are only required for pitot sensing?
- U.FL for GNSS and Wifi/BT via external SMA-Pigtails.
- USB-C connectors whereever possible. Vertical USB-C for GNSS somewhere on PCB
- 2 RJ45 connectors. 1 for CAN/RS232 (selectable) 1 for RS232 
- Redesigned 3.3VA supply with capacity multiplier and filtering.

# TODOs for hardware version 2.0
- Add text (plane symbol) to mark default direction of flight on the pcb. 
- Add feedthrough capacitors for i2c connectors
- Routing on Layer 4 to IMU? Does this make sense as close coppling to the 3.3VA layer.
- RJ45 not in stock at JLCPCB find alternative.

## Done
- DONE: Larus Symbol on PCB
- DONE: Separate Shield GND around the PCB connected with one ferrit to GND.
- DONE: Thermal reliefs on copper fills. 
- DONE: Added 3 mounting holes 0.8inch distance for sparkfun headers
- DONE: MS5611 no routing not between pins!
- DONE: Active current limiting of GNSS antenna feed with C8542 cuircuit taken from https://content.u-blox.com/sites/default/files/ZED-F9P_IntegrationManual_UBX-18010802.pdf
- DONE: Added a LED to 3.3VA
- DONE: ESD-diodes at voltage supply input and GNSS antenna.
- DONE: changed ptc fuse with a suitable current 
- DONE: Change RJ45 CAN pinout so that a real twisted pair is used.
- DONE: Replace the diodes with a lower forward voltage ones.
- DONE: Boost Converter to Boost USB Voltage: TPS61170DRVR Inductors: 10uH 1.5A: C340393, 
- DONE: Move sd-card as far as possible to the pcb edge.
- DONE: Redesign 3.3VA voltage supply with a separate LDO after the 5V Buck.
- DONE: Filter C for R1 on DC-DC regulators: 15PF here: https://www.researchgate.net/figure/The-circuit-structure-of-the-MP2359-power-supply_fig24_330912026  Put a 0603 footprint. 
- DONE: Check ferrit bead current rating. Saturation!
- DONE: Remove cheap Gyro / ACC IMU as there will e.g. be a SparkFun 9DoF IMU Breakout. Keep expensive xSense Footprint.   
- DONE: Add a switch for boot0 at the pcb edge. 
- DONE: Add GNSS reset pullup resistor. 
- DONE: At least add a 10uF, 100nF on voltage input and after buck converters.
- DONE: Change name in schematic for gauge sensor to HSCMRRV001PG2A3 
- DONE: Replace existing USART-3 connector with Pixhawk standard JST-GH 6 pin Connector to connect and supply simpleRTK2B+heading modules.  1: 5V_IN, 2: RX (3.3V level), 3: TX (3.3V level), 4,5: Not connected, 6: GND
- DONE: Detect hardware version with an adc input. Might use new GNSS-Reset or CAN2 pullup? Check for missing GPS_RESET pullup to detect the first or newer version. Use ADC123_IN11 to distinguish between 2nd and future versions. 50% for 2nd version. 
- DONE: Decrease testpoint size to 1mm
- DONE: Sense supply voltage before ferit.
- DONE: Remove one MS5611 sensor
- DONE: change RJ45 connectors
- DONE: u.fl connector
- DONE: status led name labeling
- DONE: Connect differential pressure supply to analog voltage and beautify schematic symbol. 
- DONE: Connect USB, RJ45 schields and aluminium enclosure together (Shield_GND). Connect Shield_GND with ferrit to GND. 
- DONE: Connect aluminium enclosure on one side to the PCB.
- DONE: 7x C77096 (4.7u 1206 Package) on the input side of the Buck Converter. Remove 10uF and 22uF. 
- DONE: Adjust R28 1k 5V Supply LED resistor.
- DONE: Add ESP protection for CH340E USB connection
- DONE: Add solder jumper (default closed) on CH340 TXD pin.   (Default shall be the USB connection) 
- DONE: GNSS antenna connection on pcb is slightly above the critical length: https://www.youtube.com/watch?v=_Hfzq1QES-Q  Consider when changing to U.FL


# Design decisions which wont be realized for version 2:
- User switch at the pcb edge.
- A single sepic converster e.g. LM3488 for 3... 24V input  -> 5V output
- Alternative Debug Connector TC2030-CTX-NL-STDC14 : https://www.tag-connect.com/solutions-target-devices/arm#s0
- Sd-card power supply switchable
- 27R series resistors for sdio bus lines. 
- Connect GNSS-PPS to GPIO timer input. 
- Fuses between RJ45 12V connections. 
- Change CAN1 to CAN2 so that the build in STM CAN-Bootloader can be used for flashing.
- Sockets for 2 DGNSS modules: https://www.gnss.store/gnss-gps-modules/145-elt128.html,  https://www.ardusimple.com/product/simplertk2blite/


## Links to parts
Gauge pressure sensor: HSCMRRV001PG2A3
https://de.farnell.com/honeywell/hscmrrv001pg2a3/drucksensor-1psi-i2c-digital/dp/3439040
https://de.rs-online.com/web/p/drucksensor-ics/2269696

IMU:  MTi-1
https://de.farnell.com/xsens/mti-1-0i-t/mems-modul-2-16-3-6v-lcc-28/dp/3793980?st=mti-1-0i-t

GNSS:
https://www.mouser.de/ProductDetail/u-blox/NEO-M9N-00B?qs=DPoM0jnrROVeJ6BHpcwcjw%3D%3D
