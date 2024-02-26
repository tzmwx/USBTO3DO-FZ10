# USBTO3DO-FZ10

This is translation from the original repo by tzmwx.

This is an expansion of Francois CARON's SATATO3DO project https://github.com/FCare/SataTo3DO. It uses integrated circuits to reduce the size and expand it to Panasonic FZ-10. Please refer to its plan for specific usage methods.

---
## Note on UF2 files

Regarding UF2 files, please note that the source code of this build has been updated. Do not use compiled UF2 files directly.

How to obtain a UF2 file that can be used:
- Method 1: Please recompile the source file yourself to obtain a new UF2 file.
- Method 2: Authorized by Francois CARON, if you only make it for yourself and not for commercial use, you can contact tzmwx to get a copy. Special @TZMWXdiyer gets new UF2 files. Please do not bother Mr. Francois CARON with any further emails.

---
## BOM

### Minimum system
- U1 RP2040 PICO module (see [2040pico.jpg](2040pico/2040pico.jpg) for compatible pin functions)
- U2/U3 TXS0108EPWR TSSOP-20
- U4 74LVC4245 TSSOP-24

### Disk changing function
If you want to build a disk changing function on the module, you need to add:
- a 6X6mm button switch
- an R2 4.7K (SMD0603 or direct plug)

### CD cover switch function
If you want to build a CD cover switch function on the module, you need to add:
- R2 4.7K
- R3 10K
- Q1 9014 (or other NPN transistor) (SMD0603 or direct plug)

### Disk reading light
If you want to create a disk reading light on the module (same as the green disk reading light on the host panel), you need to add:
- R1: 470Ω
- LED: 3MM (SMD0603 or direct plug)

The position of the capacitor is reserved and does not need to be installed.
- C1/C2: 220uf-470uf/10V (direct plug)
- C3/C4/C5/C6/C7: 0.1uf (SMD0603)

X1, active crystal oscillator OSC SMD7050 33.86Mhz, is reserved. It only needs to be installed when you do not pick up IC640 but remove IC640, and then connect CLK to the motherboard L643. But if you need to use the function of playing music CD, you must install this OSC, otherwise the music CD will freeze once in the time period of 3:00-3:15, and then the volume bar will freeze, and the game controller will slowly stop working. For details, please refer to the information in the AUDIOCD directory.

READ disk reading light interface, connect to Q410 as shown in the figure

COVER optical drive cover induction interface, connect to SW721 as shown in the figure, you need to add R2 4.7K, R3 10K, Q1 9014 (or other NPN transistor), use the switch CD compartment cover to realize the disc changing function

The DISC interface is a parallel connection of the disc change keys. If you don't like the CD hatch mode, you can add a button switch.

The (+5V, D-, D+, GND) interface can extend the USB without using the C extension cable. Note that this interface must be welded to the 2040 module at the bottom in advance.

---
## Fixation

Regarding fixation: There are a total of 5 vias ABCDE on the PCB (refer [here](install/step2.jpg) for details). They are used to fix the motherboard. When your 3DO motherboard is MODEL A (CLIO CPU), please pay attention to the possibility of D vias. It will affect the plugging and unplugging of TYPE-C cable, so it is necessary to increase the thickness of 1-1.5 mm between the RP2040 module and the PCB.

Note: For your more convenient DIY, some component soldering positions are designed with two modes: SMD and direct plug. If you use "direct plug" components, please pay attention to the flatness of the back of the PCB, especially the 6x6 button switch, it is best to use SMD, otherwise the pins will touch IC640, making the PCB installation uneven.