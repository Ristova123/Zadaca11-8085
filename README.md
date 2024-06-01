# Zadaca11-8085

Повеќе процесорски систем се состои од 4µP 8085А.
Едниот од нив е надреден во однос на останатите три.
Надредениот µP испраќа бајт податок кон сите µP кои потоа
истиот го обработуваат. Надредениот µP по испраќање на
податокот влегува во IDLE режим и останува 3.2 msec. Потоа
со прозивка го зема резултатот од сите 3 µP и го споредува.
Доколку сите 3 резултати се исти се пали зелено, ако се
различни се пали црвено светло. 


**Resenie:**


![Screenshot (1)](https://github.com/slavko444/8085-Zadaca-11/blob/main/Diagram%2011.1.png)

![Screenshot (2)](https://github.com/slavko444/8085-Zadaca-11/blob/main/Diagram11.2.png)
```
MOV A,M ;се чита податокот

 OUT 01h ;се праќа мна првиот микропроцесор

 OUT 04h ;се праќа мна вториот микропроцесор

 OUT 16h ;се праќа мна третиот микропроцесор

 Јамка за 3.2 msec.

 IN 02h ;по 3.2 msec се чита од првиот микропроцесор

 MOV B,A

 IN 08h ;по 3.2 msec се чита од вториот микропроцесор

 CMP B ;се споредува со податокот добиен од I микропроцесор

 JZ OK1 ;исти се!

 JMP CRVENO

 OK1: IN 20h ; се чита податокот од третиот микропроцесор

 CMP B

 JZ OK

CRVENO: MVI A,01XXXXXX ;се праќа „0“ на SOD

 SIM

 JMP KRAJ

 OK: MVI A,11XXXXXX ;се праќа „1“ на SOD

 SIM

 KRAJ: NOP

 END

```

 ![Screenshot (3)](https://github.com/slavko444/8085-Zadaca-11/blob/main/Code%2011%2C1.png)
 ![Screenshot (4)](https://github.com/slavko444/8085-Zadaca-11/blob/main/Code%2011.2.png)
 
**Develop by:**

[Tamara Ristova ](https://github.com/Ristova123)


**Subject**

Microcomputer's systems

**Built With**

This project is built using the following tools:

- [8085 simulator](https://github.com/8085simulator/8085simulator.github.io?tab=readme-ov-file): Assembler and emulator for the Intel 8085 microprocessor.

**Getting Started**

To get a local copy up and running, follow these steps.

**Prerequisites**

In order to run this project you need:

A working computer
Connection to internet
Setup

**How to Run**

To run the program, you need an 8085 emulator or assembler. You can use emulators like DOSBox or TASM (Turbo Assembler). Here's how to run the program using 8085 simulator:

1. Download and install 8085 simulator from [here](https://github.com/8085simulator/8085simulator.github.io?tab=readme-ov-file).
2. Clone this repository to your local machine.
3. Open 8085 simulator and load the `Zadaca11 code.asm` file.
4. Assemble the code by pressing the Assemble button.
5. Run the program by pressing the Run button or by pressing F10.
