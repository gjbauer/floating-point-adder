# 8-Bit Floating Point Adder

A complete hardware implementation of an 8-bit floating-point addition unit, designed and simulated in Logisim for a Computer Architecture final project.

## 📋 Project Overview

This project implements a fully functional 8-bit floating-point adder following a custom floating-point specification. The circuit performs IEEE 754-style floating-point addition through a multi-stage pipeline including exponent alignment, mantissa arithmetic, normalization, and rounding.

**Key Features:**
- Custom 8-bit floating-point format (1 sign, 4 exponent, 3 mantissa bits)
- Multi-cycle execution with finite state machine control
- Basic rounding implementation
- Visual simulation in Logisim
<!-- Support for special cases (zero, infinity, NaN) -->

## 🏗️ Architecture

### Floating-Point Format
```
[1 bit] [4 bits]   [3 bits]
 Sign   Exponent   Mantissa
```
- **Sign**: 0 for positive, 1 for negative
- **Exponent**: 4-bit biased representation (bias = 7)
- **Mantissa**: 3-bit fractional part with implicit leading 1

### Datapath Components
- **Input Unpacking**: Extracts sign, exponent, and mantissa fields
- **Exponent Comparator**: Determines alignment shift amount
- **Barrel Shifter**: Aligns mantissas based on exponent difference
- **Mantissa Adder/Subtractor**: 4-bit arithmetic unit
- **Leading Zero Counter**: Finds the first 1-bit for normalization
- **Normalization Shifter**: Adjusts mantissa and exponent
- **Rounding Logic**: Applies basic rounding rules
- **Output Packing**: Reassembles final floating-point result

### Control Unit
- **Finite State Machine**: 6-state controller managing the addition pipeline
- **State Sequencing**: UNPACK → ALIGN → ADD → NORMALIZE → ROUND → PACK

## 🚀 Getting Started

### Prerequisites
- [Logisim Evolution](https://github.com/logisim-evolution/logisim-evolution) (recommended) or Logisim Classic

### Installation & Usage
1. Clone this repository:
   ```sh
   git clone https://github.com/gjbauer/computer-architecture-final-project.git
   ```
2. Open Logisim and load `main/floating_point_adder.circ`
3. Set input values using the input pins
4. Run the simulation using the clock cycle controls
5. Observe the result on output pins and internal state displays

### Testing
The project includes comprehensive test cases:
- **Unit Tests**: Individual component verification
- **Integration Tests**: Full pipeline validation
- **Edge Cases**: Special values and boundary conditions

Load test files from the `tests/` directory to verify circuit functionality.

## 👥 Team Members

### TODO :
- [ ] Assign roles to team members...

### [Team Member 1 Name] - **Control Systems Architect**
- Designed and implemented the finite state machine controller
- Developed the main circuit integration and timing
- Created comprehensive test suites

### [Team Member 2 Name] - **Arithmetic Unit Specialist** 
- Implemented core arithmetic components (adder, shifter, comparator)
- Optimized datapath for performance and resource usage
- Developed normalization and rounding logic

### [Team Member 3 Name] - **Special Cases & I/O Engineer**
- Built input unpacking and output packing units
- Implemented special case handling (NaN, zero, infinity)
- Designed user interface and debugging displays

## 📚 Technical Details

### Algorithm Steps
1. **Unpack**: Extract sign, exponent, and mantissa from inputs
2. **Align**: Shift smaller mantissa right by exponent difference
3. **Add/Subtract**: Perform integer arithmetic on aligned mantissas
4. **Normalize**: Shift result left/right and adjust exponent
5. **Round**: Apply rounding to mantissa
6. **Pack**: Combine components into final result

### Performance Characteristics
- **Latency**: 6 clock cycles per operation
- **Resource Usage**: ~# of logic gates total

## 🔧 Development Notes

This project was developed over a 10-week period as part of Computer Architecture at Plymouth State University. The implementation focuses on educational clarity while maintaining computational correctness.

<!--### Challenges Overcome
 - --> 

## 🙏 Acknowledgments

- Professor Peter Drexel for project guidance and Computer Architecture instruction
- Logisim Evolution development team for the simulation environment
- IEEE 754 standard reference documentation

---

*Computer Architecture Final Project • Plymouth State University • Fall 2025*
