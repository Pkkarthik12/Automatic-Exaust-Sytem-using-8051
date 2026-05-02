# Automatic Exhaust System Using 8051 Microcontroller

An embedded systems project that automatically activates an exhaust ventilation system when harmful gas levels are detected, using the 8051 microcontroller as the control unit.

---

## Project Overview

This project implements an automatic exhaust control system that continuously monitors the surrounding air quality using a gas sensor. When the sensor detects gas concentration above a safe threshold, the 8051 microcontroller triggers a relay to turn ON the exhaust fan/motor automatically — without any manual intervention. Once the air quality returns to a safe level, the system turns the exhaust OFF.

This kind of system is practical in kitchens, laboratories, garages, and industrial environments where gas leaks or poor ventilation pose a safety risk.

---

## How It Works

1. The gas sensor continuously monitors air quality and outputs an analog signal based on gas concentration
2. The ADC0804 converts the analog signal to digital and sends it to the 8051 microcontroller
3. The microcontroller reads the value and compares it against a preset threshold
4. If gas is detected above the threshold, the microcontroller activates the motor driver (LM293D) to run the exhaust fan
5. The LCD display shows the real-time gas level and status (SAFE / DANGER)
6. The exhaust fan runs until gas levels drop back to safe levels, at which point it switches OFF automatically

---

## Components Used

| Component | Description |
|-----------|-------------|
| AT89C51 (8051) | Main microcontroller — reads sensor data, controls motor and display |
| MQ-2 / MQ-6 Gas Sensor | Detects LPG, smoke, and other harmful gases (used in physical circuit) |
| ADC0804 | Analog-to-Digital Converter — converts sensor output for the 8051 |
| LM293D | Motor driver IC — drives the exhaust DC motor |
| DC Motor / Exhaust Fan | The actuator — activated when gas is detected above threshold |
| LM016L (16×2 LCD) | Displays real-time gas level and system status |
| LED (Red) | Visual alert indicator when gas level is in DANGER zone |
| RESPACK-8 | Pull-up resistor pack for LCD data lines |
| Resistors & Capacitors | Supporting passive components |
| Power Supply (5V / 12V) | Powers the microcontroller and motor separately |
| Crystal Oscillator (11.0592 MHz) | Clock source for the 8051 |

> **Note:** This project does **not** use a CO2 sensor. The gas detection is done using an **MQ-2 or MQ-6 sensor**, which detects LPG, smoke, and combustible gases.

---

## Proteus Simulation

The complete circuit has been designed and simulated in **Proteus 8 Professional**.

> ⚠️ **Simulation Note:** In the Proteus simulation, a **Potentiometer (POT-HG)** is used **instead of the MQ-2/MQ-6 gas sensor**. The potentiometer simulates the varying analog voltage output of the gas sensor — rotating it increases or decreases the simulated gas concentration level. In the actual physical circuit, the real MQ-series gas sensor is connected in its place.

📁 **Simulation file:** `simulation/AUTOMATIC_EXAUSTSYSTEM.pdsprj`

To run the simulation:
1. Open the `.pdsprj` file in **Proteus 8 or later**
2. Make sure the HEX file is loaded into the AT89C51 component
3. Click **Run** and rotate the potentiometer to simulate different gas levels
4. Watch the LCD display update with gas level readings and SAFE / DANGER status

### Simulation Preview

![Proteus Simulation](images/proteus_simulation.png)

---

## Project Photo

The hardware prototype of the Automatic Exhaust System:

![Project Photo](images/project_photo.jpg)

---

## Folder Structure

```
.
|-- README.md
|-- simulation/
|   └── AUTOMATIC_EXAUSTSYSTEM.pdsprj     # Proteus 8 simulation file
|-- images/
|   |-- proteus_simulation.png            # Screenshot of Proteus circuit
|   └── project_photo.jpg                 # Photo of hardware prototype
|-- src/
|   └── exhaust_system.asm                # 8051 Assembly source code
└── hex/
    └── exhaust_system.hex                # Compiled HEX file for microcontroller
```

---

## Key Concepts

- **Sensor interfacing** — Reading analog output from MQ-series gas sensors via ADC0804 into the 8051
- **ADC interfacing** — Using ADC0804 to convert analog sensor voltage to 8-bit digital value
- **Motor driver control** — Using LM293D to safely drive the DC exhaust motor from MCU signals
- **LCD interfacing** — Displaying real-time gas level and status messages on a 16×2 LCD
- **Threshold detection** — Comparing sensor values in software to trigger actuation
- **Potentiometer simulation** — POT-HG used in Proteus to replicate gas sensor analog output
- **Flyback protection** — Diode placement to protect the microcontroller from motor coil spikes
- **Sensor warm-up** — MQ sensors require ~20 seconds warm-up time before stable readings in physical circuit

---

## Applications

- Kitchen exhaust automation
- Garage and basement ventilation
- Industrial gas leak response systems
- Laboratory fume hood control
- LPG leak safety systems

---

## Author

**KARTHIK PK**  
Electronics and Instrumentation Engineering  
Federal Institute of Science and Technology (FISAT)
