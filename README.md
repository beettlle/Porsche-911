# Porsche 911 OBD Database

This repository contains OBD-II diagnostic data for Porsche 911 vehicles, focusing on both standard OBD-II PIDs and Porsche-specific Mode 22 commands.

## Vehicle Coverage

### 997 Generation (2005-2012)
- **2005-2008**: 997.1 (First generation)
- **2009-2012**: 997.2 (Mid-cycle refresh)

### 991 Generation (2012-2019)
- **2012-2016**: 991.1 (First generation)
- **2017-2019**: 991.2 (Mid-cycle refresh)

### 992 Generation (2019-2024)
- **2019-2023**: 992.1 (First generation)
- **2024+**: 992.2 (Mid-cycle refresh)

## Data Structure

### Standard OBD-II PIDs
Standard PIDs are documented in the [SAEJ1979 repository](https://github.com/OBDb/SAEJ1979) and include:
- Engine RPM, Vehicle Speed, Coolant Temperature
- Throttle Position, MAF Sensor, O2 Sensors
- Fuel Trims, Ignition Timing, Engine Load

### Porsche-Specific PIDs (Mode 22)
This repository focuses on Porsche-specific diagnostic data:

#### Performance Data
- **Engine RPM** (PID 0x242): High-precision engine speed
- **Engine Oil Temperature** (PID 0x441): Critical engine health indicator
- **Engine Coolant Temperature** (PID 0x245): Porsche-specific calculation formula

#### Chassis & Suspension
- **Steering Angle** (PID 0xC2): Steering wheel position and rate
- **PASM Mode** (PID 0x442): Porsche Active Suspension Management status
- **Individual Wheel Speeds** (PID 0x24A): All four wheel speed sensors

#### Driver Inputs
- **Throttle Pedal Position** (PID 0x246): Gas pedal position
- **Throttle Position (Actual)** (PID 0x242): Actual throttle plate position
- **Sport/Sport Plus Mode** (PID 0x308): Driving mode selection

#### Vehicle Dynamics
- **Vehicle Speed (GPS)** (PID 0x14A): GPS-referenced speed
- **Vehicle Speed (Speedometer)** (PID 0x44C): Speedometer reading

## Temperature Formulas

### Coolant Temperature (PID 0x245)
- **Celsius**: (x - 64) × 3/4
- **Fahrenheit**: (x - 64) × 27/20 + 32

### Oil Temperature (PID 0x441)
- **Celsius**: x - 60
- **Fahrenheit**: (x - 60) × 9/5 + 32

## Testing

Run the test suite to validate signal definitions:

```bash
python tests/test_responses.py
```

## Contributing

To add data for a new vehicle:

1. Create test cases in `tests/test_cases/[YEAR]/`
2. Add command support documentation
3. Update signal definitions in `signalsets/v3/default.json`
4. Run tests to validate

## Data Sources

- Community contributions from Porsche owners
- Technical documentation and service manuals
- Real-world testing and validation
- Forum discussions and technical articles

## License

This project is part of the OBDb initiative and follows the same licensing terms as the main OBDb organization.

