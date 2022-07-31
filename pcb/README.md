# Concept change
- Enclosure(same pcb size) 1455K1202 120x78x43  1455J1201 120x78x27    27mm for single GNSS 43mm with space for DGNSS.     
- No HM-19 Bluetooth. Hard to get and not everyone is happy with the functionality HM-19. Wifi instead of bluetooth? A TCP or UDP connection to XCSOAR is easy.
- Alternative ESP32-WROOM-32U with external Antenna for 2.4Ghz / Bluetooth. Connected via several UARTs, Could even be used to flash the 
  STM32F4 via WIFI! => Connect STM32 UART, Boot-0 and Reset for Bootloader flashing? Attention: 400mA peak consumption ESP32 in Wifi Mode. Additional UART USB Adapter for ESP32 flashing or rely on WIFI flashing?
  Example for WIFI / TCP: https://github.com/AlphaLima/ESP32-Serial-Bridge Connection of two smartphones simultaneously in a double seater possible. 
- Redesigned 3.3VA supply. 3.3VA AM1117 maximum input voltage is 15V. The safety margin is small here! 3.3VA filtering is not optimal. A 100Ohm + 220nF just at the analog voltage regulator input. 
  Is a separate analog voltage regulator mandatory or can it be replaced with a C-L-C filter?  Check https://www.youtube.com/watch?v=aVUqaB0IMh4 for 3.3VA Pi Network and Crystal
- CAN2 for update via inbuild bootloader.
- Design milled static pressure hose connector. Concept Idea: Mounting holes 4x in 11.5mm distance square on the edge so that inner hoses are only required for pitot sensing?
- U.FL for  GNSS and Wifi/BT   External SMA in enclosure.
- USB-C connectors whereever possible
- Vertical USB-C for GNSS and ESP32 somewhere on PCB: 418K2022Y40000 (safe space on edges)
- Sockets for 2 of these GNSS modules: https://www.gnss.store/gnss-gps-modules/145-elt128.html,  https://www.ardusimple.com/product/simplertk2blite/
-  More status LEDs?   GNSS-Lock, GNSS-Heading-Lock,  External temp/humidity sensor values available,  SD-logging active LED next to SD slot. Different colors?  RGB?  Or two LEDs controlled with one GPIO. High-Z both off, GND red on 3.3V Blue on.
- Select RS232 or CAN on RJ45 via solder jumpers? Either 2 CAN, 2 RS232 or 1 CAN and 1 RS232.  Not above each other as small enclosure does not fit for this. E.g. Econ Connect 3022S2   or voelkner: C045531  JLCPCB: C386762 or 
Encitech RJJS-88-144-E9H-047 RJ45 


# TODOs for hardware version 2.0
- Why does the M9N needs a separate VDD_USB supply?
- Change CAN1 to CAN2 so that the build in STM CAN-Bootloader can be used for flashing.    
- Move sd-card as far as possible to the pcb edge.
- Add text to mark default direction of flight on the pcb. 
- Fuses between RJ45 12V connections. 
- Remove one MS5611 sensor
- MS5611 do not rote between pins! Correct Layout
- Remove cheap Gyro / ACC IMU as there will e.g. be a SparkFun 9DoF IMU Breakout. Keep expensive xSense Footprint.   
- GNSS antenna connection on pcb is slightly above the critical length: https://www.youtube.com/watch?v=_Hfzq1QES-Q  Consider when changing to U.FL
- Add a switch for boot0 at the pcb edge. 
- Add one user switch at the pcb edge. 
- Add GNSS reset pullup resistor.  
- At least add a 10uF, 100nF on voltage input and after buck converters.  
- Sense supply voltage before ferit and add a slow lowpass filter.   
- Decrease testpoint size 
- Improve solderability of GNSS ground pads. 
- Detect hardware version with an adc input. Might use new GNSS-Reset or CAN2 pullup?
- Change name in schematic for gauge sensor to HSCMRRV001PG2A3 
 - Replace existing USART-3 connector with Pixhawk standard JST-GH 6 pin Connector to connect and supply simpleRTK2B+heading modules.  1: 5V_IN, 2: RX (3.3V level), 3: TX (3.3V level), 4,5: Not connected, 6: GND

## Design decisions which wont be chaged for version 2:
- RJ45 CAN does not use "one" single "twisted pair" but two in a standard patch cable.
- Any critics on the chosen 1.25mm debug connector? Shall it be changed? Alternative Debug Connector TC2030-CTX-NL-STDC14 : https://www.tag-connect.com/solutions-target-devices/arm#s0
- Shall the sd-card power supply switchable? 
- Add 27R series resistors for all sdio bus lines. 
- Alternative to reduce housing width: A second vertical pcb, soldered in a milled slot. For a second stage connectors. Or a RJ45 PCB connected via some JST connectors. <= Reliability? 
- Add a GNSS-PPS LED and connect to GPIO timer input. 

## Links to parts
4 x RJ45 https://www.mouser.de/ProductDetail/TE-Connectivity/6339167-3?qs=Il0cmQ4mt8I3NV0IIRZAEg%3D%3D  

Various JST XH Micro Mini 1.25 connectors: https://www.ebay.de/itm/JST-XH-Micro-Mini-1-25mm-Stecker-10cm-Kabel-JST-XH-Buchsen-1-25mm-1-10-Pin/392995465350?_trkparms=ispr%3D1&hash=item5b805ae886:g:1ZAAAOSwoUBfmp1f&amdata=enc%3AAQAFAAACYBaobrjLl8XobRIiIML1V4Imu%252Fn%252BzU5L90Z278x5ickkyMJZWL%252BqFSgQ3TOOe%252FNr7r2qOS6GuOucX%252FmKJNUI9VcHutHy36NIsLXoezyw8Vf4YS7lTCp4hpJ0dyfj70b0arvUZ8%252F6%252F%252B8t23GE0J0BqKRSxKIqt4a220cVN5rXpxJtLeVi%252BS%252Fj2WHuyDFQBEE7LXLkEBDf8tXkhm3%252FS%252FjrMiRt1h1s7GRJ3ieRGpQ9XCiKrlC%252BDAdz%252BfpvLqWFu0XoIHybOJEcLZ0Zg7ofVixvWHkes6G4rgErXh6tOvvn5KYmpMXHCcJMgFbkimOmspLrLgjzfiDVwSwSMmnl%252BlNQ6KOJ8DRxfJOeULGA%252F28SbDVpiBHNhEDFdDNvmSykLeWh8YoNwGUd1VbFbrMFcLz1vGiu7PH1omE7NeQN0uPOsK0L5X%252FNuwbvR%252Fh6PVlQqyMDjzKrwfmiUwaNV4sNqyqx0wApz5P%252BguSYZBBnqYpC3f5qemU5tno5w%252BD2XKi5n7zxwxkfaQpfUuHFPQVmzLI1Yp8hhFlK%252F%252BwWeSXqK6lM3fn3z1rHM33ELyaV%252BHz6rEePz45OOLEDFg%252FHSjryJ%252F14V83z92%252B3DhIPoviZUTaRLfPUIvcH4%252BqDV3q%252FQmxuoWatiIjr16LAAD8FgFQaGj23QQhcrmk2JYkNS6QIQyZw0UthVEk5TdIXixoe1rtYwC8H9K0tVcbbHBkBNSKxWYUVTeptMYoKwtFIA20hFa%252Bfu8h1Wve8kt9A0B2hy9hc6QIaqIg10IEXcN9a4yVzft1lxWOa0rgiaeIgUpkUELPMUK5m%7Ccksum%3A3929954653505376b3f25a0142d8b89a03ffd0d4e3e0%7Campid%3APL_CLK%7Cclp%3A2334524


Gauge pressure sensor: HSCMRRV001PG2A3
https://de.farnell.com/honeywell/hscmrrv001pg2a3/drucksensor-1psi-i2c-digital/dp/3439040
https://de.rs-online.com/web/p/drucksensor-ics/2269696


## JLC Partnumbers
- Micro SD slot: C114218
- USB-C PCB Edge: C167321
- USB-C Straight on PCB: C2761226
- RJ45: C86575, C86577(only plastics),  or Mouser: RJHSE-5380 (Audio HW)  check magnetic? 
- U.FL IPEX: C88373
- CH340E: C99652
- ESP32: C99652 (4MB),  C701346 (16MB)



