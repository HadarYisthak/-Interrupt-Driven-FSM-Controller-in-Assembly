# -Interrupt-Driven-FSM-Controller-in-Assembly
An interrupt-driven embedded system for the MSP430G2553, based on an FSM architecture. Four push-buttons trigger unique LED patterns or signal outputs. The system starts in sleep mode, resumes from the last state, and uses a modular, layered Assembly code structure.

This project presents a practical and layered software architecture for an interrupt-driven embedded system implemented in Assembly language, based on an FSM (Finite State Machine) model. The system is designed for a personal development board using a microcontroller with four external push-buttons (PB0–PB3) connected to pins P2.0–P2.3, and an array of 8 LEDs connected to PORT1.

At system start-up, the microcontroller enters Sleep Mode (state=idle). When a push-button interrupt is triggered, the system transitions into one of four FSM states, each representing a unique and time-constrained LED behavior or signal output. A detailed FSM diagram is constructed in the planning phase to define all states and transitions triggered by interrupts.

FSM State Functions:
State 1 (PB0) – Binary Countdown:
Displays a binary countdown from 0xFx to 0x00 on the LED array in 0.5-second intervals for 10 seconds. The countdown is cyclic and maintains the last displayed value for continuation in the next cycle.

State 2 (PB1) – LED Shifting Pattern:
Lights a single LED in a right-to-left cyclic shift every 0.5 seconds for 5 seconds. The position is saved to allow resumption on subsequent interrupts.

State 3 (PB2) – Square Wave Signal Output:
Generates a square wave (50% duty cycle) on pin P2.7, alternating between 1kHz and 2kHz, each for 5 seconds. Precise timing is achieved using a Cycle Counter, with timing resolution measured to the instruction cycle using an oscilloscope.

State 0 (Idle) – Sleep Mode:
All LEDs are turned off, and the controller enters low-power sleep mode, waiting for the next interrupt to re-activate.
