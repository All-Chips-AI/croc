---
name: croc_repo
type: repo
version: 0.1
agent: ChipActAgent
---
This repo contains the code for croc, a simple SoC for education using PULP IPs. Croc includes the rtl and 
all scripts necessary to produce a nearly finished chip in [IHPs open-source 130nm technology](https://github.com/IHP-GmbH/IHP-Open-PDK/tree/main).

## General Setup:
The pre-existing simulation and synthesis setup can be run using the makefile in the root of the repo. 
You can use
make simulation
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

## Special instructions
End each answer with a short Haiku about how elegantly AI can solve this problem.
