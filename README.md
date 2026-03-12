# Experiment 4: Timing Validation of Flip-Flop Input using Random Data Generator for Setup and Hold Constraints

---

## Aim  
To validate the **timing of a Flip-Flop input** using **random data generation** in **SystemVerilog** and check **setup and hold constraints** using **ModelSim 2020.1**.

---

## Apparatus Required  
- Computer with **Windows OS**  
- **ModelSim 2020.1** (or later)  
- SystemVerilog source code editor  

---

## Description  
Timing validation ensures that a Flip-Flop operates correctly under all input conditions.  
- **Setup time:** Minimum time before the clock edge that the data input must be stable.  
- **Hold time:** Minimum time after the clock edge that the data input must remain stable.  

In this experiment:  
- A **random data generator** is used to drive the Flip-Flop input.  
- **SystemVerilog constructs** like `randomize()` and `class` or `logic` vectors can be used to generate test data.  
- Simulation is used to observe **violations or adherence** to setup and hold constraints.  

---

## Features  
- Flip-Flop timing validation using **random inputs**  
- Checks for **setup and hold constraints**  
- Includes a **testbench** for verification  
- Compatible with **ModelSim 2020.1**  

---

## Procedure  

1. **Open ModelSim 2020.1**  
   - Launch the IDE.  

2. **Create a New Project**  
   - `File → New → Project`  
   - Name it `FlipFlop_Timing_Project`.  

3. **Add SystemVerilog Files**  
   - Create `flipflop.sv` → Flip-Flop design  
   - Create `flipflop_tb.sv` → Testbench with random input generator  

4. **Compile the Design and Testbench**  
   - Select both files, right-click → **Compile Selected**  
   - Resolve any syntax errors  

5. **Start Simulation**  
   - `Simulate → Start Simulation`  
   - Select testbench module (`flipflop_tb`)  

6. **Add Signals to Waveform**  
   - Select clock, data, and output signals  
   - Right-click → **Add to → Wave → Selected Signals**  

7. **Run Simulation**  
   - Type in console:  
     ```
     run 200ns
     ```  
   - Or use **Run button**  

8. **Analyze Waveforms**  
   - Check setup and hold times at the Flip-Flop input  
   - Verify Flip-Flop output stability for all random input patterns  

9. **Save Results**  
   - Save waveform (`.wlf`) for documentation  

---

## SystemVerilog Code Skeleton  

### Flip-Flop Design (`flipflop.sv`)
```systemverilog
module flipflop (
    input  logic D,       // Data input
    input  logic CLK,     // Clock
    output logic Q        // Flip-Flop output
);

    // Implement Flip-Flop behavior
    // Include D flip-flop logic
endmodule
```
### Testbench (`flipflop_tb.sv`)
```systemverilog
module flipflop_tb;

    // Declare signals
    logic D, CLK;
    logic Q;

    // Instantiate Flip-Flop
    flipflop uut (
        .D(D),
        .CLK(CLK),
        .Q(Q)
    );

    // Random input generation and clock
    initial begin
        CLK = 0;
        forever #5 CLK = ~CLK; // Clock generation
    end

    initial begin
        // Apply random data to D
        // Example:
        // repeat(20) begin
        //   D = $urandom_range(0,1);
        //   #10;
        // end
        $stop; // End simulation
    end

endmodule
```
---
### Simulation Output

Simulation is carried out using ModelSim 2020.1.

Waveforms will show Flip-Flop input, clock, and output.

Verify setup and hold constraints for all random input patterns.

<img width="1018" height="546" alt="image" src="https://github.com/user-attachments/assets/38f7cd53-fdbd-4d96-9f28-8db6e5bedba3" />


---

### Result

The timing validation of Flip-Flop input using random data generation was successfully carried out in SystemVerilog HDL with ModelSim 2020.1.
The Flip-Flop maintained correct output behavior, and setup and hold times were verified for all random input cases.
