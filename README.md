# Newton-Raphson Load Flow (NRLF) with Distributed Generation in C++

## Overview

This project implements a Newton-Raphson Load Flow (NRLF) solver for power systems, supporting distributed generation (DG) and various load models. The code is written in C++ and reads system data from input files, performs iterative load flow calculations, and outputs bus voltages, generator outputs, and system losses.

## Features

- **Newton-Raphson Load Flow** for balanced power systems
- **Support for Distributed Generators (DG)** with droop control
- **Multiple Load Models:** PQ, ZIP, and frequency-dependent loads
- **Per-unit and Ohmic Data Support**
- **Jacobian Matrix Construction and Inversion**
- **Detailed Output:** Bus voltages, angles, generator outputs, power losses, and convergence information

## File Structure

- `NRLF.cpp` — Main source code implementing the NRLF algorithm
- `islandip.txt` — Input file containing system data (buses, lines, loads, DGs)
- `nrlfop.txt` — Output file with results (voltages, angles, losses, etc.)

## How to Use

### 1. Prepare Input Data

Edit `islandip.txt` to define your system:
- Number of buses, lines, DGs, etc.
- Line data (from bus, to bus, r, x)
- Load data (bus, P, Q, type)
- DG data (bus, droop coefficients, limits, etc.)

**Note:** You can use per-unit or ohmic data. Set the `is_pu_data` flag in the code accordingly.

### 2. Compile

On macOS or Linux:
```sh
g++ -std=c++11 -o nrlf NRLF.cpp
```

### 3. Run

```sh
./nrlf
```

### 4. View Results

Check `nrlfop.txt` for:
- Bus voltages and angles
- DG outputs
- Power losses
- Convergence information

## Key Parameters

- **Base Voltage (`base_V`)** and **Base Power (`base_VA`)**: Used for per-unit conversion.
- **Tolerance**: Convergence criterion for the Newton-Raphson method.
- **no_iterations**: Maximum number of iterations allowed.

## Example Output

```
Bus_no    Voltage(magnitude)    Angle(deg)
1         1.00000000            0.00000000
2         0.98726088           -0.05700321
...
```

## Troubleshooting

- **Segmentation Faults:** Check input data for missing or invalid values.
- **Non-convergence:** Try increasing the number of iterations or adjusting the tolerance.
- **Incorrect Voltages:** Ensure per-unit conversion is correct and input data matches the expected format.

## License

This project is for educational and research purposes.

---

