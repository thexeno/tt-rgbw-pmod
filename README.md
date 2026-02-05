# tt-rgbw-pmod
An overkill PMOD to powerfully handle powerful coloured LEDs for the tt08-rgbw-controller ASIC

[![tt-rgbw-pmod board](./images/tt-rgbw-pmod-3d.png)](./images/tt-rgbw-pmod.png "The tt-rgbw-pmod)

## Overview

This PMOD board provides high-power LED driver capabilities for the tt08-rgbw-controller ASIC, featuring four independent channels for RGBW LED control with both digital PWM and analog dimming modes.

## Pinout

| Pmod  | TinyTapeout | Function | Note |
|-------|-------------|----------|------|
| OUTPUT1 | uo[0]       | Red PWM input | Input impedance 100 kΩ |
| OUTPUT2 | uo[1]       | Green PWM input| Input impedance 100 kΩ |
| OUTPUT3 | uo[2]       | Blue PWM input| Input impedance 100 kΩ |
| OUTPUT4 | uo[3]       | White PWM input| Input impedance 100 kΩ |
| OUTPUT1 | -         | Not connected           |      |
| OUTPUT1 | -         | Not connected       |  |
| OUTPUT1 | -           | Not connected    |      |
| OUTPUT1 | -           | Not connected    |      |

## Getting Started

### Quick Setup Checklist

1. **Select the control mode** for each color channel using jumpers JP1, JP2, JP3, JP4:
   - **Jumper bridged**: Analog (LED side) dimming mode
   - **Jumper open**: Digital (LED side) PWM mode

2. **Verify 3.3V power** is available on the Demoboard's PMOD connector

3. **Connect** the RGBW Color Processor board to the Demoboard

4. **Apply external power**: Connect 6-20V to J4 or J5 (minimum 5V required to activate drivers)

### Using External LEDs

To use external LEDs instead of the onboard ones, open the following jumper connections:
- R3, R4, R5, R8, R9, R10, R11, R12

### Current Adjustment

Adjust the constant current output via resistors:
- R14 (Red channel)
- R18 (Green channel)
- R22 (Blue channel)
- R26 (White channel)

**Current calculation:**
- Digital dimming mode: I = 0.1V / R (default: 75mA)
- Analog dimming mode: I = 0.2V / R (default: 150mA)

## Operating Modes

### Digital PWM Mode (Jumper Open)
- PWM PMOD pin frequency: **< 1 kHz**
- Lower current consumption
- Suitable for most applications

### Analog Dimming Mode (Jumper Bridged)
- PWM  PMOD pin frequency: **> 10 kHz** (recommended: 50 kHz)
- Higher current capability
- For continuous operation at default settings (150mA per channel), a small heatsink is recommended:
  - Base size: 7×7 mm
  - Thermal resistance: 30-40°C/W

## Electrical Characteristics

| Parameter | Min | Typ | Max | Unit | Notes |
|-----------|-----|-----|-----|------|-------|
| External supply voltage | 6 | 12 | 20 | V | Required (J4 or J5) |
| External supply current | - | - | 400 | mA | 2W total max |
| Logic input voltage | - | 3.3 | - | V | TTL compatible |
| LED current (Digital mode) | - | 75 | - | mA | Per channel, default |
| LED current (Analog mode) | - | 150 | - | mA | Per channel, default |
| PWM frequency PMOD pin, Digital mode | - | - | 1 | kHz | Maximum recommended |
| PWM frequency PMOD pin, Analog mode | 10 | 50 | - | kHz | Minimum / recommended |

**TODO:** Verify reliable TTL level driving at 3.3V input

## License
todo

