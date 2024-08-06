# GPS Disciplined Oscillator

This project focuses on developing a GPS Disciplined Oscillator (GPSDO) using the NEO-6M GPS module to generate a stable frequency oscillator with precise timing. The system is designed to extract 1PPS (one pulse per second) signals from the GPS module and use a Phase Locked Loop (PLL) circuit to ensure high-precision timekeeping. This README file provides an overview of the project, its components, and the implementation details.

## Table of Contents

1. [Introduction](#introduction)
2. [Problem Statement](#problem-statement)
3. [Components](#components)
4. [Circuit Design](#circuit-design)
5. [Software Implementation](#software-implementation)
6. [Simulation Tools](#simulation-tools)
7. [Results](#results)
8. [Literature Survey](#literature-survey)
9. [References](#references)

## Introduction

The Global Positioning System (GPS) is a satellite network that provides accurate location and time information globally. It has applications in various fields, including navigation, surveying, timing synchronization, and emergency response. The NEO-6M GPS module, with its compact size and reliable performance, is used in this project to provide precise timing information required for the GPS Disciplined Oscillator (GPSDO). Phase Locked Loop (PLL) are known for their stability and utilized in systems where synchronization accuracy is required.

## Problem Statement

The project's goal is to develop a system that accurately extracts 1PPS signals from a NEO-6M GPS module to trigger a PLL circuit generating a stable frequency oscillator. The system's design and implementation will be evaluated for timing accuracy and synchronization across multiple units, demonstrating its effectiveness for high-precision timekeeping applications.

## Components

1. **NEO-6M GPS Module**:
   - Features: MediaTek MT3339 chipset, supports GPS, GLONASS, Galileo.
   - Interface: UART for easy integration with microcontrollers.
   - Applications: Drones, handheld GPS devices, vehicle tracking systems.

2. **Phase Locked Loop (PLL)**:
   - Components:
     - **Phase Detector (PD)**: Compares phases of input and feedback signals.
     - **Voltage-Controlled Oscillator (VCO)**: Generates output signal frequency.
     - **Low Pass Filter (LPF)**: Filters out high-frequency noise.
     - **Frequency Divider**: Divides the frequency of the VCO output.
   - Applications: Communication systems, clock recovery, frequency synthesis.

## Circuit Design

### Block Diagram

![Block Diagram](https://github.com/anirudhnayak27/GPS_DISCIPLINED_OSCILLATOR/blob/a8cc889584264d59354eb08446d58e0c8492959f/PROJECT_DOCS/GPSDO_BLOCK_DIAGRAM.png)  

### Circuit Diagrams

1. **GPS Circuit**
   - Connects the NEO-6M GPS module and Arduino to extract 1PPS signals.
  ![GPS-CIRCUIT](https://github.com/anirudhnayak27/GPS_DISCIPLINED_OSCILLATOR/blob/e9c71a6aab1f83298501b55bb2cb23059e39ac80/PROJECT_DOCS/GPS_CIRCUIT.png)
2. **PLL Circuit**
   - Utilizes the PLL `CD4046` IC for frequency synthesis.
   ![PLL-CIRCUIT](https://github.com/anirudhnayak27/GPS_DISCIPLINED_OSCILLATOR/blob/e9c71a6aab1f83298501b55bb2cb23059e39ac80/PROJECT_DOCS/PLL_CIRCUIT.png) 

### Flow Chart
![FLOW-CHART](https://github.com/anirudhnayak27/GPS_DISCIPLINED_OSCILLATOR/blob/a8cc889584264d59354eb08446d58e0c8492959f/PROJECT_DOCS/GPSDO_FLOWCHART.png)

## Software Implementation

The software implementation involves configuring the NEO-6M GPS module and interfacing it with the PLL circuit. The following steps outline the process:

1. **Data Extraction**: Parse NMEA 0183 sentences, specifically the $GPRMC sentence, to extract timing information.
2. **Signal Processing**: Use extracted 1PPS signals to control the PLL circuit.
3. **Error Correction**: Implement error-checking mechanisms using checksums for data integrity.

### Example $GPRMC Sentence

```plaintext
$GPRMC,123519,A,4807.038,N,01131.000,E,022.4,084.4,230394,003.1,W*6A
```

### Explanation

- `123519`: Time of fix is 12:35:19 UTC.
- `A`: Status is Active (valid fix).
- `4807.038,N`: Latitude is 48 degrees 7.038 minutes North.
- `01131.000,E`: Longitude is 11 degrees 31.000 minutes East.
- `022.4`: Speed over ground is 22.4 knots.
- `084.4`: Track angle is 84.4 degrees (True).
- `230394`: Date of fix is 23rd March 1994.
- `003.1,W`: Magnetic variation is 3.1 degrees West.
- `*6A`: Checksum value for data integrity verification.

## Simulation Tools

### TINA by Texas Instruments

- **Key Features**: Design PLLs, analyze stability, evaluate phase noise.
- **Benefits**: Accelerates design and facilitates optimization.

### ADIsimPLL by Analog Devices

- **Key Features**: Customizable parameters, phase noise analysis, loop filter optimization.
- **Benefits**: Streamlines design process and offers access to Analog Devices' PLL products.

## Results

### Intermediate Results

- **GPS Output**: The GPS module provides accurate 1PPS signals.
  ![GPS-result](https://github.com/anirudhnayak27/GPS_DISCIPLINED_OSCILLATOR/blob/2b737941010f289b3e0ced852432c7ba1a7b475e/RESULTS/GPS_RESULT.png)
- **PLL Output**: The PLL circuit generates a stable frequency with precise synchronization.
  ![PLL-result](https://github.com/anirudhnayak27/GPS_DISCIPLINED_OSCILLATOR/blob/2b737941010f289b3e0ced852432c7ba1a7b475e/RESULTS/PLL_RESULT.png)

### Final Results

The GPS Disciplined Oscillator successfully demonstrates high-precision timekeeping with effective frequency stabilization. The system is suitable for applications requiring precise timing and synchronization across multiple units.

#### RESULT EXPLAINATION
![result-explained](https://github.com/anirudhnayak27/GPS_DISCIPLINED_OSCILLATOR/blob/5aa92979e5ed261350767cb1498942aaac4b291f/RESULTS/RESULT_EXPLAINED.png)

## Literature Survey

1. **Characterizing GPS Disciplined Oscillators for Distributed Vehicle-to-X Measurement Applications** by Julia Bauer:
   - Analyzes reference signal stability of 1PPS and 10MHz signals using a low-cost GPSDO.
   - Utilizes software-defined radio and digital signal processing for measurement.

2. **Evaluating the Frequency and Time Uncertainty of GPS Disciplined Oscillators and Clocks** by Michael A. Lombardi:
   - Discusses uncertainty evaluation in GPSDOs and GPSDCs.
   - Explains GPS time traceability to the International System (SI).

3. **Senior Design Project Report on GPS Disciplined Oscillator** by Mohammed Faraz (KLETECH):
   - Focuses on improving GPS data accuracy using the Neo-6M module and Arduino processing.
   - Enhances the frequency of the 1PPS signal with an integrated oscillator circuit and timer.

## References

1. Bauer, J. (Year). Characterizing GPS Disciplined Oscillators for Distributed Vehicle-to-X Measurement Applications.
2. Lombardi, M. A. (Year). Evaluating the Frequency and Time Uncertainty of GPS Disciplined Oscillators and Clocks.
3. Faraz, M. (Year). Senior Design Project Report on GPS Disciplined Oscillator [KLETECH].

---
