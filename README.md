# ARMv7 Processor for Logisim

ARMv7 Single-Cycle processor implementation in Logisim [[1]](#links)

![processor_main](https://user-images.githubusercontent.com/23485117/122071011-b0652680-cdf6-11eb-8b15-35859115ebd9.PNG)

## Main Features
- loadable ROM, RAM, 15 + 1 cell Register Field, ALU and Control Unit
- support for all basic arithmetic commands, memory access and basic flow control [[full list]](#supported-commands)
- conditional execution
- shifted second operant support
- fully complient to the ARMv7 specifications [[2]](#links)

## Getting Started
Download the Logisim executable from the official website. The only prerequisit is a working Java 5 or higher environment. 
After starting Logisim go to ``` File -> Open... ``` and select the .circ file from this repository. The top-level processor file called 'main' should automatically open. 

The processor ROM is by default loaded with the following short ARM 32bit programm:
```
00000000 <main>:
   0:   e3a01006        mov     r1, #6
   4:   e3a02005        mov     r2, #5
   8:   e3a04001        mov     r4, #1
   c:   e0813002        add     r3, r1, r2
  10:   e1a03083        lsl     r3, r3, #1

00000014 <loop>:
  14:   e0533004        subs    r3, r3, r4
  18:   e2855001        add     r5, r5, #1
  1c:   1afffffc        bne     14 <loop>
```

The programm can be changed by selecting the ROM element and selecting ```Contents -> (click to edit)``` from the element attributes window on the left side. The compiled machine code, for example via ```arm-linux-gnueabihf-as```, can now either be typed in by hand by clicking each singe cell or pasted in from the clipboard. Examples can be found in this repository in the folder ```../examples/```. Just use *CTRL + A* to select all instructions, copy them by *CTRL + C*, then click into the Hex-Editor window and press *CTRL + V* to past them. Rember to first clear all old instructions from the ROM has the new ones will only be pasted 'on-top'. 

The simulation can then be started by ticking  ``` Simulate -> Simulation Enabeled ``` and then run either by doing single-cycle steps with ``` Simulate -> Tick Once``` or by enabeling automatic ticking by a given frequency by selecting ```Simulate -> Ticks Enabeled```. 
While the simulation is running every component, for example ALU or Register Field but also every cable, can be inspected by using the 'Peek and Poke' tool from the upper right tool selection bar by either clicking on a cable or double-cklicking an a structure. 
## <a name = "supported-commands"></a> Supported Commands
  ### Arithmetic commands
  * AND
  * SUB
  * ADD
  * TST
  * CMP
  * CMN
  * ORR
  * MOV
  * LSL
  * LSR
  * ASR
  * MVN
  ### Memory Instructions
  * STR
  * LDR
  ### Branch Instructions
  * B
## Missing Instructions / Features
  * EOR
  * RSB
  * ADC
  * SBC
  * RSC
  * TEQ
  * RRX
  * ROR
  * BIC
  * all multiply and divide instructions
  * all special load / store instructions
  * BL
  * all misscellaneous instructions
## Acknowledgements
The processor is based on the design proposed by Harris & Harris in their book *Digital Design and Computer Architecture : ARM Edition* [[3]](#links) and the ARM material by Dr. Wolfgang Heenes [[4]](#links) was implemented at the TU Darmstadt for use in the course 'Rechnerorganisation' in the SS21. 
Feel free to use or extend this project in any non-commercial or educational project or course, but cite this project as 
> David Eckhardt. *ARMv7-Logisim*, TU Darmstadt, 2021. https://github.com/TeflonAntihaft/ARMv7-Logisim 

![processor_ALU](https://user-images.githubusercontent.com/23485117/122080893-edcdb200-cdfe-11eb-876b-b31649c388be.PNG)
![processor_register](https://user-images.githubusercontent.com/23485117/122080899-ef977580-cdfe-11eb-8c61-950d937e69da.png)

## <a name = "links"></a> Links
[1] http://www.cburch.com/logisim/de/index.html \
[2] https://developer.arm.com/documentation/ddi0406/latest/ \
[3] Harris, Sarah, and David Harris. *Digital Design and Computer Architecture : ARM Edition*, Elsevier Science & Technology, 2015. ProQuest Ebook Central, https://ebookcentral.proquest.com/lib/ulbdarmstadt/detail.action?docID=5754460. \
[4] http://www.heenes.de/ro/material/arm/arm-instructionset.pdf 
