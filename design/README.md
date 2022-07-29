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

 