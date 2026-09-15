# LDO_PMIC_Projects
# PMOS LDO Regulator Design and Analysis

## Design & Testbench of a Low-Dropout Regulator Using an Ideal VCVS Error Amplifier

This project presents the design, simulation, and analysis of a **PMOS-based Low-Dropout Regulator (LDO)** using an ** 60-dB  error amplifier**. The project also includes the design of a **5-transistor OTA** .

The LDO is designed and simulated in **Cadence Virtuoso/Spectre**.

---

# PMOS LDO Regulator Design and Analysis

## Design & Testbench of a PMOS LDO with BGR Reference,
## 80-dB VCVS Error Amplifier and Miller Compensation

This project presents the design, simulation, and analysis of a
PMOS-based Low-Dropout Regulator (LDO).

The LDO consists of:

- Bandgap Reference (BGR)
- Ideal 80-dB VCVS error amplifier
- PMOS pass transistor
- Feedback voltage divider
- Miller compensation network
- 500-pF output capacitor

The reference voltage used by the LDO error amplifier is generated
by the **Bandgap Reference (BGR)** rather than being generated
internally by the error amplifier.

The nominal reference voltage is approximately:

```text
VREF ≈ 0.8 V

## Project Specifications

| Parameter | Specification |
|-----------|---------------|
| Input Voltage (`Vin`) | 1.8 V |
| Output Voltage (`Vout`) | 1.5 V |
| Load Current | 20 mA – 100 mA |
| Nominal Load Current | 50 mA |
| Output Capacitor (`Cout`) | 500 pF |
| Error Amplifier | Ideal VCVS |
| Error Amplifier Gain | 80 dB |
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

## 1. LDO Architecture

The LDO consists of the following major blocks:

```text
                    Vin = 1.8 V
                        |
                        |
                   +----+----+
                   |  PMOS   |
                   |  Pass   |
                   |   FET   |
                   +----+----+
                        |
                        +---------- Vout = 1.5 V
                        |              |
                        |             Cout
                        |            500 pF
                        |              |
                        |             GND
                        |
                    Feedback
                        |
                   +----+----+
                   | R1 / R2 |
                   | Divider |
                   +----+----+
                        |
                       VFB
                        |
                  +-----+------+
                  |   Error    |
           Vref ->| Amplifier  |----> PMOS Gate
                  |  80 dB     |
                  +------------+

Note: i have not met all the specifications as mentioned above 
