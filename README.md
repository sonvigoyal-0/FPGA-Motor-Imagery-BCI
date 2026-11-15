# A Resource-Efficient Reconfigurable VLSI Architecture for Real-Time EEG Feature Extraction and Motor-Imagery Classification

**Status:** Active Development (Phase 1: Architecture Planning & Literature Review)

## What is this Project?

### The Core Concept: Motor-Imagery BCI
A Brain-Computer Interface (BCI) allows humans to control external devices (like wheelchairs or prosthetic limbs) using only their brain activity. **Motor-Imagery** refers to the specific brain signals (EEG) generated when a person *imagines* moving their limbs, even if they do not physically move them. 

### The Problem: Software Bottlenecks
Traditionally, raw EEG signals are recorded and sent to a computer, where software (like Python or MATLAB) runs complex math to clean the signal and extract features. This software-centric approach is power-hungry, bulky, and introduces significant processing delays (latency). For a paralyzed patient relying on a neuro-prosthetic, even a 500-millisecond delay can make the device feel unnatural and unsafe.

### Our Solution: Hardware Acceleration via FPGA
Instead of relying on software, this project builds the entire mathematical pipeline directly into hardware circuits using an **FPGA (Field Programmable Gate Array)**. By writing the architecture in Verilog, we are designing a custom silicon pathway that processes the brain signals instantly at the "edge" (right on the device). 

This approach dramatically reduces latency and power consumption, paving the way for wearable, real-time neuro-prosthetics.

## How the Pipeline Works
Our VLSI architecture is designed to handle the critical stages of EEG signal processing on-chip:
1. **Adaptive Artifact Cancellation (DSP):** Brain signals are often corrupted by eye blinks (EOG artifacts). We are implementing on-chip Digital Signal Processing (DSP) to dynamically filter out these blinks without losing the core motor-imagery data.
2. **Tapped Delay Line (TDL) Architecture:** Utilizing TDL structures to efficiently process the time-series brain waves while minimizing hardware resource usage.
3. **Feature Extraction:** Isolating the most important discriminative features from the cleaned signals (targeting the standard BCI Competition IV-2a dataset).
4. **Classification:** Outputting the final movement intent with ultra-low latency.

## Technology Stack
* **Hardware Description:** Verilog, SystemVerilog
* **Software Prototyping:** MATLAB, Python (MNE-Python)
* **Target Hardware:** FPGA 
* **Simulation & EDA:** Vivado / ModelSim / Tanner EDA

## Repository Structure
```text
├── docs/                   # High-level block diagrams and project reports
├── literature_review/      # Academic paper summaries and feasibility notes
├── software_models/        # Python/MATLAB DSP filter baseline scripts
├── rtl/                    # Verilog/SystemVerilog source files
├── testbenches/            # Simulation and verification files
└── README.md