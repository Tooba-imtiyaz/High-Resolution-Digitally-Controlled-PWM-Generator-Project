# High-Resolution Digitally Controlled PWM Generator
> **Mixed-Signal Design & Co-Simulation Verification Pipeline**

This repository contains the design, simulation, and verification files for a **Digitally Controlled Pulse-Width Modulation (PWM) Generator**. The project bridges digital logic design in Verilog with analog signal conditioning and comparison in LTspice using an automated Piece-Wise Linear (PWL) log-parsing workflow.

---

## 📌 Architecture & Overview

The system operates across two core domains:
1. **Digital Brain (Verilog):** A 4-bit synchronous counter with synchronous reset and enable controls generating discrete digital step states (`0000` to `1111`).
2. **Analog Bridge (LTspice):** 
   - **R-2R Ladder DAC:** Converts the 4-bit digital count into an analog stepped sawtooth waveform.
   - **Inverting Op-Amp Buffer (LT1001):** Scales and buffers the DAC output (Ramp range: 0V to -4.69V).
   - **Voltage Comparator (LT1011):** Compares the analog ramp against an adjustable reference voltage (Vref) to output a PWM signal with a duty cycle proportional to Vref.

---

##  Tools & Technologies Used
* **Digital Design:** Verilog HDL, Icarus Verilog (`iverilog`), GTKWave
* **Analog Simulation:** LTspice (LT1001 Op-Amp, LT1011 Comparator)
* **Co-Simulation Bridge:** Custom script converting `iverilog` transition logs to LTspice `.txt` PWL files.

---

##  Repository Structure

```text
PWM_project/
├── ANALOG/                   # LTspice schematics, symbol models, and simulation files
├── Digital/                  # Verilog source codes, testbenches, and VCD files
├── PWM Project REPORT.pdf    # Full engineering verification report
├── PWM_Generator.pdf         # Presentation slides
└── README.md                 # Project documentation
