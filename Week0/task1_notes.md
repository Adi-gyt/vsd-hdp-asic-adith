# Chip Design Flow — *Silicon Proven*

The chip design flow describes the complete journey of how a **software program** is ultimately realized as a **working silicon chip**.  
It starts from a high-level description, such as a C program, and goes through multiple levels of refinement — specification, hardware description, verification, and physical design — before finally being fabricated at a semiconductor foundry.  

At every stage, the outputs are checked against the original specification to ensure correctness. When the final silicon matches the intended behavior, the design is considered **“Silicon Proven.”**

---

## 🔹 Design Flow Steps

### 1. Application C Model (O0)
- Begin with a **C program** that represents the application.  
- Compile with `gcc -O0` (no optimizations).  
- Output = **Golden Reference Result (O0)**.  

---

### 2. Specification C Model (O1)
- Write a **specification/architectural C model** aligned with the processor architecture.  
- Defines how the application will behave on hardware.  
- Output = **O1**, which must match O0.  

---

### 3. RTL Design (O2)
- Translate the specification into **Verilog RTL** using synthesizable constructs.  
- Output = **O2**, which must match O1.  

---

### 4. RTL Partitioning
- Split the RTL into key components:  
  - **Processor Unit** — ISA, datapath, and control logic.  
  - **Peripherals/IPs**:  
    - *Digital Macro IPs* — reusable and synthesizable (e.g., UART, multiplier).  
    - *Analog IPs* — modeled in RTL for behavior (e.g., ADC, PLL), but not synthesizable.  

---

### 5. SoC Integration (O3)
- Combine the processor and peripherals into a complete **System-on-Chip (SoC)**.  
- Integrate buses, GPIOs, and interconnect.  
- Output = **O3**, which must match O2.  

---

### 6. Physical Design
- Convert RTL into a **Gate-Level Netlist** through logic synthesis.  
- Perform **Place & Route**, timing closure, and physical verification (DRC, LVS).  

---

### 7. GDSII Generation
- Generate the **GDSII file**, which contains all layout details (masks, layers, interconnect).  
- This is the file sent to the foundry for fabrication.  

---

### 8. Fabrication & Testing (O4)
- The foundry fabricates and packages the chip.  
- Test the silicon on hardware.  
- Output = **O4**, which must match all previous outputs.  

---

## ✅ Outputs at Each Stage
- **O0** → Application C output (golden reference)  
- **O1** → Specification model output  
- **O2** → RTL output  
- **O3** → SoC integration output  
- **O4** → Final silicon output  

 If O0 = O1 = O2 = O3 = O4 → the design is **Silicon Proven** ✔  

---
