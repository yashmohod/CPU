# 🖥️ Single-Cycle & Multi-Cycle CPU Simulation  
*A COMP 370 Computer Architecture Project*

---

## 📌 Overview  
This project implements two 32-bit CPU architectures inside a digital logic simulation environment:

- **Single-Cycle CPU**
- **Multi-Cycle CPU**

Both CPUs follow the same instruction set, but their internal execution models differ significantly.  
The simulation includes **instruction memory**, **data memory**, a **decoder**, **ALU**, **control logic**, and support modules such as a manual **programming interface** and **clock system**.

The goal is to illustrate how different CPU designs execute the same instructions while varying in speed, complexity, and control-flow behavior.

---

# 🧩 Architecture 1: Single-Cycle CPU

## 🔍 Summary  
The single-cycle CPU executes **every instruction in one clock cycle**, following these four stages:

1. **Fetch**  
2. **Decode**  
3. **Execute**  
4. **Store**  

All steps occur within the same cycle, meaning each instruction takes identical time regardless of complexity.

---

## 🛠 Key Components  

### **Programming Module**  
Allows instructions to be manually encoded into instruction memory before execution.

### **Clock / Memory Viewer**  
Can toggle between live clocked execution and manual examination of memory values.

### **Decoder**  
Converts instruction bits into control signals that route values across internal buses.

### **Execute Unit (ALU + Control)**  
Combined into one module due to the single-cycle design, where every instruction follows the same datapath.

### **Data Memory + Register File**  
- Register file stores *persistent* values  
- Data memory stores *temporary* values  
- Both appear as a single module in the simulation

---

## 💡 Notes  
- Single-cycle CPUs are simple but inefficient in real hardware.  
- All instructions — even simple ones — must wait for the slowest operation.  
- Great for educational purposes, poor for real performance.

---

# 🧩 Architecture 2: Multi-Cycle CPU

## 🔍 Summary  
The multi-cycle CPU divides instruction execution into multiple smaller, optimized cycles.  
Benefits include:

- Faster instructions do not wait on slower ones  
- Propagation delays across logic units matter  
- Control flow becomes more flexible  
- Better reflects real-world CPU architecture

This design is **more realistic** than the single-cycle CPU.

---

## 🛠 Key Components  

### **Instruction Register + Step-by-Step Fetching**
- Cycle 1: Fetch instruction  
- Cycle 2: Latch instruction  
- Following cycles depend on instruction type  

### **Control Unit (More Complex)**  
- Coordinates multi-cycle execution  
- Must handle different step counts for different instructions  

### **Independent Instruction Stages**  
Arithmetic, logical, data transfer, and conditional instructions may each require a unique number of cycles.

### **Efficiency**  
Eliminates the forced “one-long-cycle” of the single-cycle CPU.

---

# 🧮 Instruction Set  
Supported by **both** CPUs:

## **Arithmetic**
- Add  
- Subtract  
- Multiply  
- Divide  
- Modulo  

## **Logical**
- And  
- Or  

## **Conditional**
- Equal To  
- Greater Than  
- Smaller Than  
- Jump If True  
- Jump If False  

## **Data Transfer**
- Move  
- Load Word  
- Store Word  
- Jump *(categorized here for convenience)*  

---

# 📘 Conclusion  
Both the **single-cycle** and **multi-cycle** CPUs implement the **same instruction set** and produce identical results, but differ internally:

| Feature | Single-Cycle | Multi-Cycle |
|--------|--------------|-------------|
| Execution Time | Fixed, one long cycle | Variable, optimized cycles |
| Complexity | Simple | More complex |
| Efficiency | Low | Much higher |
| Realism | Low (teaching use) | High (hardware-like) |

These simulations demonstrate how architectural choices affect CPU performance and control logic, forming a strong foundation for learning pipelining and advanced CPU design.

---


