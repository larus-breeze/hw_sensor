# TODOs for hardware version 2.0

- Design a milled part for static preassure hose connection. This part shall be attached with screws to the pcb.  
- Remove one of the two RJ45 RS232 connectors.
- Are the two RJ45 CAN connectors still required? 
- RJ45 CAN does not use "one" single "twisted pair" but two in a standard patch cable.
- Change CAN1 to CAN2 so that the build in STM CAN-Bootloader can be used for flashing.    
- Move sd-card socket / bluetooth module to bottom side for a smaller size. 

- PCB cutout below the bluetooth antenna?
- Evaluate other bluetooth modules. Not everyone is happy with the HM-19. http://www.jnhuamao.cn/bluetooth.asp,  https://www.digikey.de/htmldatasheets/production/2935202/0/0/1/bt832a.html#pf5:
- Bluetooth for LongRange and Speed: Use 10uF or 47uF capcacity on module VCC pin.
- Wifi instead of bluetooth?  A TCP or UDP connection to XCSOAR is easy. 
- Add text to mark default direction of flight on the pcb. 
- Shall the CAN bus be able to go to sleep and disable the power supply? 
- Fuses between RJ45 12V connections. 
- Remove one MS5611 sensor
- MS5611 do not rote between pins! Correct Layout
- Remove cheap or expensive IMU sensors depending on which are required. 
- FXOS8700  solder mask gaps must be > 0.2mm! Increase pad gaps.  
- GNSS antenna connection on pcb is slightly above the critical length: https://www.youtube.com/watch?v=_Hfzq1QES-Q  Add cutout for SMA Connector.
- Add a GNSS-PPS LED and connect to GPIO timer input. 
- Change to USB-C connectors and increase spacing between connectors. 
- Add a switch for boot0 at the pcb edge. 
- Any critics on the chosen 1.25mm debug connector? Shall it be changed? 
- Add GNSS reset pullup resistor.  
- 3.3VA AM1117 maximum input voltage is 15V. The safety margin is small here! 
- 3.3VA filtering is not optimal. Redesign analog voltage supply. E.g. 100Ohm + 220nF just at the analog voltage regulator input.
- At least add a 10uF, 100nF on voltage input and after buck converters.  
- Is a separate analog voltage regulator mandatory or can it be replaced with a C-L-C filter. 
- Sense supply voltage before ferit and add a slow lowpass filter.   
- Add 27R series resistors for all sdio bus lines. 
- Shall the sd-card power supply switchable? 
- Decread testpoint size 
- Improve solderability of GNSS ground pads. 
- Detect hardware version with an adc input. 


## Links to parts

4 x RJ45 https://www.mouser.de/ProductDetail/TE-Connectivity/6339167-3?qs=Il0cmQ4mt8I3NV0IIRZAEg%3D%3D  

Various JST XH Micro Mini 1.25 connectors: https://www.ebay.de/itm/JST-XH-Micro-Mini-1-25mm-Stecker-10cm-Kabel-JST-XH-Buchsen-1-25mm-1-10-Pin/392995465350?_trkparms=ispr%3D1&hash=item5b805ae886:g:1ZAAAOSwoUBfmp1f&amdata=enc%3AAQAFAAACYBaobrjLl8XobRIiIML1V4Imu%252Fn%252BzU5L90Z278x5ickkyMJZWL%252BqFSgQ3TOOe%252FNr7r2qOS6GuOucX%252FmKJNUI9VcHutHy36NIsLXoezyw8Vf4YS7lTCp4hpJ0dyfj70b0arvUZ8%252F6%252F%252B8t23GE0J0BqKRSxKIqt4a220cVN5rXpxJtLeVi%252BS%252Fj2WHuyDFQBEE7LXLkEBDf8tXkhm3%252FS%252FjrMiRt1h1s7GRJ3ieRGpQ9XCiKrlC%252BDAdz%252BfpvLqWFu0XoIHybOJEcLZ0Zg7ofVixvWHkes6G4rgErXh6tOvvn5KYmpMXHCcJMgFbkimOmspLrLgjzfiDVwSwSMmnl%252BlNQ6KOJ8DRxfJOeULGA%252F28SbDVpiBHNhEDFdDNvmSykLeWh8YoNwGUd1VbFbrMFcLz1vGiu7PH1omE7NeQN0uPOsK0L5X%252FNuwbvR%252Fh6PVlQqyMDjzKrwfmiUwaNV4sNqyqx0wApz5P%252BguSYZBBnqYpC3f5qemU5tno5w%252BD2XKi5n7zxwxkfaQpfUuHFPQVmzLI1Yp8hhFlK%252F%252BwWeSXqK6lM3fn3z1rHM33ELyaV%252BHz6rEePz45OOLEDFg%252FHSjryJ%252F14V83z92%252B3DhIPoviZUTaRLfPUIvcH4%252BqDV3q%252FQmxuoWatiIjr16LAAD8FgFQaGj23QQhcrmk2JYkNS6QIQyZw0UthVEk5TdIXixoe1rtYwC8H9K0tVcbbHBkBNSKxWYUVTeptMYoKwtFIA20hFa%252Bfu8h1Wve8kt9A0B2hy9hc6QIaqIg10IEXcN9a4yVzft1lxWOa0rgiaeIgUpkUELPMUK5m%7Ccksum%3A3929954653505376b3f25a0142d8b89a03ffd0d4e3e0%7Campid%3APL_CLK%7Cclp%3A2334524

HM-19 Bluetooth Module: https://de.aliexpress.com/item/4000505501370.html?spm=a2g0s.9042311.0.0.50ed4c4dkdHVZQ

Differenzdrucksensor:
https://www.mouser.de/ProductDetail/Honeywell/HSCMRRV001PD2A3/?qs=%2Fha2pyFaduieLcp1Pvp%2FRRfdknh89kZ7vIF9%252BBlvZnfwJRDm%2F5m%252B3MtxuLhuUN1P


