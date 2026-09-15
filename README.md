# PMOS LDO Regulator Design and Analysis

## Design & Testbench of a PMOS LDO with 80-dB VCVS Error Amplifier and Miller Compensation

This project presents the design, simulation, and analysis of a
**PMOS-based Low-Dropout Regulator (LDO)** using an **ideal 80-dB
VCVS error amplifier** and a **PMOS pass transistor**.

The LDO uses **Miller compensation with a series nulling resistor**
to achieve stable closed-loop operation.

A **5-transistor OTA** is also designed as a bonus implementation
of the error amplifier.

The design and simulations are performed using **Cadence Virtuoso
and Spectre**.

---

# 1. Project Specifications

| Parameter | Specification |
|-----------|---------------:|
| Input Voltage (`Vin`) | 1.8 V |
| Output Voltage (`Vout`) | 1.5 V |
| Load Current | 20 mA – 100 mA |
| Nominal Load Current | 50 mA |
| Output Capacitor (`Cout`) | 500 pF |
| Error Amplifier | Ideal VCVS |
| Error Amplifier Gain | 80 dB |
| Compensation | Miller Compensation |
| Maximum Miller Capacitor (`Cm`) | 15 pF |
| Nulling Resistor | Series with `Cm` |
| PSRR @ 100 kHz | < -40 dB |
| Efficiency | ≥ 83% |
| DC Output Error | ≤ ±0.1 mV |
| Load Regulation | ≤ 2% |
| Line Regulation | ≤ 2% |
| Load Transient | 20 mA ↔ 50 mA |
| Load Step Edge Time | 10 ns |
| Maximum Overshoot/Undershoot | ≤ 150 mV |
| Settling Time | < 125 ns |
| Temperature Corners | 0°C, 27°C, 60°C |

---

# 2. LDO Architecture

The LDO consists of:

- PMOS pass transistor
- Feedback voltage divider
- 0.8-V reference
- Ideal 80-dB VCVS error amplifier
- Miller compensation capacitor
- Series nulling resistor
- 500-pF output capacitor
- Load current

The basic architecture is:

```text
                         Vin = 1.8 V
                             |
                             |
                        +----+----+
                        |         |
                        |  PMOS   |
                        |  PASS   |
                        |   FET   |
                        |         |
                        +----+----+
                             |
                             +------------ Vout = 1.5 V
                             |                 |
                             |                Cout
                             |               500 pF
                             |                 |
                             |                GND
                             |
                         Feedback
                             |
                         +---+---+
                         | R1/R2 |
                         |Divider|
                         +---+---+
                             |
                            VFB
                             |
                             v
                     +---------------+
                     | Error Amplifier|
              VREF ->|     80 dB      |----> PMOS Gate
                     +---------------+
                             |
                             |
                     Miller Compensation




Vref is taken from the BGR circuit   and i have not met the all the specifications mentioned above.
