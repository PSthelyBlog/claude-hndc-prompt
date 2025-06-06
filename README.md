# VM-001: Claude HNDC Prompt

[![Version](https://img.shields.io/badge/version-1.1-blue.svg)](https://github.com/PSthelyBlog/claude-hndc-prompt/releases)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Compatible](https://img.shields.io/badge/Claude-Opus%204-purple.svg)](https://www.anthropic.com)
[![Architecture](https://img.shields.io/badge/architecture-HNDC--LDDC-orange.svg)](docs/architecture.md)
[![Status](https://img.shields.io/badge/status-active-success.svg)](https://github.com/PSthelyBlog/claude-hndc-prompt)

> A Hybrid Neuro-Deterministic Computer implementation that bridges natural language and deterministic computation within Claude's conversational interface.

## Overview

VM-001 is a computational system that combines language understanding with deterministic mathematical operations. It operates as a functional computer within Claude's conversation environment, providing memory management, register operations, stack functionality, precise mathematical computations, and programmable sequences through the VM-001 Protocol Language (VPL).

The system enables users to perform calculations and computational tasks using conversational language while maintaining the precision and reproducibility of traditional computing. With VPL, users can also define reusable programs for complex computations.

## Table of Contents

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

## Quick Start

Get VM-001 running in Claude in under a minute:

1. Copy the complete operational prompt from [`VM-001 Hybrid Neuro-Deterministic Computer - Operational Instructions.md`](https://github.com/PSthelyBlog/claude-hndc-prompt/blob/main/VM-001%20Hybrid%20Neuro-Deterministic%20Computer%20-%20Operational%20Instructions.md)
2. Start a new conversation with Claude Opus 4
3. Paste the prompt
4. Claude will initialize VM-001 and display the boot sequence
5. Start computing with natural language or direct commands

```
VM-001> calculate 42 * 58
Result: 2436

VM-001> store that as answer
Stored: answer = 2436

VM-001> what's the factorial of 7
Result: 5040

VM-001> PROGRAM DEFINE square SET $result $n COMPUTE mul $result $n -> $result RETURN $result
Program 'square' defined successfully

VM-001> PROGRAM RUN square
Result: 49
```

## Features

### Core Capabilities

- **Natural Language Processing**: Understands conversational requests like "calculate 15% of 200" or "what's the square root of 144"
- **Deterministic Computation**: All mathematical operations produce consistent, reproducible results with IEEE 754 precision
- **State Management**: Maintains memory, registers, stack, and operation history throughout the conversation
- **Multiple Input Modes**: Accepts both natural language and direct VM commands
- **Real-time Execution**: Performs actual computations within the conversation environment
- **VM-001 Protocol Language (VPL)**: Define and execute reusable programs with variables, control flow, and function calls

### Computational Functions

- **Arithmetic Operations**: Addition, subtraction, multiplication, division, modulo, power, square root
- **Mathematical Functions**: Factorial (≤170), Fibonacci (≤1000), GCD, LCM, prime checking
- **Memory System**: Store/retrieve values with named keys (1000 item capacity)
- **Register Operations**: Four general-purpose registers (A, B, C, D)
- **Stack Operations**: Push, pop, peek with 100-level depth
- **Data Processing**: String manipulation, array operations, bitwise operations, statistical analysis
- **Programmable Sequences**: Create complex algorithms using VPL with loops, conditionals, and subroutines

### System Features

- **Configuration Management**: Customize memory limits, verbosity, error handling modes
- **Error Recovery**: Graceful error handling with helpful suggestions
- **Operation History**: Tracks last 5 operations for debugging and verification
- **Context Awareness**: References previous results with "that", "it", or named values
- **Help System**: Comprehensive documentation accessible within the VM
- **Program Storage**: Store and manage VPL programs in memory

## Usage

### Basic Operations

VM-001 accepts both natural language and direct commands:

```
VM-001> calculate 156 + 844
Result: 1000

VM-001> COMPUTE mul 25 4
Result: 100

VM-001> what's 20% of 450
Result: 90
```

### Memory Operations

Store and retrieve values for complex calculations:

```
VM-001> store 3.14159 as pi
Stored: pi = 3.14159

VM-001> calculate pi times 10 squared
Result: 314.159

VM-001> memory list
Memory contents:
- pi: 3.14159
- answer: 314.159
```

### Programming with VPL

Define reusable computational sequences:

```
VM-001> PROGRAM DEFINE circle_area COMPUTE mul $pi $radius -> $r_squared COMPUTE mul $r_squared $radius -> $area RETURN $area
Program 'circle_area' defined successfully

VM-001> store 3.14159 as pi
Stored: pi = 3.14159

VM-001> store 5 as radius
Stored: radius = 5

VM-001> PROGRAM RUN circle_area
Result: 78.53975
```

### Advanced Calculations

Chain operations and use mathematical functions:

```
VM-001> calculate factorial of 6 then divide by 2
Step 1: MATH factorial 6 → 720
Step 2: COMPUTE div 720 2 → 360
Result: 360

VM-001> find the GCD of 48 and 18
Result: 6

VM-001> stats [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
Statistics:
- Count: 10
- Sum: 55
- Mean: 5.5
- Median: 5
- Std Dev: 2.872
```

### Using Registers and Stack

```
VM-001> REG set A 100
Register A = 100

VM-001> REG set B 50
Register B = 50

VM-001> compute add register A and register B
Result: 150

VM-001> stack push 10
Pushed: 10

VM-001> stack push 20
Pushed: 20

VM-001> stack pop
Popped: 20
```

## Architecture

### System Layers

VM-001 implements a layered architecture combining language processing with deterministic computation:

```
┌─────────────────────────────────────────┐
│         User Interface Layer            │
│    (Natural Language I/O)               │
├─────────────────────────────────────────┤
│      Command Parser & Router            │
│   (LLM-based intent recognition)        │
├─────────────────────────────────────────┤
│       VPL Compiler & Runtime            │
│   (Program storage and execution)       │
├─────────────────────────────────────────┤
│    Deterministic Computation Engine     │
│  (JavaScript VM - Artifact System)      │
├─────────────────────────────────────────┤
│        State Management Layer           │
│  (Registers, Memory, Stack, Cache)      │
├─────────────────────────────────────────┤
│         LLM Substrate (CPU)             │
│    (Token prediction & generation)      │
└─────────────────────────────────────────┘
```

### Components

- **LLM Substrate**: Claude serves as the natural language processing layer
- **Deterministic Engine**: JavaScript artifact provides precise mathematical computation
- **VPL Runtime**: Compiler and execution environment for protocol language programs
- **State Management**: Persistent storage within conversation session
- **Command Router**: Translates between natural language and VM instructions

### Operational Flow

1. User provides input (natural language, direct commands, or VPL programs)
2. LLM parses intent and identifies computational requests
3. Commands are translated to VM instructions or VPL is compiled
4. JavaScript backend executes deterministic operations
5. Results are formatted and presented through terminal interface
6. State updates are preserved for subsequent operations

### Design Principles

- **Hybrid Processing**: Combines probabilistic language understanding with deterministic computation
- **State Persistence**: All operations maintain state within the conversation
- **Error Isolation**: Computational errors don't affect the conversational flow
- **Extensibility**: Architecture supports adding new operations and features
- **Programmability**: VPL enables complex algorithm implementation

## Command Reference

### Arithmetic Commands (COMPUTE)

| Command | Syntax                | Example              | Description            |
|---------|-----------------------|----------------------|------------------------|
| add     | `COMPUTE add <a> <b>` | `COMPUTE add 42 58`  | Addition (a + b)       |
| sub     | `COMPUTE sub <a> <b>` | `COMPUTE sub 100 37` | Subtraction (a - b)    |
| mul     | `COMPUTE mul <a> <b>` | `COMPUTE mul 6 7`    | Multiplication (a × b) |
| div     | `COMPUTE div <a> <b>` | `COMPUTE div 100 4`  | Division (a ÷ b)       |
| mod     | `COMPUTE mod <a> <b>` | `COMPUTE mod 17 5`   | Modulo (a % b)         |
| pow     | `COMPUTE pow <a> <b>` | `COMPUTE pow 2 8`    | Power (a^b)            |
| sqrt    | `COMPUTE sqrt <a>`    | `COMPUTE sqrt 144`   | Square root (√a)       |

### Mathematical Functions (MATH)

| Function  | Syntax               | Example             | Limits             |
|-----------|----------------------|---------------------|--------------------|
| factorial | `MATH factorial <n>` | `MATH factorial 5`  | n ≤ 170            |
| fibonacci | `MATH fibonacci <n>` | `MATH fibonacci 10` | n ≤ 1000           |
| gcd       | `MATH gcd <a> <b>`   | `MATH gcd 48 18`    | None               |
| lcm       | `MATH lcm <a> <b>`   | `MATH lcm 12 15`    | None               |
| prime     | `MATH prime <n>`     | `MATH prime 17`     | Returns true/false |

### Memory Commands

| Command | Syntax                       | Example              | Description               |
|---------|------------------------------|----------------------|---------------------------|
| store   | `MEMORY store <key> <value>` | `MEMORY store x 100` | Store value with key      |
| load    | `MEMORY load <key>`          | `MEMORY load x`      | Retrieve value by key     |
| clear   | `MEMORY clear [key]`         | `MEMORY clear x`     | Clear specific/all memory |
| list    | `MEMORY list`                | `MEMORY list`        | Show all stored values    |

### Program Commands (VPL)

| Command | Syntax                          | Example                              | Description                |
|---------|---------------------------------|--------------------------------------|----------------------------|
| define  | `PROGRAM DEFINE <name> <code>`  | `PROGRAM DEFINE sq COMPUTE mul $n $n -> $result RETURN $result` | Create new program |
| run     | `PROGRAM RUN <name> [args]`     | `PROGRAM RUN sq`                     | Execute stored program     |
| list    | `PROGRAM LIST`                  | `PROGRAM LIST`                       | Show all programs          |
| show    | `PROGRAM SHOW <name>`           | `PROGRAM SHOW sq`                    | Display program source     |
| delete  | `PROGRAM DELETE <name>`         | `PROGRAM DELETE sq`                  | Remove program             |

### System Commands

| Command                     | Description                | Example                                 |
|-----------------------------|----------------------------|-----------------------------------------|
| `help`                      | Display command reference  | `help`                                  |
| `help <topic>`              | Get help on specific topic | `help compute`                          |
| `help vpl`                  | VPL syntax guide           | `help vpl`                              |
| `status`                    | Show system status         | `status`                                |
| `config`                    | View configuration         | `config`                                |
| `config set <path> <value>` | Update configuration       | `config set terminal.verbosity verbose` |
| `clear <target>`            | Clear system state         | `clear memory`                          |

### Natural Language Examples

VM-001 understands various natural language patterns:

- "calculate 42 plus 58"
- "what's the factorial of 7"
- "store 100 as x"
- "multiply x by 2"
- "add 10 to the last result"
- "what's 15% of 200"
- "find the square root of 225"

## VM-001 Protocol Language (VPL)

VPL allows you to create reusable programs that execute without natural language processing, providing precise control over computational sequences.

### VPL Syntax

#### Variable References
- `$varname` - Access local or memory variables
- `$RESULT` - Last operation result
- `$STACK_TOP` - Top of stack value
- `$REG_A`, `$REG_B`, `$REG_C`, `$REG_D` - Register values
- `$FLAG_zero`, `$FLAG_carry`, `$FLAG_overflow`, `$FLAG_error` - Flag states

#### Operations
All VM instructions can be used with optional result storage:
```
COMPUTE add 5 10 -> $sum
MATH factorial 6 -> $fact
MEMORY store result $sum
STACK push $fact
```

#### Special VPL Commands
- `SET $target value` - Direct variable assignment
- `RETURN value` - Return value from program
- `CALL program_name` - Execute another program

#### Control Flow

**Conditional Execution:**
```
IF $condition > value THEN
  <operations>
ELSE
  <operations>
ENDIF
```

**Loops:**
```
LOOP count
  <operations>
ENDLOOP
```

### VPL Examples

#### Simple Function
```
VM-001> PROGRAM DEFINE double SET $result $n COMPUTE mul $result 2 -> $result RETURN $result
Program 'double' defined successfully

VM-001> SET $n 21
21

VM-001> PROGRAM RUN double
42
```

#### Factorial with Loop
```
VM-001> PROGRAM DEFINE factorial_iter SET $result 1 SET $i 1 LOOP $n COMPUTE mul $result $i -> $result COMPUTE add $i 1 -> $i ENDLOOP RETURN $result
Program 'factorial_iter' defined successfully

VM-001> SET $n 5
5

VM-001> PROGRAM RUN factorial_iter
120
```

#### Quadratic Formula Solver
```
VM-001> PROGRAM DEFINE quadratic COMPUTE pow $b 2 -> $b_sq COMPUTE mul 4 $a -> $four_a COMPUTE mul $four_a $c -> $four_ac COMPUTE sub $b_sq $four_ac -> $disc IF $disc < 0 THEN MEMORY store root_type "complex" RETURN -1 ENDIF COMPUTE sqrt $disc -> $sqrt_disc COMPUTE sub 0 $b -> $neg_b COMPUTE mul 2 $a -> $two_a COMPUTE add $neg_b $sqrt_disc -> $num1 COMPUTE div $num1 $two_a -> $root1 COMPUTE sub $neg_b $sqrt_disc -> $num2 COMPUTE div $num2 $two_a -> $root2 MEMORY store root1 $root1 MEMORY store root2 $root2 MEMORY store root_type "real" RETURN 2
Program 'quadratic' defined successfully

VM-001> SET $a 1
1

VM-001> SET $b -5
-5

VM-001> SET $c 6
6

VM-001> PROGRAM RUN quadratic
2

VM-001> MEMORY load root1
3

VM-001> MEMORY load root2
2
```

#### Recursive Fibonacci
```
VM-001> PROGRAM DEFINE fib_rec IF $n <= 1 THEN RETURN $n ENDIF COMPUTE sub $n 1 -> $n_minus SET $n $n_minus CALL fib_rec SET $fib_n_minus $RESULT COMPUTE sub $n_minus 1 -> $n_minus_2 SET $n $n_minus_2 CALL fib_rec COMPUTE add $fib_n_minus $RESULT -> $result RETURN $result
Program 'fib_rec' defined successfully

VM-001> SET $n 10
10

VM-001> PROGRAM RUN fib_rec
55
```

### Program Storage

- Programs are stored in VM memory with prefix `PROG_`
- Each program occupies one memory slot
- Programs persist throughout the session
- Programs can call other programs recursively
- Metadata tracks creation time and execution count

## Configuration

### Viewing Configuration

Display current configuration settings:

```
VM-001> config
Configuration:
{
  "memoryLimit": 1000,
  "stackLimit": 100,
  "historyLimit": 5,
  "terminal": {
    "verbosity": "normal",
    "showTiming": false,
    "showStatus": false
  },
  "errorMode": "strict",
  "precision": 15
}
```

### Configuration Options

| Setting               | Type    | Default  | Description                                         |
|-----------------------|---------|----------|-----------------------------------------------------|
| `memoryLimit`         | number  | 1000     | Maximum key-value pairs in memory                   |
| `stackLimit`          | number  | 100      | Maximum stack depth                                 |
| `historyLimit`        | number  | 5        | Number of operations to track                       |
| `precision`           | number  | 15       | Decimal places for display                          |
| `terminal.verbosity`  | string  | "normal" | Output detail level: "minimal", "normal", "verbose" |
| `terminal.showTiming` | boolean | false    | Display operation execution time                    |
| `terminal.showStatus` | boolean | false    | Show system status in responses                     |
| `errorMode`           | string  | "strict" | Error handling: "strict" or "permissive"            |

### Modifying Configuration

Update settings using the config command:

```
VM-001> config set terminal.verbosity verbose
Configuration updated: terminal.verbosity = verbose

VM-001> config set terminal.showTiming true
Configuration updated: terminal.showTiming = true

VM-001> compute add 100 200
Result: 300
Execution time: 0.5ms
State updated: operationCount = 15

VM-001> config set memoryLimit 2000
Configuration updated: memoryLimit = 2000
```

### Verbosity Levels

- **minimal**: Shows only results
- **normal**: Shows results with basic context
- **verbose**: Shows results, timing, state changes, and detailed information

### Error Modes

- **strict**: Stops execution on errors (default)
- **permissive**: Continues execution, accumulates errors for review

## Examples

### Basic Calculator Usage

Simple calculations with natural language:

```
VM-001> what's 847 divided by 7
Result: 121

VM-001> calculate 15% tip on $84.50
Result: 12.675

VM-001> what's 2 to the power of 10
Result: 1024
```

### Scientific Calculations

Complex mathematical operations:

```
VM-001> calculate the square root of 2 times pi
Loading pi...
Result: 4.442882938158366

VM-001> what's the GCD of 1024 and 768
Result: 256

VM-001> is 2017 a prime number
Result: true
```

### Multi-Step Problem Solving

Calculate compound interest:

```
VM-001> store 10000 as principal
Stored: principal = 10000

VM-001> store 0.05 as rate
Stored: rate = 0.05

VM-001> store 10 as years
Stored: years = 10

VM-001> calculate principal times (1 + rate) to the power of years
Step 1: COMPUTE add 1 0.05 → 1.05
Step 2: COMPUTE pow 1.05 10 → 1.6289
Step 3: COMPUTE mul 10000 1.6289 → 16289
Result: 16289

VM-001> subtract principal from that
Result: 6289
Interest earned: $6,289
```

### Algorithm Implementation with VPL

Implementing a GCD algorithm:

```
VM-001> PROGRAM DEFINE gcd_algo SET $a $num1 SET $b $num2 LOOP 100 IF $b == 0 THEN RETURN $a ENDIF COMPUTE mod $a $b -> $remainder SET $a $b SET $b $remainder ENDLOOP RETURN $a
Program 'gcd_algo' defined successfully

VM-001> SET $num1 48
48

VM-001> SET $num2 18
18

VM-001> PROGRAM RUN gcd_algo
6
```

### Data Analysis

Statistical operations on datasets:

```
VM-001> stats [23, 45, 67, 32, 89, 54, 21, 76, 43, 65]
Statistics:
- Count: 10
- Sum: 515
- Mean: 51.5
- Median: 49
- Min: 21
- Max: 89
- Variance: 476.25
- Std Dev: 21.823

VM-001> array sort [5, 2, 8, 1, 9, 3, 7]
Result: [1, 2, 3, 5, 7, 8, 9]
```

### Complex Program: Prime Number Checker

```
VM-001> PROGRAM DEFINE is_prime IF $n <= 1 THEN RETURN false ENDIF IF $n <= 3 THEN RETURN true ENDIF COMPUTE mod $n 2 -> $mod2 IF $mod2 == 0 THEN RETURN false ENDIF SET $i 3 LOOP 100 COMPUTE mul $i $i -> $i_squared IF $i_squared > $n THEN RETURN true ENDIF COMPUTE mod $n $i -> $mod_i IF $mod_i == 0 THEN RETURN false ENDIF COMPUTE add $i 2 -> $i ENDLOOP RETURN true
Program 'is_prime' defined successfully

VM-001> SET $n 97
97

VM-001> PROGRAM RUN is_prime
true

VM-001> SET $n 100
100

VM-001> PROGRAM RUN is_prime
false
```

### Using Stack for RPN Calculator

Reverse Polish Notation calculation (2 + 3) × 4:

```
VM-001> stack push 2
Pushed: 2

VM-001> stack push 3
Pushed: 3

VM-001> stack pop
Popped: 3

VM-001> compute add 2 3
Result: 5

VM-001> stack push 5
Pushed: 5

VM-001> stack push 4
Pushed: 4

VM-001> stack pop
Popped: 4

VM-001> stack pop
Popped: 5

VM-001> compute mul 5 4
Result: 20
```

## Limitations

### Computational Boundaries

VM-001 operates within specific computational limits:

- **Factorial**: Maximum input of 170 (due to JavaScript number limits)
- **Fibonacci**: Maximum index of 1000 (configured limit)
- **Memory**: 1000 key-value pairs (configurable, includes stored programs)
- **Stack Depth**: 100 levels (configurable)
- **Recursion**: Maximum depth depends on call stack
- **Number Precision**: IEEE 754 double precision (~15-17 decimal digits)
- **Program Size**: Limited by available memory slots
- **Loop Iterations**: Practical limit of 1000 per loop

### System Boundaries

VM-001 operates as a sandboxed computational environment and cannot:

- Access files on your actual computer
- Connect to real networks or websites
- Run system commands on your machine
- Save data that persists after the conversation ends
- Interface with real hardware or devices
- Execute code that affects anything outside the chat environment

### Operational Constraints

- **Session-based**: All data is lost when the conversation ends
- **Single-threaded**: Operations execute sequentially, no parallel processing
- **Text-only**: No graphical output or visualization capabilities
- **Fixed precision**: Cannot perform arbitrary-precision arithmetic
- **Limited data types**: Primarily handles numbers, strings, and simple arrays
- **VPL Parsing**: Simple syntax, no advanced language features

### Natural Language Understanding

While VM-001 excels at interpreting computational intent, it may occasionally:

- Misinterpret ambiguous requests
- Require clarification for complex multi-step operations
- Default to most likely interpretation when multiple options exist

### Important Note

Within these boundaries, VM-001 performs real computations with mathematical precision. The limitations define its operational scope, not its authenticity as a computational system. All calculations are genuine, deterministic, and reproducible within the session.

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

VM-001 is based on the conceptual framework of hybrid neuro-deterministic computing, combining Claude's language capabilities with deterministic computation.

For questions, issues, or discussions, please use the [GitHub Issues](https://github.com/PSthelyBlog/claude-hndc-prompt/issues) page.
