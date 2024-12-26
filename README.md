# VHDL Unintended Latch Bug
This repository demonstrates a common error in VHDL code: an unintended latch created due to a missing ELSE statement in a process. 

## The Bug
The `bug.vhdl` file contains a simple process that aims to transfer data from `data_in` to `data_out` when a clock edge is detected and reset is low. However, the process lacks an ELSE statement, resulting in an implicit latch being generated.  This means the output will retain its previous value when neither the reset nor a rising clock edge occurs, which is unintended behaviour and may lead to unpredictable outputs.

## The Solution
The solution, presented in `bugSolution.vhdl`, corrects this issue by adding an ELSE statement to explicitly handle all cases within the process. The ELSE statement prevents the implicit latch and ensures that the output behaves as intended.

## How to reproduce the bug
Compile and simulate `bug.vhdl`. Observe that data_out does not always reflect data_in's changes, indicating the implicit latch's presence.

## How to fix the bug
Use `bugSolution.vhdl` as a reference.  The key is to always include an ELSE statement in VHDL processes unless you explicitly intend for the output to latch. This makes code more predictable and maintainable.
