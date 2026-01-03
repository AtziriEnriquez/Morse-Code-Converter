# Morse-Code-Converter (SignalKey)
VHDL FPGA system that converts serial ASCII input into Morse code with audio and visual output

# FPGA Morse Code Translator  
**ENGS 31 / COSC 56 Final Project**

**Authors:** Alyssia Salas & Atziri Enriquez

---

## What This Project Does

This project is a hardware-based Morse code translator built on a Basys-3 FPGA using VHDL.

- Users type text into a terminal (PuTTY)
- The FPGA receives the text over serial (UART)
- Each character is translated into Morse code
- Morse code is output as:
  - Audio (250 Hz tone)
  - LED blinking

The system supports up to 80 characters per message and begins transmitting once the Enter key is pressed.

---

## Why We Built It

The goal of this project was to practice real-world digital system design on hardware, including:

- UART communication
- State machines and datapaths
- FIFO buffering
- Timing-accurate outputs
- Debugging differences between simulation and FPGA behavior

---

## How It Works (High Level)

Terminal (PuTTY) -> UART Receiver -> Morse Code Lookup -> FIFO Queue -> Audio Tone + LED Output

Each block is implemented as a separate VHDL module.

---

## Hardware & Tools

- FPGA: Digilent Basys-3
- Clock: 100 MHz
- Serial: 9600 baud UART
- Audio: PMODAMP2 + speaker
- Language: VHDL
- Toolchain: Xilinx Vivado

---

## Repository Structure

src/
├── SCI_Rx_final.vhd         # UART receiver
├── lookup.vhd               # ASCII -> Morse translation
├── Queue.vhd                # FIFO buffer
├── Transmitter.vhd          # Morse sequencing
├── squarewave.vhd           # 250 Hz audio tone
└── main_shell_v3.vhd        # Top-level module

constraints/
└── basys3.xdc

---

## Testing & Validation

- Individual testbenches for all major modules
- Full system verified in simulation
- Final design tested on real FPGA hardware
- Resolved LED and audio synchronization issues discovered during hardware testing

Demo video:  
https://drive.google.com/file/d/1MHbLZn1sF1Y7Xy53i4gCWDcn4dKM4H08/view

---

## What We Learned

- Simulation success does not guarantee hardware success
- Simpler state machines are easier to debug and more reliable
- Early hardware testing is critical
- Modular design simplifies integration
