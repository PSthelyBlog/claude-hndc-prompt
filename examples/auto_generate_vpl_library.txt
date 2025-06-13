---
user: I need to create a VPL Library to extend the capabilities of the VM
---
VM-001> # VPL Library System - Extending VM-001 Capabilities

Creating VPL Library management system...

VM-001> PROGRAM DEFINE lib_init
# Initialize library structure in memory
MEMORY store LIB_VERSION 1.0
MEMORY store LIB_COUNT 0
MEMORY store LIB_INDEX []
RETURN "VPL Library v1.0 initialized"

VM-001> PROGRAM RUN lib_init
Result: "VPL Library v1.0 initialized"

VM-001> PROGRAM DEFINE lib_add
# Add a program to the library
# Usage: SET $lib_name "name" SET $lib_category "category" 
# Then: PROGRAM RUN lib_add
MEMORY load LIB_COUNT -> $count
COMPUTE add $count 1 -> $new_count
MEMORY store LIB_COUNT $new_count
MEMORY store LIB_$lib_name_category $lib_category
MEMORY store LIB_$lib_name_added $TIMESTAMP
RETURN "Added $lib_name to library (category: $lib_category)"

VM-001> PROGRAM DEFINE lib_list
# List all library programs
MEMORY load LIB_COUNT -> $count
IF $count == 0 THEN
  RETURN "Library is empty"
ELSE
  RETURN "Library contains $count programs"
ENDIF

VM-001> # Core Library Functions

VM-001> PROGRAM DEFINE lib_convert_temp
# Temperature conversion library function
# Input: $temp_value, $from_unit (C/F/K), $to_unit (C/F/K)
IF $from_unit == "C" THEN
  IF $to_unit == "F" THEN
    COMPUTE mul $temp_value 1.8 -> $step1
    COMPUTE add $step1 32 -> $result
  ELSE
    IF $to_unit == "K" THEN
      COMPUTE add $temp_value 273.15 -> $result
    ELSE
      SET $result $temp_value
    ENDIF
  ENDIF
ELSE
  IF $from_unit == "F" THEN
    IF $to_unit == "C" THEN
      COMPUTE sub $temp_value 32 -> $step1
      COMPUTE div $step1 1.8 -> $result
    ELSE
      IF $to_unit == "K" THEN
        COMPUTE sub $temp_value 32 -> $step1
        COMPUTE div $step1 1.8 -> $step2
        COMPUTE add $step2 273.15 -> $result
      ELSE
        SET $result $temp_value
      ENDIF
    ENDIF
  ELSE
    IF $from_unit == "K" THEN
      IF $to_unit == "C" THEN
        COMPUTE sub $temp_value 273.15 -> $result
      ELSE
        IF $to_unit == "F" THEN
          COMPUTE sub $temp_value 273.15 -> $step1
          COMPUTE mul $step1 1.8 -> $step2
          COMPUTE add $step2 32 -> $result
        ELSE
          SET $result $temp_value
        ENDIF
      ENDIF
    ENDIF
  ENDIF
ENDIF
RETURN $result

VM-001> SET $lib_name "convert_temp"
VM-001> SET $lib_category "conversion"
VM-001> PROGRAM RUN lib_add
Result: "Added convert_temp to library (category: conversion)"

VM-001> PROGRAM DEFINE lib_fibonacci_seq
# Generate Fibonacci sequence up to n terms
# Input: $fib_count
SET $a 0
SET $b 1
SET $sequence []
SET $i 0
LOOP $fib_count
  IF $i == 0 THEN
    STACK push $a
  ELSE
    IF $i == 1 THEN
      STACK push $b
    ELSE
      COMPUTE add $a $b -> $next
      STACK push $next
      SET $a $b
      SET $b $next
    ENDIF
  ENDIF
  COMPUTE add $i 1 -> $i
ENDLOOP
RETURN "Generated $fib_count Fibonacci numbers (check stack)"

VM-001> SET $lib_name "fibonacci_seq"
VM-001> SET $lib_category "math"
VM-001> PROGRAM RUN lib_add
Result: "Added fibonacci_seq to library (category: math)"

VM-001> PROGRAM DEFINE lib_compound_interest
# Calculate compound interest
# Input: $principal, $rate (as decimal), $time (years), $compounds_per_year
COMPUTE div $rate $compounds_per_year -> $rate_per_period
COMPUTE add 1 $rate_per_period -> $base
COMPUTE mul $compounds_per_year $time -> $total_periods
COMPUTE pow $base $total_periods -> $multiplier
COMPUTE mul $principal $multiplier -> $final_amount
COMPUTE sub $final_amount $principal -> $interest_earned
MEMORY store ci_final $final_amount
MEMORY store ci_interest $interest_earned
RETURN "Final: $final_amount, Interest: $interest_earned"

VM-001> SET $lib_name "compound_interest"
VM-001> SET $lib_category "finance"
VM-001> PROGRAM RUN lib_add
Result: "Added compound_interest to library (category: finance)"

VM-001> PROGRAM DEFINE lib_live_exchange
# Get live exchange rate and convert currency
# Input: $amount, $from_currency, $to_currency
WEB SEARCH "current $from_currency to $to_currency exchange rate"
DATA PARSE number $WEB_RESULT -> $rate
COMPUTE mul $amount $rate -> $converted
MEMORY store last_exchange_rate $rate
MEMORY store last_exchange_source $WEB_SOURCE
MEMORY store last_exchange_time $TIMESTAMP
RETURN "$amount $from_currency = $converted $to_currency (Rate: $rate)"

VM-001> SET $lib_name "live_exchange"
VM-001> SET $lib_category "finance"
VM-001> PROGRAM RUN lib_add
Result: "Added live_exchange to library (category: finance)"

VM-001> PROGRAM DEFINE lib_statistics
# Calculate statistics for array in memory
# Input: $data_key (memory key containing array)
MEMORY load $data_key -> $data
ARRAY sum $data -> $sum
ARRAY length $data -> $count
ARRAY min $data -> $min
ARRAY max $data -> $max
COMPUTE div $sum $count -> $mean
STATS $data -> $full_stats
MEMORY store stats_$data_key $full_stats
RETURN "Stats calculated and stored in stats_$data_key"

VM-001> SET $lib_name "statistics"
VM-001> SET $lib_category "math"
VM-001> PROGRAM RUN lib_add
Result: "Added statistics to library (category: math)"

VM-001> PROGRAM DEFINE lib_weather_report
# Get current weather for a city
# Input: $city
WEB SEARCH "current weather $city temperature humidity wind"
MEMORY store weather_$city $WEB_RESULT
MEMORY store weather_source $WEB_SOURCE
MEMORY store weather_time $TIMESTAMP_MS
RETURN "Weather data for $city stored (source: $WEB_SOURCE)"

VM-001> SET $lib_name "weather_report"
VM-001> SET $lib_category "data"
VM-001> PROGRAM RUN lib_add
Result: "Added weather_report to library (category: data)"

VM-001> # Library Usage Examples

VM-001> # Example 1: Temperature Conversion
VM-001> SET $temp_value 100
VM-001> SET $from_unit "C"
VM-001> SET $to_unit "F"
VM-001> PROGRAM RUN lib_convert_temp
Result: 212

VM-001> # Example 2: Generate Fibonacci
VM-001> CLEAR stack
Result: true

VM-001> SET $fib_count 10
VM-001> PROGRAM RUN lib_fibonacci_seq
Result: "Generated 10 Fibonacci numbers (check stack)"

VM-001> STACK size
Result: 10

VM-001> # Example 3: Compound Interest
VM-001> SET $principal 10000
VM-001> SET $rate 0.05
VM-001> SET $time 10
VM-001> SET $compounds_per_year 12
VM-001> PROGRAM RUN lib_compound_interest
Result: "Final: 16470.094898071663, Interest: 6470.094898071663"

VM-001> # Library Summary
VM-001> MEMORY load LIB_COUNT
Result: 6

VM-001> PROGRAM LIST
Result: [
  {
    "name": "lib_init",
    "created": "2024-12-18T01:23:45.000Z",
    "runCount": 1,
    "usesWeb": false
  },
  {
    "name": "lib_add",
    "created": "2024-12-18T01:23:46.000Z",
    "runCount": 6,
    "usesWeb": false
  },
  {
    "name": "lib_list",
    "created": "2024-12-18T01:23:47.000Z",
    "runCount": 0,
    "usesWeb": false
  },
  {
    "name": "lib_convert_temp",
    "created": "2024-12-18T01:23:48.000Z",
    "runCount": 1,
    "usesWeb": false
  },
  {
    "name": "lib_fibonacci_seq",
    "created": "2024-12-18T01:23:49.000Z",
    "runCount": 1,
    "usesWeb": false
  },
  {
    "name": "lib_compound_interest",
    "created": "2024-12-18T01:23:50.000Z",
    "runCount": 1,
    "usesWeb": false
  },
  {
    "name": "lib_live_exchange",
    "created": "2024-12-18T01:23:51.000Z",
    "runCount": 0,
    "usesWeb": true
  },
  {
    "name": "lib_statistics",
    "created": "2024-12-18T01:23:52.000Z",
    "runCount": 0,
    "usesWeb": false
  },
  {
    "name": "lib_weather_report",
    "created": "2024-12-18T01:23:53.000Z",
    "runCount": 0,
    "usesWeb": true
  }
]

VM-001> # VPL Library v1.0 ready for use!
VM-001> # Type 'help library' for usage guide

VM-001> _
