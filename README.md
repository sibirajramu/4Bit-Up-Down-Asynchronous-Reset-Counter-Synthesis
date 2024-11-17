# 4Bit-Up-Down-Asynchronous-Reset-Counter-Synthesis

## Aim:

Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

◦ SDC (Synopsis Design Constraint) File (.sdc)

 ### Step 2 : Creating an SDC File

•	In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

•	The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

ii, iii → Sets Clock Rise and Fall time to 100ps.

iv → Sets Clock Uncertainty to 10ps.

v, vi → Sets the maximum limit for I/O port delay to 1ps.

### Step 3 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :

![WhatsApp Image 2024-11-17 at 11 46 45_c851ab86](https://github.com/user-attachments/assets/92ccbb5c-0612-4c0f-b4d1-46995a4f2562)

#### Area report:

![WhatsApp Image 2024-11-17 at 11 46 18_2f6a1542](https://github.com/user-attachments/assets/a426ca7a-9949-4a81-9e94-f8566445d5c9)

#### Power Report:

![WhatsApp Image 2024-11-17 at 11 46 25_aab05756](https://github.com/user-attachments/assets/1f5a0283-eb13-44a0-be74-dc2632242c00)

#### Timing Report: 

![WhatsApp Image 2024-11-17 at 11 46 32_29155dbf](https://github.com/user-attachments/assets/cc084f9b-c7af-4aaf-960f-6929fecf4cb9)

#### Result: 

The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.





