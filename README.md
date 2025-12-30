# Timing Diagram Generator – Examples & Usage

This document demonstrates how to use the **Timing Diagram Generator** in both **Editor mode** and **Simulation mode**, with examples and a detailed explanation of how the system works internally.

---

## 1. Overview

The Timing Diagram Generator is a browser-based tool for:

- Drawing timing diagrams manually
- Simulating combinational and sequential logic
- Visualizing clocked behavior using flip-flops
- Exporting diagrams for documentation or teaching

The application has **two distinct modes**:
- **Editor Mode** – manual waveform drawing
- **Simulation Mode** – logic-driven, clocked simulation

---

## 2. Editor Mode Example (Manual Timing Diagram)

### Purpose
Editor mode is used when you want **full manual control** over signal waveforms, without applying any logic or simulation rules.

This is useful for:
- Teaching timing diagrams
- Sketching expected signal behavior
- Creating figures for assignments or reports

---

### Example Setup

#### Signals
A, B, C

shell
Copy code

#### Manually Entered Waveforms
A : 01010101
B : 00110011
C : 00001111

yaml
Copy code

Each signal is independent. No signal affects another.

---

### How Editor Mode Works

- Each signal row is editable
- Clicking a cell cycles through:
unknown → 1 → 0 → unknown

yaml
Copy code
- There is **no logic evaluation**
- There is **no clock dependency**
- Signals are drawn exactly as entered

Editor mode behaves like a **pure waveform editor**.

---

## 3. Simulation Mode Example (Sequential Logic)

### Purpose
Simulation mode evaluates **Boolean expressions and flip-flops** using a generated clock.

This mode reflects **real digital hardware behavior**.

---

### Example: D Flip-Flop with Enable

#### Input Signals
D, EN

shell
Copy code

#### Output Signal
Q

shell
Copy code

#### Logic Expression
Q = D(D . EN)

yaml
Copy code

This represents:
- A **D flip-flop**
- Input = `D AND EN`
- Output updates on the selected clock edge

---

### Input Waveforms
D : 01011001
EN : 00111100

yaml
Copy code

---

### Simulation Behavior

1. A clock is generated automatically
2. On each **active clock edge**:
   - `D . EN` is evaluated using the **previous cycle**
   - The result is stored as the new `Q`
3. Between edges, `Q` remains unchanged

This matches real flip-flop timing semantics.

---

## 4. Supported Flip-Flops

| Function | Description |
|--------|------------|
| `D(x)` | D Flip-Flop |
| `T(x)` | T Flip-Flop |
| `SR(S,R)` | SR Flip-Flop |
| `JK(J,K)` | JK Flip-Flop |

### Important Rules
- Flip-flops are **edge-triggered**
- Inputs are sampled **before** the clock edge
- Outputs update **after** the edge

---

## 5. Logic Expression Syntax

### Operators

| Symbol | Meaning |
|------|--------|
| `+` | OR |
| `.` | AND |
| `'` | NOT (postfix) |
| `⊕` | XOR |
| `⊙` | XNOR |

### Examples
A + B
A . B'
(A ⊕ B)'

yaml
Copy code

---

### Keyboard Shortcuts

| Shortcut | Inserts |
|--------|---------|
| Shift + X | ⊕ (XOR) |
| Shift + N | ⊙ (XNOR) |

These shortcuts work inside logic input fields.

---

## 6. Clock Configuration

- Clock is generated based on:
  - Number of cycles
  - Starting level (0 or 1)
- In Simulation mode, you can select:
  - Rising edge (↑)
  - Falling edge (↓)

The active clock edges are **visually highlighted** in the diagram.

---

## 7. Output Editing Rules

| Signal Type | Editable | Behavior |
|-----------|--------|---------|
| Input | Yes | Fully user-defined |
| Combinational Output | No | Evaluated every cycle |
| Flip-Flop Output | First cell only | Edge-triggered |

Manual initialization is allowed **only at cycle 0** for flip-flop outputs.

---

## 8. Exporting Diagrams

You can export the timing diagram as:
- PNG
- PDF
- Clipboard image

Exports preserve:
- Clock edge markers
- Subscripts (e.g., A₁)
- Prime notation (e.g., B′)
- Grid alignment

---

## 9. When to Use Each Mode

### Use Editor Mode when:
- Drawing timing diagrams manually
- Teaching introductory concepts
- Logic behavior is not required

### Use Simulation Mode when:
- Demonstrating sequential circuits
- Teaching flip-flops and registers
- Validating logic expressions
- Showing clock-driven behavior

---

## 10. Final Notes

This simulator follows **hardware-accurate semantics**:

- Flip-flops sample inputs **before** the clock edge
- Outputs update **after** the edge
- Combinational logic settles using fixed-point evaluation

The tool is suitable for **academic, instructional, and research** use.
