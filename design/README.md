# PCB design for Vario Sensor 

## Current consumption consideration

### Measured consumption of hw version 1.0.0
- M9N GNSS active, SD-card logging active, Bluetooth connected, 
- 1.071W 85mA Peak at 12.6V supply. ~ 320mA at 3.3V
- 50mA HM-19 Bluetooth

### 3.3V Line for next hw version
- 102mA max @85°C STM32F407 
- 200mA max peak Micro SD
- 100mA peak max M9N GNSS
- 310mA ESP32 (70mA CPU, 240mA Wifi full power) 
- 33mA xSense MTi1 IMU
- 1.4mA peak MS5611
- 2.8mA peak HSCMRRN001PG2A3 absolute pressure sensing    HSCMRRD001PG2A3 (with diagnostics), HSCMRRV001PG2A3(with diagnostics and port 1 also for liquid) <= newer alternative 2022.07.26: available at Farnell and rs-online.com
- 1mA (60mA short circuit output current) RS232 Converter
- 60mA "Dominant- High Bus Load"  180mA "Dominant- Bus Fault" CAN Transceiver

Total:  810.2mA max total. 

## TPMP2359DL supply up to 1.2A continuous current should be sufficient

## Mechanical design:

### Enclosure
- Hammond Electronics 1455K1202 Enclosure 75x 120mm  PCB 74.5 x 120
- Free Space (active area on PCB) in enclosure 70 x 120  with some margin 68 x 120 mm 


## ESP32 for WIfi / BT connectivity
- GPIO16 / GPIO17 on ESP32 connected with USART2 (PA2/PA3) at 38400 baud. Flashed https://github.com/AlphaLima/ESP32-Serial-Bridge   Prototype works. Connection of two Android Smartphones with each two connenctions to a TCP socket worked. 
- Connect GPIO04 / GPIO15 on ESP with USART1 (PA9/PA10), Connect STM32F4 Reset and Boot0. 
- Add some headers for the other esp32 connectors.
- Add a reset and program (GPIO0) button. Connect GPIO1 /GPIO3 via CH340E to a USB connector.
- Connect a SPI data pump between ESP(Slave VSPI) and STM32(Master SPI2).  
Use ESP Pins: VSPI (CS:  5, CLK: 18, MOSI: 23, MISO: 19)  https://github.com/hideakitai/ESP32DMASPI  
Use STM32 Pins: CS: PB12, CLK: PB13, MOSI: PB15, MISO: PB14 ( Reuse L3GD20 interface, but provide another CS on the connector (PB0 or PB1) in case an external IMU needs SPI2)

- Where to connect the external RS232 interfaces?  XCSOAR via Wifi should be able to put data on the external RS232 line.  

