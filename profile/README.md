# Unison Logic Systems

> **Deterministic Hardware-Software Interface (HSI) Verification, Virtual HIL Simulation & Formal Silicon IP**

---

### Overview

**Unison Logic Systems** is a deep-tech engineering and verification studio dedicated to bringing digital silicon implementation, physical board peripherals, and embedded firmware drivers into absolute unison.

Across modern FPGA and SoC development, processor-rich architectures are virtually universal: over **98% of FPGA and ASIC designs** embed at least one processor core. Yet functional verification remains heavily fragmented—resulting in over **98% of FPGA projects experiencing non-trivial bug escapes** into physical hardware bring-up and production.

We eliminate this schedule and quality crisis through a compounding chain of open-source-first, deterministic verification and simulation engines:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        THE UNISON VERIFICATION CAGE                    │
├────────────────────────────────┬───────────────────────────────────────┤
│ 1. HSI Semantic Assurance      │ Compiler-grade static cross-auditing  │
│                                │ of RTL decode logic vs. C/Rust headers│
├────────────────────────────────┼───────────────────────────────────────┤
│ 2. Pre-Silicon Virtual HIL     │ Auto-compiled Renode peripheral models│
│                                │ co-simulated with Verilator logic     │
├────────────────────────────────┼───────────────────────────────────────┤
│ 3. Protocol VIP-as-Code        │ Formal BMC & temporal induction for   │
│                                │ AXI4, APB, & TileLink via SymbiYosys  │
├────────────────────────────────┼───────────────────────────────────────┤
│ 4. Post-Silicon Triage         │ Automated waveform slicing & logic    │
│                                │ analyzer trace triage via MCAP        │
├────────────────────────────────┼───────────────────────────────────────┤
│ 5. Certified Silicon IP        │ Pre-verified, formally certified      │
│                                │ parametric hardware accelerator cores │
└────────────────────────────────┴───────────────────────────────────────┘
```

---

### Key Capabilities

#### 1. Hardware-Software Interface (HSI) Semantic Assurance
- **Reverse AST Extraction**: Deterministic static extraction of memory-mapped control/status registers (CSRs) from hand-written SystemVerilog RTL using `pyslang`.
- **Dead & Unwired Register Detection**: Combinational netlist fan-out graph analysis (via `slang-netlist`) flagging bus-accessible registers with zero functional downstream sinks.
- **Cross-Language Semantic Diffing**: Mathematical equivalence checking proving alignment across address offsets, bitfield widths, reset values, and `W1C` / `RO` access policies against C99/C11 firmware headers.

#### 2. Pre-Silicon Virtual HIL & Firmware Regression
- **Datasheet-to-Simulation Compilers**: Generating cycle-accurate C# peripheral simulation models for **Antmicro Renode** directly from sensor datasheets (IMUs, CAN-FD, flash).
- **MCU-to-RTL Co-Simulation**: Socket-based bridges linking Renode ARM Cortex-M/RISC-V cores with custom FPGA RTL in **Verilator**, executing unmodified production `.elf` firmware before PCB fabrication.
- **Corner-Case Fault Injection**: Deterministic CI simulation of I2C bus lockup, SPI bit-flip noise, CAN arbitration loss, and brownout resets.

#### 3. Formal Verification & VIP-as-Code
- **Open-Source Formal Engines**: Bounded model checking (BMC) and temporal induction using **SymbiYosys (SBY)** and SMT solvers (Z3, Boolector, Yices2).
- **Bus Integrity Monitors**: Parametric SystemVerilog Assertions (SVA) and Python Cocotb testbenches enforcing ARM AMBA AXI4, APB4, and TileLink compliance with zero deadlock guarantees.
- **Mutation Testing (MCY)**: Formally certifying assertion density and eliminating false-positive coverage holes.

---

### Open-Source Benchmark Corpus

We validate our tooling against real-world open-source silicon and FPGA codebases:

* **[kebag-logic/milan-fpga](https://github.com/kebag-logic/milan-fpga)**: Forensic analysis of hand-written CSR address divergence (`0x3810` vs `0x3818`) and unwired latency registers.
* **[chili-chips-ba/openPCIE](https://github.com/chili-chips-ba/openPCIE)**: Parameterized PCIe control register decode and packed struct alignment.
* **[pulp-platform/apb_gpio](https://github.com/pulp-platform/apb_gpio)**: APB bus decode and interrupt clearing verification.

---

### Enterprise & Air-Gapped Deployment

All Unison verification and simulation engines are built on a **local-first, zero-cloud architecture**:
- **100% Offline Execution**: Runs locally inside customer firewalls via reproducible Docker containers (`ghcr.io`).
- **Zero Third-Party Telemetry**: Proprietary RTL and driver source code never leave customer infrastructure.
- **Defense & Export Compliance**: Fully compliant with US EAR99 / ITAR data isolation boundaries.

---

### Connect with Us

- **Organization**: [Unison Logic Systems on LinkedIn](https://www.linkedin.com/company/unison-logic-systems/)
- **Inquiries & Audit Requests**: `unisonlogicsystems@gmail.com`
- **Location**: Bengaluru, India / Global

