# Clock Module

## Table of Contents
1. [Module Overview](#module-overview)


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

 
