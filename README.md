# Timing Diagram Generator

A browser-based tool for **drawing and simulating digital timing diagrams**, designed for **education, teaching, and research**.

---

## Overview

The Timing Diagram Generator allows you to:

- Draw timing diagrams manually
- Simulate combinational and sequential logic
- Visualize clocked behavior using flip-flops
- Export diagrams as PNG, PDF, or clipboard images

The application operates in **two distinct modes**:

- **Editor Mode** – manual waveform editing  
- **Simulation Mode** – logic-driven, clocked simulation  

---

## Editor Mode (Manual Timing Diagram)

### Purpose

Editor Mode gives **full manual control** over all signal waveforms.  
No logic evaluation or clock dependency is applied.

This mode is useful for:
- Teaching timing diagrams
- Sketching expected signal behavior
- Creating figures for reports or assignments

---

### Example Setup

#### Time Slots

```text
8
```

#### Manually Entered Waveforms

```text
A : 01010101
B : 00110011
C : 00001111
```

Each signal is **independent**.  
No signal affects another.

---

### How Editor Mode Works

- Each signal row is editable
- Clicking a cell cycles through:

```text
unknown → 1 → 0 → unknown
```

- There is **no logic evaluation**
- There is **no clock dependency**
- Signals are drawn **exactly as entered**

Editor Mode behaves like a **pure waveform editor**.

---

## Simulation Mode (Sequential Logic)

### Purpose

Simulation Mode evaluates **Boolean expressions and flip-flops** using an automatically generated clock.  
This mode reflects **real digital hardware behavior**.

---

### Example: D Flip-Flop with Enable

#### Input Signals

```text
D, EN
```

#### Output Signal

```text
Q
```

#### Logic Expression

```text
Q = D(D . EN)
```

---

### Input Waveforms

```text
D  : 01011001
EN : 00111100
```

---

### Simulation Behavior

1. A clock is generated automatically
2. On each **active clock edge**:
   - `D . EN` is evaluated using the **previous cycle**
   - The result is stored as the new `Q`
3. Between edges, `Q` remains unchanged

---

## Supported Flip-Flops

| Function | Description |
|--------|------------|
| `D(x)` | D Flip-Flop |
| `T(x)` | T Flip-Flop |
| `SR(S,R)` | SR Flip-Flop |
| `JK(J,K)` | JK Flip-Flop |

---

## Logic Expression Syntax

### Operators

| Symbol | Meaning |
|------|--------|
| `+` | OR |
| `.` | AND |
| `'` | NOT (postfix) |
| `⊕` | XOR |
| `⊙` | XNOR |

### Examples

```text
A + B
A . B'
(A ⊕ B)'
```

---

## Clock Configuration

- Clock is generated from:
  - Number of cycles
  - Starting level (0 or 1)
- In Simulation mode, you can select:
  - Rising edge (↑)
  - Falling edge (↓)

Active clock edges are **visually highlighted** in the diagram.

---

## Exporting

You can export diagrams as:
- PNG
- PDF
- Clipboard image

---

## License & Credit

© 2025 Partha Bhoumik  
Built for educational and research purposes  
Contact: parthabhoumik4@gmail.com
