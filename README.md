ASIC-Ready 8-Bit Register Design

This project implements a full-custom 8-bit register in Cadence Virtuoso as a building block for an 8-bit computer architecture. The design was developed from transistor-level circuits and completed through schematic design, layout implementation, post-layout verification, and timing analysis.
The register supports bidirectional interaction with a shared system bus through dedicated read and write control signals and incorporates tri-state buffering for bus isolation.

A. Features

-Stores 8 bits of data
-Rising-edge-triggered operation
-Built using master-slave D Flip-Flops
-BUS0 to BUS7 : Shared data bus inputs
-A0 to A7 : Register outputs to ALU
-W : Write Enable
-R : Read Enable
-CLK : Clock Input
-RESET : Synchronous Reset
-Total Pins: 20

B. Functional Description

1) Write Operation:-
   
When the Write Enable (W) signal is active:-
Data present on BUS[7:0] is loaded into the register
Data is captured on the rising edge of the clock

When W is inactive:-
The register retains its previously stored value

2) Read Operation

When the Read Enable (R) signal is active:-
Stored data is driven onto the shared system bus through tri-state buffers

When R is inactive:-
Outputs enter a High-Impedance (Z) state
Bus contention is avoided

3) Reset Operation
A synchronous reset signal clears all stored bits and initializes the register to zero.

Design Hierarchy
The complete register was developed hierarchically from reusable transistor-level building blocks.
1-Bit Register Cell
The 1-bit register consists of:
D Flip-Flop with Reset
Tri-State Buffer
NAND Gates
Inverter
Hierarchy:
D_latch → D_ff_using_latch → D_ff_reset → 1_bit_register

Layout Implementation
1-Bit Register Layout
The basic register cell integrates:
D Flip-Flop
Tri-State Buffer
Control Logic
Routing and Power Rails
8-Bit Register Layout
The complete 8-bit register was created by replicating and integrating eight verified 1-bit register cells.
The final layout includes:
Shared control lines
Bus routing
Output routing
Clock distribution network

Verification Flow
The design was verified through:
Functional Simulation
Layout Design
Design Rule Check (DRC)
Layout Versus Schematic (LVS)
Post-Layout Simulation

Timing Results
Stage
Delay
Pre-Layout Simulation
0.34 ns
Post-Layout Simulation
0.81 ns

The increase in delay after extraction reflects realistic parasitic effects introduced by interconnects and layout routing.

Tools Used
Cadence Virtuoso
Spectre Simulator

Learning Outcomes
Full-custom digital IC design
Master-Slave D Flip-Flop implementation
Tri-State Bus Architecture
Layout design and routing
DRC and LVS verification
Post-layout timing analysis
Hierarchical ASIC design methodology

Future Improvements
Clock-gating for reduced power consumption
Multi-register bank implementation
Integration with ALU and control unit
Complete ASIC implementation of an 8-bit processor
