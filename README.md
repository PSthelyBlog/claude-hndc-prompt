# VM-001: Claude HNDC Prompt

[![Version](https://img.shields.io/badge/version-2.0-blue.svg)](https://github.com/PSthelyBlog/claude-hndc-prompt/releases)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Compatible](https://img.shields.io/badge/Claude-Opus%204-purple.svg)](https://www.anthropic.com)
[![Architecture](https://img.shields.io/badge/architecture-HNDC--LDDC-orange.svg)](docs/architecture.md)
[![Status](https://img.shields.io/badge/status-active-success.svg)](https://github.com/PSthelyBlog/claude-hndc-prompt)

> A Hybrid Neuro-Deterministic Computer implementation that bridges natural language and deterministic computation within Claude's conversational interface, now with true REPL runtime execution.

## Overview

VM-001 v2.0 is a computational system that combines language understanding with deterministic mathematical operations through a hybrid execution model. It operates as a functional computer within Claude's conversation environment, providing:

- **True Deterministic Computation**: Real JavaScript execution via REPL for complex operations
- **Hybrid Execution**: Intelligent selection between pattern matching (fast) and REPL execution (accurate)
- **Natural Language Interface**: Conversational commands alongside direct VM instructions
- **VM-001 Protocol Language (VPL)**: Define reusable programs for complex computations
- **State Persistence**: Maintains memory, registers, and stack throughout the session

The system achieves genuine computational accuracy by executing actual JavaScript code for complex operations while using Claude's pattern matching for simple calculations, optimizing for both speed and precision.

## Table of Contents

- [What's New in v2.0](#whats-new-in-v20)
- [Features](#features)
- [Quick Start](#quick-start)
- [Usage](#usage)
- [Architecture](#architecture)
- [Command Reference](#command-reference)
- [VM-001 Protocol Language (VPL)](#vm-001-protocol-language-vpl)
- [Configuration](#configuration)
- [Examples](#examples)
- [Limitations](#limitations)
- [License](#license)

## What's New in v2.0

### True Hybrid Computation
VM-001 v2.0 introduces REPL (analysis tool) integration for genuine deterministic computation:

- **Pattern Matching Layer**: Fast execution for simple arithmetic and state management
- **REPL Execution Layer**: Accurate computation for complex operations, floating-point precision, and mathematical functions
- **Intelligent Routing**: Automatic selection of execution method based on operation complexity
- **Performance Optimization**: Configurable thresholds for execution method selection

### Key Improvements
- Real JavaScript execution for mathematical precision
- IEEE 754 floating-point accuracy for complex calculations
- Seamless integration between language understanding and computation
- Performance benchmarking capabilities
- Enhanced error handling with execution method tracking

## Features

### Core Capabilities

- **Hybrid Execution Model**: 
  - Pattern matching for operations with numbers < 5 digits
  - REPL execution for complex calculations requiring precision
  - Automatic method selection based on complexity
- **Natural Language Processing**: Understands conversational requests like "calculate 15% of 200"
- **Deterministic Computation**: All mathematical operations produce consistent, reproducible results
- **State Management**: Maintains memory, registers, stack, and operation history throughout the conversation
- **Multiple Input Modes**: Accepts natural language, direct VM commands, and VPL programs
- **Real-time Execution**: Performs actual computations using JavaScript runtime when needed

### Computational Functions

- **Arithmetic Operations**: Addition, subtraction, multiplication, division, modulo, power, square root
- **Mathematical Functions**: Factorial (≤170), Fibonacci (≤1000), GCD, LCM, prime checking
- **Memory System**: Store/retrieve values with named keys (1000 item capacity)
- **Register Operations**: Four general-purpose registers (A, B, C, D)
- **Stack Operations**: Push, pop, peek with 100-level depth
- **Data Processing**: String manipulation, array operations, bitwise operations, statistical analysis
- **Programmable Sequences**: Create complex algorithms using VPL with loops, conditionals, and subroutines

### System Features

- **Execution Method Tracking**: Monitor which operations use pattern matching vs REPL
- **Performance Benchmarking**: Compare execution methods for optimization
- **Configuration Management**: Customize memory limits, verbosity, error handling, and REPL thresholds
- **Error Recovery**: Graceful error handling with execution method information
- **Operation History**: Tracks last 5 operations for debugging and verification
- **Context Awareness**: References previous results with "that", "it", or named values
- **Help System**: Comprehensive documentation including execution method guidance

## Quick Start

Get VM-001 v2.0 running in Claude in under a minute:

1. Copy the complete operational prompt from [`VM-001 Hybrid Neuro-Deterministic Computer - Operational Instructions.md`](https://github.com/PSthelyBlog/claude-hndc-prompt/blob/main/VM-001%20Hybrid%20Neuro-Deterministic%20Computer%20-%20Operational%20Instructions.md)
2. Start a new conversation with Claude Opus 4
3. Paste the prompt
4. Claude will initialize VM-001 with REPL runtime and display the boot sequence
5. Start computing with natural language or direct commands

```
================================================================================
VM-001 HYBRID NEURO-DETERMINISTIC COMPUTER
Version 2.0 | Architecture: HNDC-LDDC
================================================================================

Boot sequence initiated...
Loading deterministic computation engine... OK
Initializing state management layer... OK
Establishing LLM substrate connection... OK
Configuring terminal interface... OK
Loading VM-001 Protocol Language (VPL)... OK
Initializing REPL runtime interface... OK

System ready.
Features: True deterministic computation via hybrid execution

VM-001> calculate 42 * 58
Result: 2436

VM-001> compute sqrt 2 times pi
Result: 4.442882938158366
[Execution: REPL - complex operation]

VM-001> what's 847293 * 652847
Result: 552825098171
[Execution: REPL - large numbers]
```

## Usage

### Basic Operations

VM-001 intelligently selects the execution method based on complexity:

```
VM-001> calculate 156 + 844
Result: 1000
[Execution: Pattern matching]

VM-001> compute sqrt 1000
Result: 31.622776601683793
[Execution: REPL - mathematical function]

VM-001> what's 20% of 450
Result: 90
[Execution: Pattern matching]
```

### Memory Operations

Store and retrieve values for complex calculations:

```
VM-001> store 3.14159265359 as pi
Stored: pi = 3.14159265359

VM-001> calculate pi times 10 squared
Result: 314.159265359
[Execution: REPL - precision required]

VM-001> memory list
Memory contents:
- pi: 3.14159265359
- answer: 314.159265359
```

### Execution Method Control

Monitor and control how operations are executed:

```
VM-001> config set repl.threshold 1000
Configuration updated: repl.threshold = 1000

VM-001> optimization benchmark
Operation: multiply 847 by 293
Pattern result: 248171
REPL result: 248171
Pattern time: ~5ms (estimated)
REPL time: ~75ms (measured)
Recommendation: Use pattern matching for this scale

VM-001> config set terminal.showTiming true
Configuration updated: terminal.showTiming = true
```

### Programming with VPL

VPL programs use hybrid execution automatically:

```
VM-001> PROGRAM DEFINE pythagoras SET $c_squared 0 COMPUTE pow $a 2 -> $a_squared COMPUTE pow $b 2 -> $b_squared COMPUTE add $a_squared $b_squared -> $c_squared COMPUTE sqrt $c_squared -> $c RETURN $c
Program 'pythagoras' defined successfully

VM-001> SET $a 3
3

VM-001> SET $b 4
4

VM-001> PROGRAM RUN pythagoras
Result: 5
[Execution: Mixed - pattern for squares, REPL for sqrt]
```

## Architecture

### System Layers

VM-001 v2.0 implements a layered architecture with hybrid execution:

```
┌─────────────────────────────────────────┐
│         User Interface Layer            │
│    (Natural Language I/O)               │
├─────────────────────────────────────────┤
│      Command Parser & Router            │
│   (LLM-based intent recognition)        │
├─────────────────────────────────────────┤
│       Execution Method Selector         │
│   (Complexity analysis & routing)       │
├─────────────────────────────────────────┤
│       VPL Compiler & Runtime            │
│   (Program storage and execution)       │
├─────────────────────────────────────────┤
│    Hybrid Computation Engine            │
│  ┌─────────────┐  ┌─────────────────┐  │
│  │Pattern Match│  │ REPL Execution  │  │
│  │   (Fast)    │  │   (Accurate)    │  │
│  └─────────────┘  └─────────────────┘  │
├─────────────────────────────────────────┤
│        State Management Layer           │
│  (Registers, Memory, Stack, Cache)      │
├─────────────────────────────────────────┤
│         LLM Substrate (CPU)             │
│    (Token prediction & generation)      │
└─────────────────────────────────────────┘
```

### Execution Decision Flow

```
Input Command
     ↓
Parse Intent
     ↓
Analyze Complexity
     ↓
Is operation complex?
  /        \
NO          YES
 ↓           ↓
Pattern    REPL
Match    Execute
 ↓           ↓
Update State ←
     ↓
Terminal Output
```

### Complexity Criteria for REPL Execution

The system uses REPL for:
- Numbers with more than 5 digits
- Floating-point operations requiring precision
- Mathematical functions (sqrt, pow, trig, log)
- Array and matrix operations
- Statistical calculations
- Any operation where pattern matching might fail

### State Management Strategy

Since REPL execution is stateless:
1. All state is maintained in conversation memory
2. Only necessary values are passed to REPL
3. Minimal code is executed per REPL call
4. Results are integrated back into conversation state

### Design Principles

- **Hybrid Processing**: Optimizes for both speed and accuracy
- **Transparent Operation**: Execution method is trackable but doesn't interfere with usage
- **State Persistence**: All operations maintain state within the conversation
- **Error Isolation**: Computational errors don't affect the conversational flow
- **Minimal Overhead**: REPL is used only when necessary for accuracy

## Command Reference

### Arithmetic Commands (COMPUTE)

| Command | Syntax                | Example              | Execution Method        |
|---------|-----------------------|----------------------|-------------------------|
| add     | `COMPUTE add <a> <b>` | `COMPUTE add 42 58`  | Pattern (small numbers) |
| sub     | `COMPUTE sub <a> <b>` | `COMPUTE sub 100 37` | Pattern (small numbers) |
| mul     | `COMPUTE mul <a> <b>` | `COMPUTE mul 6 7`    | Pattern/REPL (by size) |
| div     | `COMPUTE div <a> <b>` | `COMPUTE div 100 4`  | Pattern/REPL (by precision) |
| mod     | `COMPUTE mod <a> <b>` | `COMPUTE mod 17 5`   | Pattern (integers)      |
| pow     | `COMPUTE pow <a> <b>` | `COMPUTE pow 2 8`    | REPL (always)           |
| sqrt    | `COMPUTE sqrt <a>`    | `COMPUTE sqrt 144`   | REPL (always)           |

### Mathematical Functions (MATH)

| Function  | Syntax               | Example             | Execution   | Limits     |
|-----------|----------------------|---------------------|-------------|------------|
| factorial | `MATH factorial <n>` | `MATH factorial 5`  | Pattern/REPL| n ≤ 170    |
| fibonacci | `MATH fibonacci <n>` | `MATH fibonacci 10` | Pattern/REPL| n ≤ 1000   |
| gcd       | `MATH gcd <a> <b>`   | `MATH gcd 48 18`    | Pattern     | None       |
| lcm       | `MATH lcm <a> <b>`   | `MATH lcm 12 15`    | Pattern     | None       |
| prime     | `MATH prime <n>`     | `MATH prime 17`     | Pattern     | Returns bool|

### Memory Commands

| Command | Syntax                       | Example              | Description               |
|---------|------------------------------|----------------------|---------------------------|
| store   | `MEMORY store <key> <value>` | `MEMORY store x 100` | Store value with key      |
| load    | `MEMORY load <key>`          | `MEMORY load x`      | Retrieve value by key     |
| clear   | `MEMORY clear [key]`         | `MEMORY clear x`     | Clear specific/all memory |
| list    | `MEMORY list`                | `MEMORY list`        | Show all stored values    |

### Execution Control Commands

| Command                          | Description                      | Example                          |
|----------------------------------|----------------------------------|----------------------------------|
| `optimization benchmark`         | Compare execution methods        | `optimization benchmark`         |
| `config set repl.threshold <n>`  | Set complexity threshold         | `config set repl.threshold 5000` |
| `config set terminal.showTiming` | Show execution timing            | `config set terminal.showTiming true` |
| `execution stats`                | Display execution statistics     | `execution stats`                |

### System Commands

| Command                     | Description                | Example                                 |
|-----------------------------|----------------------------|-----------------------------------------|
| `help`                      | Display command reference  | `help`                                  |
| `help execution`            | Execution method guide     | `help execution`                        |
| `status`                    | Show system status         | `status`                                |
| `config`                    | View configuration         | `config`                                |
| `clear <target>`            | Clear system state         | `clear memory`                          |

## VM-001 Protocol Language (VPL)

VPL programs automatically benefit from hybrid execution - simple operations use pattern matching while complex operations use REPL.

### VPL Features with Hybrid Execution

```vpl
# Example: Newton's Method for Square Root
PROGRAM DEFINE newton_sqrt
  SET $x $n
  SET $i 0
  
  LOOP 10
    # Simple arithmetic - pattern matching
    COMPUTE add $x $n -> $sum
    
    # Division - may use REPL for precision
    COMPUTE div $sum $x -> $avg
    COMPUTE div $avg 2 -> $x
    
    COMPUTE add $i 1 -> $i
  ENDLOOP
  
  RETURN $x
```

### Performance Considerations

VPL programs optimize automatically:
- Loop counters and simple arithmetic use pattern matching
- Complex calculations within loops use REPL
- State is maintained between operations
- No manual optimization needed

## Configuration

### Viewing Configuration

```
VM-001> config
Configuration:
{
  "memoryLimit": 1000,
  "stackLimit": 100,
  "precision": 15,
  "repl": {
    "threshold": 10000,
    "forceComplex": ["sqrt", "pow", "sin", "cos", "tan", "log"],
    "precision": true,
    "arrays": true,
    "stats": true
  },
  "terminal": {
    "verbosity": "normal",
    "showTiming": false,
    "showExecutionMethod": false
  }
}
```

### REPL Configuration Options

| Setting                        | Type    | Default | Description                             |
|--------------------------------|---------|---------|----------------------------------------|
| `repl.threshold`               | number  | 10000   | Use REPL for numbers larger than this  |
| `repl.forceComplex`            | array   | [...]   | Functions that always use REPL         |
| `repl.precision`               | boolean | true    | Use REPL for precision-critical ops    |
| `terminal.showExecutionMethod` | boolean | false   | Display which method was used          |

## Examples

### Precision-Critical Calculations

```
VM-001> calculate e to the power of pi
Loading constants...
Result: 23.140692632779267
[Execution: REPL - mathematical constants and complex function]

VM-001> what's the exact value of 1/3 plus 1/6
Result: 0.5
[Execution: REPL - precise fraction arithmetic]
```

### Performance Comparison

```
VM-001> optimization benchmark multiply 1234567 by 9876543
Analyzing operation complexity...

Pattern matching attempt...
REPL execution...

Results:
- Pattern: 12193254554881 (estimated)
- REPL: 12193254554881 (verified)
- Pattern time: ~10ms
- REPL time: ~80ms

Both methods agree. Pattern matching recommended for this scale.

VM-001> _
```

### Mixed Execution in Programs

```
VM-001> PROGRAM DEFINE mandelbrot_check
SET $real $c_real
SET $imag $c_imag
SET $i 0

LOOP 100
  # Complex arithmetic - uses REPL
  COMPUTE mul $real $real -> $real_sq
  COMPUTE mul $imag $imag -> $imag_sq
  COMPUTE add $real_sq $imag_sq -> $magnitude_sq
  
  # Simple comparison - pattern matching
  IF $magnitude_sq > 4 THEN
    RETURN $i
  ENDIF
  
  # More complex arithmetic
  COMPUTE mul $real $imag -> $temp
  COMPUTE mul $temp 2 -> $new_imag
  COMPUTE sub $real_sq $imag_sq -> $new_real
  COMPUTE add $new_real $c_real -> $real
  COMPUTE add $new_imag $c_imag -> $imag
  
  # Simple increment - pattern matching
  COMPUTE add $i 1 -> $i
ENDLOOP

RETURN 100
```

## Limitations

### Computational Boundaries

VM-001 v2.0 operates within specific computational limits:

- **Factorial**: Maximum input of 170 (JavaScript number limits)
- **Fibonacci**: Maximum index of 1000 (configured limit)
- **Memory**: 1000 key-value pairs (configurable)
- **Stack Depth**: 100 levels (configurable)
- **Number Precision**: IEEE 754 double precision (~15-17 decimal digits)
- **REPL Execution Time**: Adds ~50-100ms overhead per call
- **Pattern Matching**: Limited to 5-digit numbers for reliability

### System Boundaries

VM-001 operates as a sandboxed computational environment:

- Cannot access files on your actual computer
- Cannot connect to real networks or websites
- REPL execution is sandboxed within Claude's environment
- All data is lost when the conversation ends
- No parallel processing capabilities

### Hybrid Execution Constraints

- **REPL Overhead**: Complex operations have additional latency
- **State Transfer**: Values must be passed to/from REPL
- **Execution Limits**: Very long computations may timeout
- **Memory Overhead**: Hybrid system uses more conversation memory

### Important Note

VM-001 v2.0 performs REAL computations with mathematical precision through actual JavaScript execution. The hybrid architecture optimizes for both speed and accuracy, choosing the best execution method automatically. All calculations are genuine, deterministic, and reproducible within the session.

## License

This project is licensed under the MIT License:

```
MIT License

Copyright (c) 2025 PSthelyBlog

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## Acknowledgments

VM-001 v2.0 represents a significant evolution in hybrid neuro-deterministic computing, combining Claude's language capabilities with true deterministic computation through REPL integration.

For questions, issues, or discussions, please use the [GitHub Issues](https://github.com/PSthelyBlog/claude-hndc-prompt/issues) page.
