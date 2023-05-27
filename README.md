# Electric Vending Machine Project
This repository contains a project developed for a course at our university. The project applies the knowledge gained during the course, including the use of assembly language with the FRDM-KL25Z microcontroller and the usage of the Mbed online compiler with C language. The main aim of the project is to provide students with a hands-on experience of how a microcontroller and assembly language work, and to develop a practical understanding of these concepts.

## Project Objective
The primary objective of this project is to design and build a "Mini Electric Vending Machine" using the FRDM-KL25Z microcontroller. This vending machine will supply electricity when a token is inserted, which can then be used to charge devices such as mobile phones and power banks.

The components used in the construction of this vending machine include:

- Infrared proximity sensor
- Light Emitting Diodes (LEDs)
- 2 buttons
- Liquid Crystal Display (LCD)
- Relay switch
- Servomotor
## Working Concept
When a token is inserted into the machine, it slides past an infrared proximity sensor, which then sends a signal to the PTC2_ANALOGIN_JX10. The total amount of tokens is calculated, with each token being worth RM0.50, and the total is displayed on the LCD.

The user is then presented with the option to proceed or cancel (refund). If they proceed, the PTB0_ANALOGIN_JX02 will receive a signal (0), the PTC1_ANALOGIN_JX12 will send a signal to the M1 Servo to move in a clockwise direction, and the total amount of tokens will be counted. This count will then be used to determine the amount of time that the electric supply will be provided for charging.

If the user chooses to cancel, the PTB1_ANALOGIN_JX04 will receive a signal (1), the PTC1_ANALOGIN_JX12 will send a signal to the M1 Servo to move in a clockwise direction, and all tokens will be refunded for the user to collect.

## Getting Started
### Prerequisites
- Mbed OS compatible development environment is required to compile and run the program.
### Usage
1. Clone this repository.
2. Navigate to the project directory.
3. Compile the program using Mbed OS compatible development environment.
4. Run the executable on FRDM-KL25Z microcontroller.

---
