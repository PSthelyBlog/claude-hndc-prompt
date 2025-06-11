# VM-001: Claude HNDC Prompt

[![Version](https://img.shields.io/badge/version-3.0-blue.svg)](https://github.com/PSthelyBlog/claude-hndc-prompt/releases)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Compatible](https://img.shields.io/badge/Claude-Opus%204-purple.svg)](https://www.anthropic.com)
[![Architecture](https://img.shields.io/badge/architecture-HNDC--LDDC--WI-orange.svg)](docs/architecture.md)
[![Status](https://img.shields.io/badge/status-active-success.svg)](https://github.com/PSthelyBlog/claude-hndc-prompt)

> A Hybrid Neuro-Deterministic Computer implementation that bridges natural language and deterministic computation within Claude's conversational interface, now with REPL runtime execution and web data integration.

## Overview

VM-001 v3.0 is a computational system that combines language understanding with deterministic mathematical operations and real-time data access through a triple-layer execution model. It operates as a functional computer within Claude's conversation environment, providing:

- **True Deterministic Computation**: Real JavaScript execution via REPL for complex operations
- **Web Data Integration**: Real-time data retrieval through web search and fetch operations
- **Hybrid Execution**: Intelligent selection between pattern matching (fast), REPL execution (accurate), and web search (current)
- **Natural Language Interface**: Conversational commands alongside direct VM instructions
- **VM-001 Protocol Language (VPL)**: Define reusable programs that can access web data
- **State Persistence**: Maintains memory, registers, stack, and web cache throughout the session

The system achieves genuine computational accuracy by executing actual JavaScript code for complex operations, using Claude's pattern matching for simple calculations, and retrieving real-world data through web searches, optimizing for speed, precision, and currency.

## Table of Contents

- [What's New in v3.0](#whats-new-in-v30)
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

## What's New in v3.0

### Web Data Integration
VM-001 v3.0 introduces web search and fetch capabilities for accessing real-time information:

- **Web Search Layer**: Retrieve current data, prices, rates, and information
- **Data Processing**: Parse JSON, CSV, and extract specific values from web results
- **Source Attribution**: Track and display data sources for transparency
- **Intelligent Caching**: Store web results to minimize repeated searches
- **VPL Integration**: Programs can now include web operations for dynamic data

### Enhanced Triple-Layer Architecture
- **Pattern Matching Layer**: Fast execution for simple arithmetic and state management
- **REPL Execution Layer**: Accurate computation for complex operations and mathematical functions
- **Web Integration Layer**: Current data retrieval for real-world information
- **Intelligent Routing**: Automatic selection of execution method based on operation type and data needs

### Key Improvements from v2.0
- Real-time data access through web search
- Enhanced VPL with web operation commands
- Web result caching and source tracking
- Data parsing and extraction utilities
- Expanded use cases for financial, scientific, and research applications

## Features

### Core Capabilities

- **Triple Execution Model**: 
  - Pattern matching for operations with numbers < 5 digits
  - REPL execution for complex calculations requiring precision
  - Web search for current data and external information
  - Automatic method selection based on complexity and data needs
- **Natural Language Processing**: Understands requests like "calculate 15% of 200" or "get current bitcoin price"
- **Deterministic Computation**: All mathematical operations produce consistent, reproducible results
- **Real-Time Data Access**: Retrieve current prices, rates, weather, and other live information
- **State Management**: Maintains memory, registers, stack, web cache, and operation history
- **Multiple Input Modes**: Accepts natural language, direct VM commands, VPL programs, and data queries

### Computational Functions

- **Arithmetic Operations**: Addition, subtraction, multiplication, division, modulo, power, square root
- **Mathematical Functions**: Factorial (≤170), Fibonacci (≤1000), GCD, LCM, prime checking
- **Memory System**: Store/retrieve values with named keys (1000 item capacity)
- **Register Operations**: Four general-purpose registers (A, B, C, D)
- **Stack Operations**: Push, pop, peek with 100-level depth
- **Data Processing**: String manipulation, array operations, bitwise operations, statistical analysis
- **Web Operations**: Search queries, URL fetching, data parsing, result caching
- **Programmable Sequences**: Create complex algorithms using VPL with loops, conditionals, and web access

### System Features

- **Execution Method Tracking**: Monitor which operations use pattern matching, REPL, or web search
- **Web Cache Management**: Store and retrieve web results with source attribution
- **Performance Benchmarking**: Compare execution methods for optimization
- **Configuration Management**: Customize memory limits, verbosity, error handling, and web settings
- **Error Recovery**: Graceful error handling with execution method and source information
- **Operation History**: Tracks last 5 operations for debugging and verification
- **Context Awareness**: References previous results with "that", "it", or named values
- **Help System**: Comprehensive documentation including web integration guidance

## Quick Start

Get VM-001 v3.0 running in Claude in under a minute:

1. Copy the complete operational prompt from [`VM-001 Hybrid Neuro-Deterministic Computer - Operational Instructions.md`](https://github.com/PSthelyBlog/claude-hndc-prompt/blob/main/VM-001%20Hybrid%20Neuro-Deterministic%20Computer%20-%20Operational%20Instructions.md)
2. Start a new conversation with Claude Opus 4
3. Paste the prompt
4. Claude will initialize VM-001 with REPL runtime and web integration
5. Start computing with natural language or direct commands

```
================================================================================
VM-001 HYBRID NEURO-DETERMINISTIC COMPUTER
Version 3.0 | Architecture: HNDC-LDDC-WI
================================================================================

Boot sequence initiated...
Loading deterministic computation engine... OK
Initializing state management layer... OK
Establishing LLM substrate connection... OK
Configuring terminal interface... OK
Loading VM-001 Protocol Language (VPL)... OK
Initializing REPL runtime interface... OK
Initializing web search interface... OK
Configuring data cache... OK

System ready.
Features: True deterministic computation via hybrid execution
          Real-time data access via web integration

VM-001> calculate 42 * 58
Result: 2436
[Execution: Pattern matching]

VM-001> what's the current EUR/USD exchange rate
Searching web...
Found: EUR/USD = 1.0892
Source: European Central Bank (2024-12-17)
Cached as: eur_usd_rate

VM-001> compute mul 1000 1.0892
Result: 1089.2
Converting €1000 = $1089.20
[Execution: REPL - precision required]
```

## Usage

### Basic Operations

VM-001 intelligently selects the execution method based on complexity and data needs:

```
VM-001> calculate 156 + 844
Result: 1000
[Execution: Pattern matching]

VM-001> compute sqrt 1000
Result: 31.622776601683793
[Execution: REPL - mathematical function]

VM-001> get current gold price per ounce
Searching web...
Found: Gold = $2,024.50/oz
Source: Kitco (2024-12-17 16:45 EST)
Cached as: gold_price_oz
[Execution: Web search]
```

### Web Data Operations

Access and process real-time information:

```
VM-001> web search "S&P 500 current value"
Searching web...
Found: S&P 500 = 4,719.55
Source: Yahoo Finance (2024-12-17)
Cached as: sp500_current

VM-001> web fetch https://api.exchangerate.com/usd
Fetching URL...
Data retrieved and cached as: exchange_rates

VM-001> data parse json {"rates": {"EUR": 0.918, "GBP": 0.792}}
Parsed JSON data stored

VM-001> data extract rates.EUR
Result: 0.918
```

### Memory Operations with Web Data

Store and use web-retrieved values in calculations:

```
VM-001> web search "speed of light meters per second"
Searching web...
Found: c = 299,792,458 m/s
Source: NIST Physics Constants
Cached as: speed_of_light

VM-001> store 299792458 as c
Stored: c = 299792458

VM-001> calculate wavelength of 2.4 GHz wifi
VM-001> compute div c 2.4e9
Result: 0.124913524
Wavelength: 0.125 meters (12.5 cm)
```

### Programming with VPL and Web Data

VPL programs can now access web data:

```
VM-001> PROGRAM DEFINE crypto_portfolio
WEB SEARCH "bitcoin price USD"
DATA PARSE number $WEB_RESULT -> $btc_price
WEB SEARCH "ethereum price USD"  
DATA PARSE number $WEB_RESULT -> $eth_price
COMPUTE mul $btc_holdings $btc_price -> $btc_value
COMPUTE mul $eth_holdings $eth_price -> $eth_value
COMPUTE add $btc_value $eth_value -> $total_value
MEMORY store portfolio_value $total_value
MEMORY store last_update $WEB_SOURCE
RETURN $total_value

VM-001> SET $btc_holdings 0.5
0.5

VM-001> SET $eth_holdings 2.0
2.0

VM-001> PROGRAM RUN crypto_portfolio
Searching web...
Searching web...
Result: 24750.50
Portfolio value: $24,750.50
[BTC: 0.5 × $43,521, ETH: 2.0 × $1,614.75]
```

## Architecture

### System Layers

VM-001 v3.0 implements a layered architecture with triple execution:

```
┌─────────────────────────────────────────┐
│         User Interface Layer            │
│    (Natural Language I/O)               │
├─────────────────────────────────────────┤
│      Command Parser & Router            │
│   (LLM-based intent recognition)        │
├─────────────────────────────────────────┤
│       Execution Method Selector         │
│   (Complexity & data need analysis)     │
├─────────────────────────────────────────┤
│       VPL Compiler & Runtime            │
│   (Program storage and execution)       │
├─────────────────────────────────────────┤
│      Triple Computation Engine          │
│  ┌────────────┐ ┌────────────┐ ┌──────┐│
│  │Pattern Match│ │REPL Execute│ │ Web  ││
│  │   (Fast)    │ │ (Accurate) │ │Search││
│  └────────────┘ └────────────┘ └──────┘│
├─────────────────────────────────────────┤
│        State Management Layer           │
│  (Memory, Registers, Stack, Web Cache)  │
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
Need external data?
  /        \
YES         NO
 ↓           ↓
Web      Complex math?
Search    /      \
 ↓      NO        YES
 ↓       ↓         ↓
 ↓    Pattern    REPL
 ↓     Match    Execute
 ↓       ↓         ↓
 └───→ Update State ←┘
          ↓
    Terminal Output
```

### Execution Method Criteria

**Pattern Matching (Claude Native):**
- Simple arithmetic with small numbers
- Basic string operations
- State management
- Command parsing

**REPL Execution:**
- Numbers with more than 5 digits
- Floating-point precision operations
- Mathematical functions (sqrt, pow, trig)
- Statistical calculations
- Matrix operations

**Web Search:**
- Current prices and rates
- Real-time data
- Reference information
- External API data
- Research queries

### State Management Strategy

Since REPL and web operations are stateless:
1. All state is maintained in conversation memory
2. Only necessary values are passed to REPL
3. Web results are cached with source attribution
4. Minimal code execution per operation
5. Results are integrated back into conversation state

## Command Reference

### Arithmetic Commands (COMPUTE)

| Command | Syntax                | Example              | Execution Method        |
|---------|-----------------------|----------------------|-------------------------|
| add     | `COMPUTE add <a> <b>` | `COMPUTE add 42 58`  | Pattern (small numbers) |
| sub     | `COMPUTE sub <a> <b>` | `COMPUTE sub 100 37` | Pattern (small numbers) |
| mul     | `COMPUTE mul <a> <b>` | `COMPUTE mul 6 7`    | Pattern/REPL (by size) |
| div     | `COMPUTE div <a> <b>` | `COMPUTE div 100 4`  | Pattern/REPL (precision)|
| mod     | `COMPUTE mod <a> <b>` | `COMPUTE mod 17 5`   | Pattern (integers)      |
| pow     | `COMPUTE pow <a> <b>` | `COMPUTE pow 2 8`    | REPL (always)           |
| sqrt    | `COMPUTE sqrt <a>`    | `COMPUTE sqrt 144`   | REPL (always)           |

### Web Commands (WEB)

| Command | Syntax                    | Example                               | Description           |
|---------|---------------------------|---------------------------------------|-----------------------|
| search  | `WEB SEARCH "query"`      | `WEB SEARCH "bitcoin price"`          | Search for data       |
| fetch   | `WEB FETCH <url>`         | `WEB FETCH https://api.example.com`   | Retrieve specific URL |
| cache   | `WEB CACHE <key>`         | `WEB CACHE btc_price`                 | View cached result    |
| cached  | `WEB CACHED <key>`        | `WEB CACHED exchange_rates`           | Load cached data      |

### Data Commands (DATA)

| Command   | Syntax                        | Example                          | Description              |
|-----------|-------------------------------|----------------------------------|--------------------------|
| parse     | `DATA PARSE <format> <data>`  | `DATA PARSE json {"a": 1}`       | Parse data format        |
| extract   | `DATA EXTRACT <path>`         | `DATA EXTRACT rates.EUR`         | Extract nested value     |
| aggregate | `DATA AGGREGATE <op> <array>` | `DATA AGGREGATE sum prices`      | Aggregate array data     |

### Memory Commands

| Command | Syntax                       | Example              | Description               |
|---------|------------------------------|----------------------|---------------------------|
| store   | `MEMORY store <key> <value>` | `MEMORY store x 100` | Store value with key      |
| load    | `MEMORY load <key>`          | `MEMORY load x`      | Retrieve value by key     |
| clear   | `MEMORY clear [key]`         | `MEMORY clear x`     | Clear specific/all memory |
| list    | `MEMORY list`                | `MEMORY list`        | Show all stored values    |

### System Commands

| Command                     | Description                      | Example                                 |
|-----------------------------|----------------------------------|-----------------------------------------|
| `help`                      | Display command reference        | `help`                                  |
| `help web`                  | Web integration guide            | `help web`                              |
| `status`                    | Show system status with web info | `status`                                |
| `config`                    | View configuration               | `config`                                |
| `clear webcache`            | Clear web result cache           | `clear webcache`                        |

## VM-001 Protocol Language (VPL)

VPL programs can now integrate web data for dynamic computations:

### Web Operations in VPL

```vpl
# Available web commands in VPL:
WEB SEARCH "query"           # Execute web search
WEB FETCH url               # Fetch specific URL
DATA PARSE format content   # Parse retrieved data
DATA EXTRACT path          # Extract from nested data

# Special variables:
$WEB_RESULT    # Last web operation result
$WEB_SOURCE    # Last web operation source
```

### Example: Weather Analysis Program

```vpl
PROGRAM DEFINE weather_convert
  # Get temperature for city
  WEB SEARCH "temperature $city celsius"
  DATA PARSE number $WEB_RESULT -> $temp_c
  
  # Convert to Fahrenheit
  COMPUTE mul $temp_c 1.8 -> $temp_f_base
  COMPUTE add $temp_f_base 32 -> $temp_f
  
  # Store results
  MEMORY store celsius $temp_c
  MEMORY store fahrenheit $temp_f
  MEMORY store weather_source $WEB_SOURCE
  
  # Categorize temperature
  IF $temp_c > 30 THEN
    SET $category "Hot"
  ELSE
    IF $temp_c < 10 THEN
      SET $category "Cold"
    ELSE
      SET $category "Moderate"
    ENDIF
  ENDIF
  
  RETURN "$category: $temp_c°C ($temp_f°F)"
```

### Example: Financial Calculator

```vpl
PROGRAM DEFINE investment_value
  # Get current stock price
  WEB SEARCH "$symbol stock price"
  DATA PARSE number $WEB_RESULT -> $price
  
  # Calculate current value
  COMPUTE mul $shares $price -> $current_value
  
  # Calculate gain/loss
  COMPUTE sub $current_value $cost_basis -> $gain_loss
  COMPUTE div $gain_loss $cost_basis -> $return_rate
  COMPUTE mul $return_rate 100 -> $return_pct
  
  # Store results
  MEMORY store current_price $price
  MEMORY store position_value $current_value
  MEMORY store return_percentage $return_pct
  
  RETURN $current_value
```

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
    "forceComplex": ["sqrt", "pow", "sin", "cos", "tan", "log"]
  },
  "web": {
    "maxResults": 5,
    "timeout": 10000,
    "cacheResults": true,
    "attributeSources": true
  },
  "terminal": {
    "verbosity": "normal",
    "showTiming": false,
    "showSources": true
  }
}
```

### Web Configuration Options

| Setting                | Type    | Default | Description                           |
|------------------------|---------|---------|---------------------------------------|
| `web.maxResults`       | number  | 5       | Maximum search results to process     |
| `web.timeout`          | number  | 10000   | Web operation timeout (ms)            |
| `web.cacheResults`     | boolean | true    | Cache web results in memory           |
| `web.attributeSources` | boolean | true    | Track and display data sources        |
| `terminal.showSources` | boolean | true    | Show sources in output                |

## Examples

### Real-Time Financial Analysis

```
VM-001> web search "Apple stock price"
Searching web...
Found: AAPL = $195.89
Source: Yahoo Finance (2024-12-17 16:00)
Cached as: aapl_price

VM-001> store 150 as shares
Stored: shares = 150

VM-001> compute mul 150 195.89
Result: 29383.5
Position value: $29,383.50

VM-001> web search "Apple stock price 1 year ago"
Searching web...
Found: AAPL (Dec 2023) = $142.65
Source: Historical data
Cached as: aapl_1year

VM-001> compute sub 195.89 142.65
Result: 53.24

VM-001> compute div 53.24 142.65
Result: 0.3732

VM-001> compute mul 0.3732 100
Result: 37.32
Annual return: 37.32%
```

### Scientific Calculations with Constants

```
VM-001> web search "Avogadro constant"
Searching web...
Found: NA = 6.02214076 × 10²³ mol⁻¹
Source: NIST Reference Constants
Cached as: avogadro_constant

VM-001> store 6.02214076e23 as NA
Stored: NA = 6.02214076e+23

VM-001> calculate molecules in 2.5 moles
VM-001> compute mul 2.5 6.02214076e23
Result: 1.50553519e+24
[Execution: REPL - large numbers]
```

### Automated Currency Converter

```
VM-001> PROGRAM DEFINE convert_currency
WEB SEARCH "exchange rate $from to $to"
DATA PARSE number $WEB_RESULT -> $rate
COMPUTE mul $amount $rate -> $converted
MEMORY store conversion_rate $rate
MEMORY store converted_amount $converted
MEMORY store conversion_source $WEB_SOURCE
RETURN "$amount $from = $converted $to (Rate: $rate)"

VM-001> SET $from "USD"
USD

VM-001> SET $to "JPY"
JPY

VM-001> SET $amount 1000
1000

VM-001> PROGRAM RUN convert_currency
Searching web...
Result: "1000 USD = 151230 JPY (Rate: 151.23)"
```

### Research and Computation

```
VM-001> web search "distance from Earth to Mars in km"
Searching web...
Found: Average distance = 225 million km
Source: NASA
Cached as: earth_mars_distance

VM-001> store 225e6 as distance_km
Stored: distance_km = 225000000

VM-001> store 299792.458 as c_km_per_s
Stored: c_km_per_s = 299792.458

VM-001> compute div 225e6 299792.458
Result: 750.663524
[Execution: REPL - precision required]

VM-001> compute div 750.663524 60
Result: 12.5110587
Light travel time: 12.5 minutes
```

## Limitations

### Computational Boundaries

VM-001 v3.0 operates within specific computational limits:

- **Factorial**: Maximum input of 170 (JavaScript number limits)
- **Fibonacci**: Maximum index of 1000 (configured limit)
- **Memory**: 1000 key-value pairs (configurable)
- **Web Cache**: 100 entries (automatic rotation)
- **Stack Depth**: 100 levels (configurable)
- **Number Precision**: IEEE 754 double precision (~15-17 decimal digits)
- **Web Timeout**: 10 seconds per request (configurable)

### System Boundaries

VM-001 operates as a sandboxed computational environment:

- Cannot access local files on your computer
- Cannot authenticate with private APIs
- Web access limited to public information
- REPL execution is sandboxed within Claude's environment
- All data is lost when the conversation ends
- No parallel processing capabilities

### Web Integration Constraints

- **Public Data Only**: Cannot access authenticated or private resources
- **Rate Limiting**: Subject to reasonable use of web searches
- **Data Freshness**: Cached results may become stale
- **Parse Limitations**: Complex data formats may require manual processing
- **Network Dependency**: Web features require internet connection

### Important Note

VM-001 v3.0 performs REAL computations with mathematical precision through actual JavaScript execution and retrieves REAL data through web searches. The triple-layer architecture optimizes for speed, accuracy, and currency, choosing the best execution method automatically. All calculations are genuine, deterministic, and reproducible within the session, while web data reflects actual current information with source attribution.

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

VM-001 v3.0 represents the evolution of hybrid neuro-deterministic computing, combining Claude's language capabilities with true deterministic computation through REPL integration and real-world data access through web search integration.

For questions, issues, or discussions, please use the [GitHub Issues](https://github.com/PSthelyBlog/claude-hndc-prompt/issues) page.
