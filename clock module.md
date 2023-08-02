# Clock Module
## Table of Contents
1.  [Module Overview](#module-overview)
2.  [Components](#components)
3.  [Schematics](#schematics)
4.  [Working](#working)
-   [Overall Working of Clock module](#overall-working-of-clock-module)
-   [Working of Astable mode of IC 555 Timer](#working-of-astable-mode-of-ic-555-timer)
-   [Working of Monostable mode of IC 555 Timer](#working-of-monostable-mode-of-ic-555-timer)
-   [Working of bistable mode of IC 555 Timer and Role of IC 7400](#working-of-bistable-mode-of-ic-555-timer-and-role-of-ic-7400)
5.  [Images](#images)
6.  [References](#references)
   
## Module overview

A clock module synchronizes all the operations of the computer. The clock is based on the popular 555 timer IC, which we use in three different ways in the project.

The clock can adjust its speed from less than 1Hz to a few hundred Hz. The clock also has a manual mode where we can push a button to advance each clock cycle which is useful in debugging the computer.

## Components
- **555 timer**
- **SPDT switch**
- **Push button**
- **Resistors** : 5x 1K ohm, 1x 1M ohm, 1x 220 ohm
- **Capacitors**: 3x 0.01uF, 1x 0.1uF, 1x 1uF
- **LED**: 1x Red
- **Potentiometer** : 1x 1M ohm
- **IC 7400** : 2x Quad NAND Gates

## Schematics

![MAR_Schematics](https://eater.net/schematics/clock.png)

**Fig.** ***Clock module Schematic*** (designed on KiCAD, Credits: Ben Eater)

## Working

### Overall Working of Clock module

- The clock module is the first module of the computer and it is used to synchronize all operations.
- The clock module is based on the popular 555 timer IC and it uses three of them in different modes: astable, monostable, and bistable.
- The astable mode generates an oscillating signal that can be adjusted by a potentiometer from less than 1 Hz to a few hundred Hz.
- The monostable mode generates a single pulse when triggered by a negative edge on the trigger pin2.
- The bistable mode acts as a latch that can be toggled by a switch.
- The clock module has three outputs: Halt, Step, and Clock.
- The Halt output is high when the clock is stopped by the switch, and low when the clock is running.
- The Step output is high when the switch is in manual mode, and low when the switch is in automatic mode.
- The Clock output is the final clock signal that is fed to the rest of the computer. It can be either the oscillating signal from the astable mode, or the single pulse from the monostable mode, depending on the switch position.
- The clock module also has a 5V/2A power supply that powers the whole computer.

### Working of Astable mode of IC 555 Timer

- In astable mode, the 555 timer acts as an oscillator that generates a square wave.
- The frequency and duty cycle of the wave can be adjusted by changing the values of two resistors (R1 = 1K and R2 =1M ohm potentiometer) and a capacitor (C1 = 1uF) connected to the chip.
- The output cycles on and off continuously, with no stable state.The output voltage is approximately equal to 5V.
- The output stays on for a time period determined by 0.693 (R1+R2)C1 and stays off for a time period determined by 0.693 (R2*C1).
- In order to keep the pulse generated to be symmetrical, 1K and 1M ohm potentiometer resistors are used to minimize the difference between the charging and discharging time to less than 1%.
- The capacitor (C1) charges up through both resistors (R1 and R2) when the output is on, and discharges through resistor (R2) when the output is off12.
- The charging and discharging of the capacitor is controlled by the trigger pin (pin 2), the threshold pin (pin 6), and the discharge pin (pin 7) of the IC.
- The trigger pin turns on the output when the voltage across the capacitor drops below 1/3 Vcc, and the threshold pin turns off the output when the voltage across the capacitor reaches above 2/3 Vcc.
- The discharge pin connects the capacitor to ground when the output is off, allowing it to discharge.
- The output pin (pin 3) provides the square wave output signal.
- The frequency of the clock pulse can be varied by changing the value of potentiometer
- The reset pin (pin 4) can be used to reset the timer by applying a low voltage, so it is connected to Vcc.
- The control pin (pin 5) can be used to adjust the threshold voltage, so in order to minimize noise it is connected to ground through a 0.01 μF capacitor.

### Working of Monostable mode of IC 555 Timer

For manual clock pulses normal push button can be used but there is issue of debouncing because of metal contacts which is undesirable. In order to avoid this IC 555 timer is used in mono stable mode.
Where even if there are multiple debouncing only one output pulse would be obtained.

-In monostable mode, the 555 timer acts as a one-shot pulse generator that produces a single output pulse of a fixed duration when triggered by the pushbutton which is pulled to 5V by 1K resistor.
- The duration of the output pulse is set by the values of a resistor (R1=1M ohm) and a capacitor (C1 = 0.1 uF) connected to the chip.
- The output pulse is approximately equal to 1.1 R1 C1 seconds long.
- The output is normally low (0 V) and goes high to 5V when a negative trigger pulse is applied to the trigger pin (pin 2).
- The trigger pulse must be shorter than the output pulse and its amplitude must be below 1/3 Vcc.
- The capacitor (C1) charges up through resistor (R1) when the output is high, and discharges through the discharge pin (pin 7) when the output is low.
- The charging and discharging of the capacitor is controlled by the trigger pin (pin 2), the threshold pin (pin 6), and the discharge pin (pin 7) of the IC.
- The threshold pin turns off the output when the voltage across the capacitor reaches above 2/3 Vcc.The discharge pin connects the capacitor to ground when the output is low, allowing it to discharge.
- The output pin (pin 3) provides the output pulse signal.
- The reset pin (pin 4) can be used to reset the timer by applying a low voltage, so it is connected to Vcc.
- The control pin (pin 5) can be used to adjust the threshold voltage, so to avoid unwanted noise it is connected to ground through a 0.01 μF capacitor.

### Working of bistable mode of IC 555 Timer and Role of IC 7400

- Selection between the automatic mode and manual mode of clock module can be simply done using a SPDT switch but due to debouncing of metal contacts which leads to undesirable results. So to implement this we make use of IC555 timer in Bistable mode along with the switch.
- In this mode the SR latch inside the IC 555 is used as the debouncing circuit.
- The pin 6 (Threshold) is connected to ground.
- So if the pin 4(Reset) is made low it resets the SR latch and if the pin 2 (Trigger) is made low the it sets the SR latch.
- Pin 4 and pin 2 are pulled  high by 1K ohm resistors.  
- The control pin (pin 5) can be used to adjust the threshold voltage, so to avoid unwanted noise it is connected to ground through a 0.01 μF capacitor.
- Using IC 7400 the selection between the monostable and astable output can be done with output of bistable mode as the select line as per the schematic.


## Images
![clk](https://github.com/Abhilash-bhat/EightBitComputer/assets/132778360/b3825cc1-f535-4656-8c60-620513b76d95)


## References 


* [Ben Eater's Channel](https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU)
* [Ben Eater's Website ](https://eater.net/8bit/alu)

 
