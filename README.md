# Beam Current Integrator

Low-cost current-to-frequency nanoammeter based on the IVC102U switched integrator and STM32F407 microcontroller.

## Overview

This project implements a charge-quantization-based current measurement system for ultra-low current detection in the picoampere and nanoampere range. The system converts input current into a pulse frequency by integrating charge packets using the IVC102U precision switched integrator and counting comparator-generated pulses with an STM32F407 microcontroller.

The measurement architecture eliminates the need for a high-resolution ADC by directly converting accumulated charge into digital pulse events. Hardware-timed reset generation is implemented using TIM2 configured in slave-trigger one-pulse mode, providing deterministic reset timing independent of software latency.

## Features

* Current-to-frequency conversion based on charge quantization
* IVC102U precision switched integrator
* Adjustable integration capacitance (10 pF / 100 pF)
* Hardware-timed reset pulse generation using STM32 TIM2
* USB CDC communication
* Real-time pulse counting and CPS measurement
* Graphical user interface for monitoring and data logging
* CSV export support
* Compatible with multichannel beam-monitoring architectures

## Repository Contents

* Firmware for STM32F407 nanoammeter DAQ
* Firmware for DAC-based programmable current source
* Circuit schematics
* PCB design files
* DAQ software
* Documentation

## Applications

* Beam current monitoring
* Beam profile diagnostics
* Ionization chamber readout
* Radiation detector instrumentation
* Photodiode current measurements
* Educational nuclear instrumentation systems

## Principle of Operation

The input current is integrated on the selected feedback capacitor of the IVC102U. When the integrator output reaches the comparator threshold, a digital pulse is generated. Each pulse corresponds to a fixed amount of charge:

[
Q = C_{int}V_{th}
]

The input current is determined from the pulse frequency:

[
I = \frac{N \cdot C_{int} \cdot V_{th}}{T}
]

where:

* (N) is the number of counted pulses,
* (C_{int}) is the integration capacitance,
* (V_{th}) is the comparator threshold voltage,
* (T) is the acquisition interval.

## License

This project is provided for research, educational, and instrumentation-development purposes.




| Nanoammeter PCB Signal            | STM32 Pin | Function                                                   |
| --------------------------------- | --------- | ---------------------------------------------------------- |
| Comparator Output                 | PB3       | Hardware trigger input for TIM2 one-pulse reset generation |
| Comparator Output (optional copy) | PE11      | Pulse counting input (EXTI interrupt)                      |
| Integrator Reset                  | PA0       | TIM2 CH1 output generating reset pulse                     |
| GND                               | GND       | Common ground                                              |
| USB                               | USB FS    | Data acquisition and control                               |
