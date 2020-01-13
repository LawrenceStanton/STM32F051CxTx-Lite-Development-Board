# STM32F051C6-Lite-Development-Board
 PCB Files for a STM32F051 Lightweight Development Board

## Contents
1. Altium Designer PCB files.
2. Summary PDF Document (Schematics, PCB Outline)

## Instructions for Use

The board is intended to be used as a standlone MCU or to be connected to breadboard circuitry via jumper (dupont) wires and the available pin headers.

### Critical Components
The following components are critical for operation:

1. USB2.0 Type B Connector
2. ST-Link V2 Debogger Module
3. MCP1700 LDO Regulator
4. 1uF Regulator Capacitors

### Decoupling Capacitors
The STM32F051 requires decoupling capacitors for smooth operation. Failure to populate these capacitors may result in watchdog lockup.

The recommended decupling capacitor values are 100nF on each of the three power inputs. VBAT does not require a decoupling capacitor. The Analogue Power Supply may demand greater capacitence for high switching useage of the analogue domain devices (particularly the DAC) and ST recommends up to 4,7uF on C3.

### Optional Crystal Resonator
The crystal oscilator circuit is provided as this is a hard circuit to import from a breadboard. The STM32F051 can operate with varying input frequency so long as the HSE oscillator is enabled with the correct frequency settings. The recommended frequecy is 8MHz.

The recommended load capacitors for a typical 8MHz crystal is 10pF, however it is the users responcibility to check with the crystal's specifications to ensure good oscillation.

No biasing capacitor is required. The STM32F051 provides this internally.

### SWD Header
The SWD header is provided for easy connection to an embedded STM32F051 in typically a THT perfboard. This allows the user to program the removed target without having to embed the debogger and USB connection onto the perfboard. This simplifies the design  of the perfboard and protects the user's PC.

To use the SWD header, simply place a 4-pin header on the target board in a similar position as the development board's SWD header. Simply route the connections to the relavent SWDAT, SWCLK, and NSRT pins, plus ground, as labeled.

It is critically impartant to use a good cable for this conection. Normal jumper wires may result in errors while flashing the MCU. Please ensure Flach Checking is enabled by your debug configuration and consider using a sheilded cable. 

### Power Protection
The MCP1700 provided avercurrent foldback protection at approximately 450mA, which is below the USB ports specified 500mA minimum drawable current, and will protect the PC from short circuits downstream. However, it is critical then that the MCP1700 is not destroyed. The MCP1700 is known to fail by shorting input to ground if its output is pulled above the input. Please ensure then that the "3V3" pins are never subjected to more than 5V.

Please consider power limitations if your USB port is being split between several devices.

Otherwise please ensure that the 5V input regulating capacitor is high quality to prevent s short through this device.

The Author is not responcible for any damage or harm caused whatsoever as a result of this board or its assocuiated desig documentation.
