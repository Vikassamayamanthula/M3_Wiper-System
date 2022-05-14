# About Programming
The complete procedure of writing, compiling and testing the user program can be done in a set of
programs called the development suite.
The following files to create the machine code for the microcontroller:
* The user program, a text file written in “C” language.
* The file “startup_stm32f4xx.s”, a text file written in assembly language; this file contains
instructions for the initial set-up of the microcontroller (stack, program counter, interrupt
vector table, initial system clock …; the description of the file is given in its header).
* The file “system_stm32f4xx.c”, a text file written in “C”; this file contains functions for the
detailed microcontroller set-up (system clock, clock distribution …; the description of this file is
given in its header).

In our case the file may have different names; since the file contains clock configuration
commands it is best to prepare several files in advance, each for a different configuration of the
clock and then simply include in the process of compiling the file that corresponds to the
current needs. We will run the microcontroller at its maximum speed, and the corresponding
file is named “system_stm32f4xx_CLK168_HSE8.c”.

* The header file “stm32f4xx.h”; this file defines processor used, names the registers and bits
inside the STM32F4xx microcontroller, and defines some register structures. This is the only
file that must be included from the user program in the process of compilation. The file has
been modified from the original (obtained from the ST site):
           * by uncommenting the line 68 (select the microcontroller STM32F40xx by default),
           * by uncommenting the line 88 (allow the use of standard peripheral driver) and
           * by changing the HSE frequency in line 100 
* The header file “system_stm32f4xx.h”; allows the definition of some stuff for the use of CMSIS.
* The header file “stm32F4xx_conf.h”; defines and includes some files mandatory for the project.

The header file defines the data structures used in
accessing the peripheral and names the registers and
constants (“stm32f4xx_$$$$.h”).

-The source file contains the actual functions to access
the registers responsible for the behavior of
peripherals (“stm32f4xx_$$$$.c”).
## Struct
A structure is used to store the different types of data and every data (structure member) has own independent memory that means we can access any member anytime.
Syntax of structure in C:

struct [name of structure] {member-list };

We cannot initialize the member of the structure at the time of the structure declaration because there is no memory is allocated to the members at the time of declaration.

struct MyData

{
     
     int Age;
     
     float fees;
     
    char name[4];
    
} data;

### Example
typedef struct
{

  uint32_t GPIO_Pin;
  
  GPIOMode_TypeDef GPIO_Mode;
  
  GPIOSpeed_TypeDef GPIO_Speed;
  
  GPIOOType_TypeDef GPIO_OType;
  
  GPIOPuPd_TypeDef GPIO_PuPd;
  
}GPIO_InitTypeDef;

EX:

static struct platform_driver leds_platform_driver = {

  .driver = {
  
    .name = "imx6ul-led",
    
    .of_match_table = leds_of_match,
    
  },
  
  .probe = leds_probe,
  
  .remove = leds_remove,
  
};
# enum Keyword
The enum is nothing but enemuration.In which the values of some data are often limited and can only be a very small number of integers, and it is best to take a name for each value to facilitate its use in subsequent codes.

enum week a, b, c;

Typedef enum

### Example
enum week{

  Mon,
  
  Tues,
  
  Wed,
  
  Thurs,
  
  Fri,
  
  Sat,
  
  Sun
  
};
## Functions
A function is a group of statements that together perform a task.
Every C program has at least one function, which is main(), and all the most trivial programs can define additional functions. 
You can divide up your code into separate functions.

* Avoid repetition of codes. 
* Increases program readability. 
* Divide a complex problem into simpler ones. 
* Reduces chances of error. 
* Modifying a program becomes easier by using function.
## Macros
The macros are for port and pin read and write.A macro is a piece of code in a program that is replaced by the value of the macro. Macro is defined by #define directive. Whenever a macro name is encountered by the compiler, it replaces the name with the definition of the macro.

#define Mon 1
#define Tues 2
#define Wed 3
#define Thurs 4
#define Fri 5
#define Sat 6
#define Sun 7

### Example
#ifndef PINOUT_BLUE_PILL_H

#define PINOUT_BLUE_PILL_H

#define SIZE_OF_PIN                 (sizeof(pin_t))
                                   
#define PIN_BLUE_PILL_PA0           ((pin_t const){GPIOA, 0U})
#define PIN_BLUE_PILL_PA1           ((pin_t const){GPIOA, 1U})
                                   
...                                 

#define PIN_BLUE_PILL_WKUP                (PIN_BLUE_PILL_PA0)

#define PIN_BLUE_PILL_USART2_CTS          (PIN_BLUE_PILL_PA0)

#define PIN_BLUE_PILL_ADC12_IN0           (PIN_BLUE_PILL_PA0)

#define PIN_BLUE_PILL_TIM2_CH1_ETR        (PIN_BLUE_PILL_PA1)

#define PIN_BLUE_PILL_USART2_RTS          (PIN_BLUE_PILL_PA1)

#define PIN_BLUE_PILL_TIM2_CH2            (PIN_BLUE_PILL_PA1)

...

#endif  // PINOUT_BLUE_PILL_H
## Loops
Loop is used to execute the block of code several times according to the condition given in the loop. 
It means it executes the same code multiple times so it saves code and also helps to traverse the elements of an array.
* For Loop
* While Loop

Ex: delay(10000)

# Description about Components
## STM32F4 Microcontroller
The STM32 F4-series is the first group of STM32 microcontrollers based on the ARM Cortex-M4F core. The F4-series is also the first STM32 series to have DSP and floating-point instructions. The F4 is pin-to-pin compatible with the STM32 F2-series and adds higher clock speed, 64 KB CCM static RAM, full-duplex I²S, improved real-time clock, and faster ADCs. 
* Core
* Memory
* Peripherals

![image](https://user-images.githubusercontent.com/101356849/168000036-a4acf1be-4eb8-447d-a5d3-76e4d6f15c29.png)
## LEDs
A Light Emitting Diode (LED) is a semiconductor device, which can emit light when an electric current passes through it. To do this, holes from p-type semiconductors recombine with electrons from n-type semiconductors to produce light.
## Push Button or Switch
 A Push Button switch is a type of switch which consists of a simple electric mechanism or air switch mechanism to turn something on or off. Depending on model they could operate with momentary or latching action function. The button itself is usually constructed of a strong durable material such as metal or plastic.
  ![image](https://user-images.githubusercontent.com/101356849/168000228-7dd21e85-3560-4977-b40d-7d1a8e66a200.png)
                
 ![image](https://user-images.githubusercontent.com/101356849/168000259-076d8ae7-3d78-42c0-b429-fd04cbe520bf.png)
 ## Timer
 The timer circuit is basically implemented ton introduce delay that is delay(5000).A timer is a specialized type of clock which is used to measure time intervals. A timer that counts from zero upwards for measuring time elapsed is often called a stopwatch. 
 It is a device that counts down from a specified time interval and used to generate a time delay, for example, an hourglass is a timer.
 ## Software
 QEMU is a machine emulator that can run operating systems and programs for one machine on a different machine. Mostly it is not used as emulator but as Virtualizer in collaboration with KVM kernel components. In that case it utilizes the virtualization technology of the hardware to virtualize guests.
While Qemu has a command line interface and a monitor to interact with running guests those is rarely used that way for other means than development purposes. Libvirt provides an abstraction from specific versions and hypervisors and encapsulates some workarounds and best practices.

  


