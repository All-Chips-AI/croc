---
name: croc_repo
type: repo
version: alpha
agent: ChipActAgent
---
This repo contains the code for croc, a simple SoC for education using PULP IPs. Croc includes the rtl and 
all scripts necessary to produce a nearly finished chip in [IHPs open-source 130nm technology](https://github.com/IHP-GmbH/IHP-Open-PDK/tree/main).

## General Setup:
The pre-existing simulation and synthesis setup can be run using the makefile in the root of the repo. Assume that you will always run simulations with the verilator
You can use
make verilator
to run a simulation, and 
make yosys 
to run synthesis.

There is also `make openroad` and `make klayout` if the tools are installed.

Note: for simulation always use verilator. vsim / modelsim / questasim are not installed.

## Repository Structure
RTL Code: 
- in rtl directory
- top level is `croc_chip.sv`
- testbench is `tb_croc_soc.sv`
Main Makefile:
- in project root
Constraints:
- in `openroad/src`
Readme:
- readme.md

## Memory Map

The address map of the default configuration is as follows:

| Start Address   | Stop Address    | Description                                |
|-----------------|-----------------|--------------------------------------------|
| `32'h0000_0000` | `32'h0004_0000` | Debug module (JTAG)                        |
| `32'h0300_0000` | `32'h0300_1000` | SoC control/info registers                 |
| `32'h0300_2000` | `32'h0300_3000` | UART peripheral                            |
| `32'h0300_5000` | `32'h0300_6000` | GPIO peripheral                            |
| `32'h0300_A000` | `32'h0300_B000` | Timer peripheral                           |
| `32'h1000_0000` | `+SRAM_SIZE`    | Memory banks (SRAM)                        |
| `32'h2000_0000` | `32'h8000_0000` | Passthrough to user domain                 |
| `32'h2000_0000` | `32'h2000_1000` | reserved for string formatted user ROM*    |
