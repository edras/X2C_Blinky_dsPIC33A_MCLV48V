# Model based X2C Blinky demo MCLV-48V-300W and dsPIC33AK128MC106 Motor Control DIM

## 1. INTRODUCTION
This is a model based design with X2C. It is a minimalistic blinky demo code to show basic usage of the tools and the dsPIC33A MCU.
Button switches

## 2. REQUIREMENTS

### 2.2 Software Tools Used for Testing the firmware
- MPLAB® X IDE **MPLABX v6.20** 
- DFP: **dsPIC33AK-MC_DEV_DFP v1.0.33** Update process: [link](https://microchip.my.site.com/s/article/Programming-and-Debugging-the-dsPIC33A-on-MPLAB-X-IDE-v6-20-and-IPE-v6-20)
- MPLAB® XC16 Compiler **XC-DSC_3.10**
- MPLAB® PICkit™ on board 4 In-Circuit Debugger 
- Scilab v2023.1.0
- X2C v6.5.3419



### 2.3 Hardware Tools Required for the Demonstration
- MCLV-48V-300W Inverter Board [(EV18H47A)](https://www.microchip.com/en-us/development-tool/EV18H47A)
- dsPIC33AK128MC106 Motor Control Dual In-line Module [(EV68M17A)](https://www.microchip.com/en-us/development-tool/EV68M17A)
- 24V Power Supply [(AC002013)](https://www.microchipdirect.com/dev-tools/AC002013)

> **_NOTE:_**
> All items listed under the section Hardware Tools Required for the Demonstration are available at [microchip DIRECT](https://www.microchipdirect.com/)

## 3. HARDWARE SETUP
<p style='text-align: justify;'>This section describes hardware setup required for the demonstration.</p>

1. <p style='text-align: justify;'> Insert the dsPIC33AK128MC106 Motor Control DIM into the DIM Interface Connector J8 provided on the MCLV-48V-300W Inverter Board. Make sure the DIM is placed correctly and oriented before going ahead.</p>

    <p align="left">
    <img  src="images/dimconnected.PNG"></p>

2. <p style='text-align: justify;'>	Plug in the 24V power supply to connector J1 provided on the MCLV-48V-300W Inverter Board. Alternatively, the Inverter Board can also be powered through Connector J3.</p>
      <p align="left">
      <img  src="images/mclvpower.png"></p>

3. <p style='text-align: justify;'>The board has an onboard programmer ‘PICkit™ On Board (PKoB4)’ , which can be used for debugging the dsPIC33CK256MP508. To use an on-board programmer/debugger, connect a micro-USB cable between Host PC and Connector J16 provided on the MCLV-48V-300W Inverter Board.</p>

      <p align="left">
     <img  src="images/mclvpkob4.png"></p>
 

<br />

## 4. SOFTWARE SETUP AND RUN
### 4.1 Setup: MPLAB X IDE and MPLAB XC-DSC Compiler

Install MPLAB X IDE and MPLAB XC-DSC Compiler versions that support the device dsPIC33AK128MC106. 

- MPLAB X IDE installation, refer [link](https://microchipdeveloper.com/mplabx:installation)
- MPLAB XC-DSC Compiler installation steps, refer [link](https://microchipdeveloper.com/XCDSC:installation)
- Update MPLAB X programmer/debugger interface plugins and Device Firmware Packages (DFP) [link](https://microchip.my.site.com/s/article/Programming-and-Debugging-the-dsPIC33A-on-MPLAB-X-IDE-v6-20-and-IPE-v6-20)

### 4.2 RUN
1. Open the project in MPLABX, then program the device. (Make and program button)
2. LD2 should start to blink (Potentiometer sets the blinking frequency.)
3. Open scilab and navigate to X2Cscope folder, start init script or open the model
4. Start the communicator (Orange boxes inside the model)
5. Transform the model (Orange boxes inside the model)
6. Check serial settings (At the communicator window, setup tab)
7. Connect to the HW (Connection button)
8. Monitor live signals with watch and scope functionalities


## 5.0 Peripheral Connections: 

### IO
| board    | pin  | 
|:--------:|:----:| 
| SW1       |  RD9   |
| SW2	     |  RD10   |
| POT      |  AD1AN10   |
| LED1     |  RD5   |
| LED2     |  RC9   |

### UART settings: 

   **Communication**: For X2C Scope Communication currently UART is used. User needs to select the required UART instance 
   and Configure the UART.

| Baudrate | Databits | Parity | Stopbits |
| -------- | -------- | ------ | -------- |
| 115200   | 8        | none   | 1        |

    _U1RXR = 44;
    _RP43R = 9;

### Other Peripherals   

TMR1 is set to 10kHz interrupt. Model calculation is done in the T1Interrupt.