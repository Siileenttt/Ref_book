# Electronics → Embedded → PCB → Robotics
## A 52-Week, 5-Hours-a-Day Plan (Beginner → Industry Engineer)

**Total commitment:** 5 h/day × 6 days/week × 52 weeks = **1,560 focused hours.**
Sunday is deliberately off (or light review). Burnout kills more self-taught engineers than difficulty does.

---

# 0. How to Use This Plan

## 0.1 The Daily 5-Hour Template

| Block | Time | What |
|---|---|---|
| **A — Theory** | 90 min | One book chapter / lecture. Active notes only: redraw every circuit by hand, derive every equation once. No passive video watching. |
| **B — Problems** | 30 min | 5–10 numerical problems or a simulation task. If you can't calculate it, you don't know it. |
| **C — Build** | 120 min | Hands on hardware: breadboard, scope, code, layout. This is the block that actually makes you an engineer. |
| **D — Datasheet drill** | 30 min | Read one real datasheet/app-note. Extract: abs-max ratings, operating conditions, key spec, one design pitfall. Write 5 lines about it. |
| **E — Log + recall** | 30 min | Update your engineering logbook, push to git, Anki review of yesterday's facts. |

**Hard rules**
1. Block C never gets skipped. If time is short, cut Block A instead.
2. Everything you build goes in a git repo with a README, schematic, photos, and measured results.
3. Every week ends with one artifact you could show an interviewer.
4. Simulate → build → measure → explain the difference. The gap between sim and reality *is* the education.
5. When you get stuck >45 min, write down the exact question, move on, and return to it the next morning.

## 0.2 Weekly Rhythm

- **Mon–Fri:** the daily template above.
- **Saturday:** 5 h project integration day — no new theory, just finish the week's deliverable and document it.
- **Sunday:** off, or 60 min review of the week's Anki deck + read one engineering blog/teardown.

## 0.3 Assessment Gates

You may **not** advance to the next phase until you pass the gate. Gates are pass/fail and self-administered honestly.

| Gate | After Week | Test |
|---|---|---|
| G1 | 8 | Design, build, and measure an analog circuit to a written spec, with LTspice sim matching hardware within 10%. |
| G2 | 13 | A physically manufactured PCB in your hand that works. |
| G3 | 21 | Bare-metal firmware (no vendor HAL) with UART + SPI + DMA + interrupts, debugged over SWD. |
| G4 | 26 | Your own 4-layer board running your own firmware, brought up from bare PCB in one sitting. |
| G5 | 34 | RTOS-based multi-node system with OTA update and a CI-run unit test suite. |
| G6 | 39 | A controlled-impedance high-speed board with a written SI/PI/EMC justification. |
| G7 | 48 | An autonomous robot on your own hardware doing a real task. |
| G8 | 52 | A complete design package a manufacturer could build from without asking you a question. |

---

# 1. Gear & Budget

Buy in phases. Do **not** buy everything on day one.

## Phase 1 (Week 1) — ~$350–600
- Digital oscilloscope, 100 MHz, 2ch (Rigol DHO804/DS1054Z, Siglent SDS1104X-E) — *the single most important purchase*
- Bench PSU, 0–30 V / 0–5 A, adjustable current limit (Korad KA3005P or similar)
- Decent DMM (Brymen BM235, Owon, or Fluke 101 minimum)
- Soldering station with temperature control (Hakko FX-888D, Pinecil V2, or T12 clone)
- Flux (no-clean gel), solder wick, tweezers, IPA, 63/37 leaded solder 0.6 mm
- Breadboards, jumpers, DuPont wire, resistor/cap/LED kits, THT transistor kit
- Helping hands + USB microscope (a $40 one is transformative for SMD)

## Phase 2 (Week 9) — ~$150
- Logic analyzer (Saleae clone 8ch, or better: a DSLogic Plus)
- Function generator (or use scope's built-in AWG)
- Cheap FPGA board: Tang Nano 9K (~$15) or iCEBreaker
- SMD practice kit + hot air rework station (858D) or mini reflow plate

## Phase 3 (Week 14) — ~$120
- STM32 Nucleo (F411 / G474) + Blue Pill + ESP32-S3 + RP2040
- ST-Link V2 / J-Link EDU / DAPLink
- Sensor kit: MPU6050 or ICM-42688, BME280, W25Q SPI flash, SSD1306 OLED, SD card module
- USB-to-UART (CP2102/FT232)

## Phase 4 (Week 22) — ~$150–300
- 2–3 PCB fab runs (JLCPCB: ~$5–30/board incl. assembly for small designs)
- Stencil + solder paste + tweezer set if hand-assembling
- Precision multimeter leads, current clamp / µCurrent for power measurement

## Phase 5 (Week 32) — ~$120
- Raspberry Pi 4/5 or BeagleBone Black, SD cards, USB-TTL console cable
- CAN transceiver boards + USB-CAN adapter (canable/candleLight)
- BLE dongle / nRF52840 dongle

## Phase 6 (Week 35) — ~$200 (optional but valuable)
- Near-field probe set + cheap spectrum analyzer (TinySA Ultra) for EMI pre-scan
- VNA (NanoVNA V2) for impedance/RF sanity checks

## Phase 7 (Week 40) — ~$250–500
- 2× brushed gearmotors with quadrature encoders, or 2× BLDC gimbal motors + SimpleFOC driver
- Robot chassis, LiPo/Li-ion pack + BMS + charger
- RPLidar A1 (~$100), USB camera, ToF sensor (VL53L1X)

**Total across the year: ~$1,300–2,000.** Every item is reusable for a career. Buy the scope and the soldering iron good; buy everything else cheap.

## Free software stack (install as you go)
`LTspice` / `ngspice` · `KiCad 8+` · `arm-none-eabi-gcc` + `CMake` + `OpenOCD` · `STM32CubeMX` (for clock/pin reference only) · `FreeRTOS` · `Zephyr` + `west` · `PlatformIO` · `Icarus Verilog` + `GTKWave` + `Verilator` · `Saturn PCB Toolkit` · `ROS 2 Jazzy/Kilted` + `Gazebo` · `Python` (numpy/scipy/matplotlib/control) · `Docker` · `git`

---

# 2. Core Book List (one per phase — do not buy all at once)

| Phase | Primary | Secondary / Reference |
|---|---|---|
| Fundamentals | *Practical Electronics for Inventors* — Scherz & Monk | *All About Circuits* (free online) |
| Analog | *The Art of Electronics* 3rd ed. — Horowitz & Hill (Ch 1–5) | *Op Amps for Everyone* (TI, free PDF) |
| Digital | *Digital Design and Computer Architecture* — Harris & Harris | *Digital Design* — Mano |
| Embedded | *Mastering STM32* — Noviello **or** *Making Embedded Systems* — White | ARM Cortex-M Generic User Guide; *Embedded C Coding Standard* — Barr |
| RTOS | *Mastering the FreeRTOS Kernel* (free) | Zephyr docs |
| PCB | *PCB Design Guidelines* + Rick Hartley's lectures (free, watch 3×) | *Printed Circuits Handbook* — Coombs |
| SI/PI/EMC | *High-Speed Digital Design* — Johnson & Graham | *Signal and Power Integrity — Simplified* — Bogatin; *EMC for Product Designers* — Williams |
| Power | *Fundamentals of Power Electronics* — Erickson | TI/ADI power app notes |
| Control | *Feedback Systems* — Åström & Murray (free PDF) | *Modern Control Engineering* — Ogata |
| Robotics | *Modern Robotics* — Lynch & Park (free PDF + Coursera) | *Probabilistic Robotics* — Thrun |
| Industry | *The Hardware Startup* / IPC-2221, IPC-7351, IPC-A-610 standards | Company design guides (TI, ADI, ST, Nordic) |

**Free video courses worth the time:** MIT 6.002, Neso Academy (digital), Phil's Lab (KiCad + hardware design), Rick Hartley "How to Achieve Proper Grounding", Robert Feranec (PCB/SI), Ben Eater (digital logic from scratch), Northwestern *Modern Robotics* on Coursera.

---

# PHASE 1 — ELECTRICAL FUNDAMENTALS
### Weeks 1–4 · 120 hours · Goal: you can predict what a circuit will do before you build it

## Week 1 — DC Circuit Analysis + Lab Setup
**Theory:** Charge, current, voltage, EMF. Ohm's law. Power & energy (P = VI, I²R). Resistors: E-series values, tolerance, power rating, derating, temperature coefficient. Series/parallel reduction. Voltage divider (loaded vs unloaded — the #1 beginner trap). Current divider. Kirchhoff's Current & Voltage Laws. Nodal analysis. Mesh analysis. Ideal vs real voltage/current sources, internal resistance.

**Build (Block C):**
- Day 1–2: Set up the bench. Learn your scope: probe compensation, 1×/10×, AC/DC/GND coupling, trigger modes (edge, level, auto vs normal), timebase, vertical scale, measurements, cursors. **This is a skill, spend the full 4 hours.**
- Day 3: DMM technique — 4-wire vs 2-wire resistance, burden voltage when measuring current, continuity, diode test, why you blew the fuse.
- Day 4: Build 6 resistor networks. Predict → measure → explain error.
- Day 5: Loaded voltage divider. Watch the output sag as you add load. Derive why.
- Day 6 (Sat): Write your first lab report: hypothesis, method, table of predicted vs measured, error analysis.

**Datasheet drills:** a standard 1/4 W resistor, a Vishay thick-film chip resistor, a 5 mm LED.

**Deliverable:** Lab report #1 in your git repo, with photos and a scope screenshot.

---

## Week 2 — Network Theorems, Capacitors, Inductors, Transients
**Theory:** Superposition. Thévenin & Norton equivalents (derive both directions). Source transformation. Maximum power transfer and when you *don't* want it. Capacitors: Q = CV, i = C dv/dt, energy, dielectric types (C0G/NP0, X7R, X5R, Y5V — and DC bias derating, which surprises everyone). ESR, ESL, self-resonant frequency. Electrolytic vs ceramic vs film vs tantalum. Inductors: v = L di/dt, energy, saturation current vs RMS current, DCR, core materials. RC and RL first-order transients, time constant τ, 5τ rule, step response.

**Build:**
- Thévenin-ize a real 3-resistor network; verify with a load sweep.
- Scope an RC charging curve; measure τ from the 63.2% point; compare to RC.
- Measure a "10 µF" X5R ceramic's actual capacitance at 0 V and at rated voltage bias (use an LCR meter or a resonance trick). Be shocked.
- Measure inductor saturation: drive with a current ramp, watch di/dt change.
- Install **LTspice**. Simulate everything above. Learn `.tran`, `.ac`, `.dc`, `.step`, `.meas`.

**Datasheet drills:** Murata GRM series MLCC (find the DC bias curve), a Würth power inductor, a Nichicon electrolytic (find ripple current rating and lifetime hours).

**Deliverable:** LTspice library of 8 sims + measured-vs-simulated comparison table.

---

## Week 3 — AC, Impedance, Filters, Frequency Domain
**Theory:** Sinusoids: amplitude, frequency, phase, period. RMS vs peak vs average (and RMS of non-sinusoids). Complex numbers & phasors. Impedance and admittance. Reactance of C and L. Series/parallel RLC, resonance, Q factor, bandwidth. Transfer functions H(jω). Decibels (20log vs 10log — know when each applies). Bode plots: poles, zeros, −20 dB/decade, corner frequency, phase shift. First-order LPF/HPF, second-order responses, Butterworth/Chebyshev/Bessel character. Fourier idea: square waves = sum of harmonics.

**Build:**
- Function generator basics; measure RMS of sine, square, triangle with your DMM (true-RMS vs average-responding — critical lesson).
- Build an RC LPF. Sweep frequency manually 10 Hz → 1 MHz, plot gain & phase, overlay LTspice `.ac` sim.
- Build a series RLC, find resonance, measure Q by −3 dB bandwidth.
- Feed a square wave through an LPF and watch the harmonics get eaten.
- Learn scope FFT mode.

**Datasheet drills:** a common-mode choke, a ferrite bead (find the impedance-vs-frequency curve — beads are resistors, not inductors, above resonance).

**Deliverable:** Hand-plotted + simulated Bode plot pair.

---

## Week 4 — Real Components, Soldering, Magnetics
**Theory:** Parasitics everywhere: every capacitor is an RLC, every inductor has capacitance, every wire has inductance (~1 nH/mm). Package types: 0402/0603/0805/1206, SOT-23, SOIC, TSSOP, QFN, BGA. Thermal: junction temperature, θJA/θJC, derating curves. Transformers: turns ratio, isolation, leakage inductance. Relays, fuses, PTCs, connectors, crimping.

**Build (this week is 60% hands-on):**
- Soldering progression: THT resistors → THT IC socket → SMD 1206 → 0805 → 0603 → 0402 → SOIC → TSSOP → QFN with hot air. Buy a $8 practice kit and do all of it.
- Learn desoldering: wick, solder sucker, hot air, low-melt alloy.
- Solder a permanent perfboard version of your Week 3 filter with a proper enclosure and connectors.
- Inspect every joint under the microscope. Learn what cold joints, tombstoning, and bridges look like.

**Datasheet drills:** an SMD package drawing (learn to read land pattern dimensions), an IPC-7351 land pattern doc.

### ⛳ Milestone 1
A soldered, enclosed, switchable RC/RLC filter board, plus a written report with measured vs LTspice Bode plots and a paragraph explaining every discrepancy.

---

# PHASE 2 — ANALOG ELECTRONICS
### Weeks 5–8 · 120 hours · Goal: you can design a signal chain and a power supply

## Week 5 — Diodes & Protection
**Theory:** PN junction, I/V curve, Shockley equation, forward drop vs current & temperature. Rectifiers: half-wave, full-wave, bridge; ripple voltage and filter cap sizing (ΔV = I·t/C); peak repetitive current. Zener diodes and shunt regulation. Schottky: low Vf, reverse leakage, thermal runaway. Flyback/freewheel diode for inductive loads. TVS diodes, clamping voltage, standoff, ESD (IEC 61000-4-2 waveform). Reverse-polarity protection: series diode vs P-FET vs ideal diode controller. Inrush limiting (NTC, soft-start). Charge pumps, voltage doublers.

**Build:** Bridge rectifier + cap filter from a 12 V AC transformer or signal generator. Measure ripple vs load and vs C. Add a Zener shunt reg, measure line/load regulation and see it fail under load. Build a P-FET reverse-polarity protector and test it. Scope the inductive kick from a relay coil with and without a flyback diode.

**Datasheet drills:** 1N4148, 1N5819, SMAJ series TVS, a P-channel MOSFET for polarity protection.

---

## Week 6 — Transistors: BJT & MOSFET
**Theory (BJT):** Structure, β/hFE and why you never trust it, active/saturation/cutoff regions, VBE ≈ 0.7 V and its −2 mV/°C tempco. Biasing (voltage divider bias, emitter degeneration). Common-emitter, common-collector (emitter follower), common-base. Small-signal model (re, gm, rπ). Current mirrors. Differential pairs. Darlington & Sziklai. Saturation for switching, base resistor sizing.

**Theory (MOSFET):** Enhancement vs depletion, VGS(th), transfer curve, Rds(on) vs VGS and vs temperature, ohmic vs saturation region, body diode. Gate charge Qg, Miller plateau, switching losses (E = ½·V·I·t·f), gate drivers, gate resistors, dV/dt issues. High-side vs low-side switching, bootstrapping, level shifting. SOA curves. Load switches, ideal diode ORing, back-to-back FETs.

**Build:** CE amplifier — bias it, measure gain, input/output impedance, distortion at clipping. Emitter follower buffer driving a low-Z load. N-FET low-side switch driving a motor: scope the gate and drain, measure rise/fall, calculate switching loss, then add a gate resistor and watch it change. Build a high-side P-FET load switch with soft-start.

**Datasheet drills:** 2N3904, BC847, IRLZ44N, AO3400, a modern logic-level MOSFET (find Qg, Rds(on) @ 4.5 V, SOA).

---

## Week 7 — Op-Amps & Signal Conditioning
**Theory (ideal):** Golden rules, virtual short. Inverting, non-inverting, buffer, summing, difference, integrator, differentiator, log amp. Instrumentation amplifier (3-op-amp topology and why the ratio matching matters). Active filters: Sallen-Key, multiple-feedback, state-variable; filter design from spec. Comparators vs op-amps (never confuse them), hysteresis / Schmitt trigger design, open-drain outputs. Oscillators: relaxation, Wien bridge, phase shift, 555 timer astable/monostable. Precision rectifier, peak detector, sample & hold, current sense amps (high-side vs low-side, shunt sizing).

**Theory (real):** Open-loop gain and GBW product, slew rate, input offset voltage & drift, input bias & offset current, CMRR, PSRR, output swing / rail-to-rail limits, input common-mode range, noise (voltage noise density, current noise, 1/f corner, noise gain), stability with capacitive load, phase margin, isolation resistor + feedback cap compensation.

**Build:** Non-inverting amp — measure gain vs frequency, find your GBW empirically. Deliberately build an unstable buffer driving a capacitive load; scope the ringing; fix it. Build a 2nd-order Sallen-Key LPF to a spec you write yourself. Build a complete sensor front end: thermistor or load cell → instrumentation amp → anti-alias filter → 0–3.3 V output. Build a Schmitt trigger and measure the hysteresis window.

**Datasheet drills:** LM358 (learn why it's mediocre), TL072, OPA2340, INA219/INA226, LM393.

---

## Week 8 — Power Electronics, Noise & Grounding
**Theory:** Linear regulators: dropout, quiescent current, PSRR vs frequency, stability & required output cap ESR, thermal calculation (P = (Vin−Vout)·I, then Tj = Ta + P·θJA). LDO vs SMPS trade-offs. Switching topologies: buck, boost, buck-boost, SEPIC, flyback, isolated. CCM vs DCM, duty cycle relationships, inductor ripple current (30–40% rule), output cap selection for ripple and transient, switching frequency trade-offs. Synchronous vs asynchronous. Control modes: voltage mode, current mode, hysteretic; loop compensation and phase margin. Efficiency: conduction, switching, core, gate-drive losses.

**Noise & grounding (start early, it pays for the whole career):** Ground is not a node, it's a network. Return current follows the path of least *impedance* (not resistance) — under a trace at high frequency. Loop area = antenna. Star ground vs ground plane. Analog/digital partitioning (and why splitting planes is usually wrong). Decoupling: why 100 nF, why local, why the loop from cap to pin matters more than the value. Common-mode vs differential-mode noise.

**Build:** Design and build a bench supply: transformer/DC input → bridge → bulk cap → buck pre-regulator → LDO post-regulator → adjustable output 0–12 V @ 1 A with a current limit and short-circuit protection. Measure: line regulation, load regulation, output ripple (use a proper ground-spring probe tip, not the 6-inch ground lead!), load transient response, efficiency vs load, thermal rise with an IR thermometer.

**Datasheet drills:** AMS1117 (and why you should stop using it), TPS7A47, LM2596 vs TPS54331, a modern synchronous buck like TPS62840.

### ⛳ Milestone 2 / GATE G1
Working, documented, enclosed bench supply. Design doc includes: spec, topology choice rationale, component calculations, LTspice sim, measured performance table, and three things you'd change in v2.

---

# PHASE 3 — DIGITAL ELECTRONICS + FIRST PCB
### Weeks 9–13 · 150 hours · Goal: you understand digital as an analog phenomenon, and you've made a real board

## Week 9 — Combinational Logic & Logic Families
**Theory:** Binary, hex, octal, BCD, Gray code. Signed representations: sign-magnitude, one's & two's complement, overflow detection. Fixed-point Q formats. Boolean algebra, De Morgan, SOP/POS, Karnaugh maps up to 5 variables, don't-cares, hazards/glitches. Building blocks: multiplexers, demux, encoders, priority encoders, decoders, comparators, half/full adders, ripple-carry vs carry-lookahead, ALU. Logic families: 74HC vs 74HCT vs 74LVC vs 74AHC, CMOS vs TTL thresholds, VIH/VIL/VOH/VOL, noise margin, unconnected input hazard, fan-out, drive strength, propagation delay, tPLH/tPHL, open-drain/open-collector, wired-AND, pull-up sizing (speed vs power), bus contention, tri-state, level shifting (resistor divider, FET-based, dedicated translator).

**Build:** Build a 1-bit full adder from discrete gates, then chain 4 of them. Measure propagation delay on the scope and watch a glitch appear on the carry chain. Build a 74HC + 3.3 V/5 V level-shift interface and prove where it fails. Measure CMOS input current when you leave a pin floating.

---

## Week 10 — Sequential Logic, Timing & Memory
**Theory:** SR latch, D latch, D flip-flop, JK, T. Setup and hold time, clock-to-Q, and how they set your maximum clock frequency. Timing analysis of a register-to-register path. Clock skew and jitter. Metastability, MTBF, two-flop synchronizers, clock domain crossing, handshakes, async FIFOs. Counters (ripple vs synchronous), shift registers, LFSRs. Finite state machines: Moore vs Mealy, one-hot vs binary encoding, state transition tables, safe state design. Memory: SRAM cell, DRAM refresh, NOR vs NAND flash, page/block erase, wear leveling, EEPROM endurance, FRAM/MRAM, memory maps, address decoding.

**Build:** Build a synchronous counter with 74HC163s. Build an FSM (traffic light or vending machine) with discrete logic. Deliberately violate setup time by overclocking and observe metastable output on the scope. Interface a 74HC595 shift register to drive 8 LEDs.

---

## Week 11 — Mixed Signal: ADC & DAC
**Theory:** Sampling theorem, Nyquist, aliasing (and how to demonstrate it), anti-aliasing filter design, oversampling & decimation (each 4× oversample = +1 bit). Quantization noise, LSB size, SNR = 6.02N + 1.76 dB, ENOB, SINAD, THD, SFDR, INL/DNL, missing codes, offset & gain error. ADC architectures: flash, SAR, sigma-delta, pipeline, dual-slope — and when each is right. Sample & hold, aperture jitter, input impedance & source impedance limits, charge injection, multiplexed sampling settling. Voltage references: bandgap, buried Zener, initial accuracy, tempco (ppm/°C), noise. DACs: R-2R, string, current-steering, PWM+filter as a DAC, glitch energy, reconstruction filters.

**Build:** Sample a signal above Nyquist and watch aliasing on the scope. Build an RC anti-alias filter for a 1 kSPS system. PWM + RC filter as a 8-bit DAC — measure ripple and settling. Read an external SPI ADC (ADS1115 or MCP3008) and characterize its noise floor by taking 10,000 samples of a shorted input and plotting the histogram.

---

## Week 12 — HDL & FPGA Fundamentals
**Theory:** Why HDL is not programming — it's structural description. Verilog syntax: modules, ports, wire vs reg, blocking (`=`) vs non-blocking (`<=`) and the rule for when to use each, `always @(*)` vs `always @(posedge clk)`, parameters, generate. Synthesizable vs non-synthesizable constructs. Inferring latches (and why it's a bug). Testbenches, stimulus, assertions, waveform inspection. Synthesis → place & route → bitstream flow. Timing constraints (SDC basics), critical path, Fmax. FPGA fabric: LUTs, flip-flops, block RAM, DSP slices, clock trees & PLLs, I/O standards.

**Build:** Toolchain: Icarus Verilog + GTKWave for sim, then Yosys/nextpnr (open source) or vendor tool for a Tang Nano 9K / iCEBreaker / Basys3.
- Blinky (clock divider)
- Debounced button + LED toggle FSM
- 7-segment display multiplexer
- **UART transmitter and receiver in Verilog** — verify with a real USB-serial adapter
- PWM generator with a duty-cycle register

---

## Week 13 — Your First PCB (KiCad, start to finish)
**Theory:** The PCB workflow: requirements → block diagram → schematic → part selection → footprint → layout → DRC → fab output → order → assemble → bring up. Schematic conventions: power flags, net labels, off-page connectors, decoupling near every IC, test points, reference designators, values vs MPN, DNP parts. Layer stackup for 2-layer. Copper pours. Design rules: trace width, clearance, annular ring, drill sizes, min via. Gerber + drill + BOM + centroid (CPL) files. Fab capability tables.

**Build (this whole week is one project):**
Design **"Board v1"** — deliberately simple, deliberately useful:
- USB-C connector (with correct 5.1 kΩ CC pull-downs — the classic first mistake)
- ESD protection + fuse
- 3.3 V LDO with proper input/output caps
- ATtiny85 or RP2040 (or a 555 if you want zero firmware)
- 4 LEDs + 2 buttons + a header breaking out all GPIO
- Power LED, test points on every rail, mounting holes, silkscreen with your name and version

Steps: draw a block diagram by hand → select every part on Digi-Key/LCSC with a real MPN and stock check → schematic in KiCad → assign footprints (verify each against the datasheet land pattern) → ERC clean → layout with a solid ground pour on the bottom → DRC clean → 3D view sanity check → generate gerbers → **upload to JLCPCB and order**.

While it ships (5–10 days), do Week 14 and come back to assemble.

### ⛳ Milestone 3 / GATE G2
Gerbers ordered. FPGA UART project working. Board v1 assembled and blinking when it arrives.

---

# PHASE 4 — EMBEDDED SYSTEMS CORE
### Weeks 14–21 · 240 hours · Goal: you can write bare-metal firmware from the reference manual alone

## Week 14 — Embedded C Discipline
**Theory:** Memory layout: `.text`, `.rodata`, `.data`, `.bss`, stack, heap — and where each lives in a microcontroller. Why you avoid `malloc` in embedded. Stack sizing and overflow detection (canaries, MPU). Pointers: pointer arithmetic, pointer-to-pointer, function pointers (jump tables, callbacks), `const` placement rules (`const char *` vs `char * const`). `volatile` — the exact three cases it's needed (memory-mapped registers, ISR-shared variables, setjmp). `static` at file vs function scope. `inline`, `restrict`. Bit manipulation idioms: set/clear/toggle/test, masks, bit fields vs shifts (and why bitfields are non-portable). Integer promotion rules and the sign bugs they cause. Endianness, packed structs, alignment, unaligned access faults. Fixed-point arithmetic: Q formats, saturating math, avoiding float on M0. `stdint.h` types — never use bare `int` for registers. Enums, unions, `offsetof`. Preprocessor discipline. Header guards, `extern`, translation units, linkage.

**Build:** Write, on your PC first: a ring buffer, a fixed-point PID skeleton, a byte-level protocol parser as an FSM, a bit-manipulation library with unit tests. Compile with `-Wall -Wextra -Werror -Wconversion` and fix every warning. Inspect `objdump -d` output for a simple function; read the assembly.

---

## Week 15 — MCU Architecture & the Bare-Metal Toolchain
**Theory:** ARM Cortex-M0+/M3/M4 core: register file (R0–R12, SP, LR, PC), xPSR, Thumb-2, privileged vs unprivileged, MSP vs PSP, exception model, vector table, reset sequence, `Reset_Handler`, `SystemInit`. Memory map: code, SRAM, peripheral, system regions, bit-banding. Harvard-ish bus matrix. Flash wait states and prefetch/ART accelerator. NVIC overview. SysTick. Toolchain internals: preprocessor → compiler → assembler → linker → objcopy. **Linker scripts**: MEMORY and SECTIONS, load vs virtual address, why `.data` must be copied from flash to RAM at startup, and `.bss` zeroed. Startup file anatomy. `-O0` vs `-Os` vs `-O2` effects. Map files: find what's eating your flash.

**Build — the week's core exercise:**
Write **blinky from absolute zero** on an STM32:
1. New empty folder. No CubeMX-generated code.
2. Write your own `startup.c` (vector table as an array of function pointers) and `linker.ld`.
3. Enable the GPIO clock by writing directly to the RCC register found in the reference manual.
4. Configure MODER, set/clear ODR (or BSRR).
5. `CMakeLists.txt` or Makefile → `.elf` → `.bin`.
6. Flash with `openocd` / `st-flash`.
7. Debug with `gdb`: breakpoints, `info registers`, examine memory, step through your startup code and watch `.data` get copied.

Do this **twice** — once for STM32, once for RP2040 or ESP32 — to prove the concept generalizes.

---

## Week 16 — Clocks, Timers, PWM, Low Power
**Theory:** Clock tree: HSI/HSE/LSI/LSE, PLL (M/N/P/Q dividers), AHB/APB prescalers, peripheral clock enables, clock security system, MCO output. Flash latency vs clock speed. SysTick for delays and RTOS tick. Timer types: basic, general-purpose, advanced (with complementary outputs + dead time). Prescaler + ARR + CCR math. PWM modes, center-aligned vs edge-aligned, resolution vs frequency trade-off. Input capture for frequency/pulse-width measurement. Output compare. One-pulse mode. Quadrature encoder interface mode. Timer chaining/master-slave. Watchdogs: independent (IWDG) vs window (WWDG), and correct kicking discipline. RTC, backup domain, alarms. Low power modes: sleep, stop, standby, shutdown; wake sources; measuring µA current properly.

**Build:** Configure the clock tree by hand to 84/100/168 MHz and verify with MCO on the scope. Generate a 20 kHz PWM and sweep duty from a variable. Measure an input signal's frequency and duty with input capture. Read a quadrature encoder in hardware timer mode. Put the MCU into stop mode, wake on a button, and measure the sleep current (this requires a µCurrent or a good DMM in µA range).

---

## Week 17 — Interrupts, NVIC & DMA
**Theory:** Exception vs interrupt. Vector table & handler naming. NVIC: enable, priority grouping (preemption vs sub-priority), pending, active, tail-chaining, late arrival. Interrupt latency and jitter. ISR design rules: short, no blocking, no printf, no malloc, set flags and defer. Atomicity: read-modify-write hazards, `__disable_irq`/critical sections, LDREX/STREX, `_Atomic`, why `volatile` is not enough for atomicity. Shared data patterns: lock-free single-producer/single-consumer ring buffer, double buffering. Race conditions and how to spot them. Fault handlers: HardFault, BusFault, UsageFault, MemManage — how to decode the stacked frame and find the faulting PC. DMA: channels/streams, request mapping, peripheral↔memory, memory↔memory, circular mode, half-transfer and transfer-complete interrupts, burst/FIFO, arbitration priority, cache coherency on M7.

**Build:** External interrupt (EXTI) button with hardware + software debouncing. Timer interrupt at exactly 1 kHz, verified with a scope pin toggle; measure ISR latency and execution time by toggling a GPIO at entry/exit. Implement a lock-free ring buffer between an ISR and main loop; then break it deliberately and observe the corruption. Deliberately cause a HardFault (null pointer dereference) and write a handler that prints the faulting address.

---

## Week 18 — Serial Communication Protocols
**Theory:**
- **UART:** framing, start/stop/parity, baud rate generation and % error tolerance (why 3% breaks it), oversampling 8× vs 16×, flow control (RTS/CTS), break condition, RS-232 vs TTL levels, idle-line detection for variable-length packet RX with DMA.
- **SPI:** master/slave, CPOL/CPHA (all four modes and how to determine the right one from a timing diagram), MSB/LSB first, chip select management, daisy chaining, max clock vs trace length, full-duplex DMA, why the slave's MISO is often open-drain-ish, 3-wire mode.
- **I²C:** open-drain bus, pull-up sizing (rise time vs bus capacitance, 1 kΩ–10 kΩ), addressing 7-bit vs 10-bit, ACK/NACK, repeated start, clock stretching, arbitration & multi-master, bus lock-up and the 9-clock recovery procedure, standard/fast/fast-plus/high-speed modes, SMBus differences, address conflicts.
- Protocol design over serial: framing (SLIP/COBS), length prefixes, CRC-8/16/32, escaping, timeouts, retries, versioning.

**Build:** UART echo → then UART command shell with a ring buffer and DMA RX. SPI: read a W25Q flash JEDEC ID, then read/write/erase a sector. I²C: bus scanner that finds all addresses, then read a BME280 and an MPU6050. **Put the logic analyzer on every one of these** and decode the traffic; compare it to the datasheet timing diagram line by line. Deliberately remove the I²C pull-ups and see what happens.

---

## Week 19 — On-Chip Analog & Sensor Integration
**Theory:** MCU ADC: resolution, sampling time vs source impedance (the RC settling calculation), sample-and-hold cap, input multiplexer, scan/sequence mode, injected channels, calibration (offset/gain), internal Vref and temperature sensor, VDDA decoupling and ferrite, oversampling for extra bits, DMA circular scan, ADC + timer trigger for deterministic sample rate. Noise reduction: averaging, median filter, layout, star ground for analog. On-chip DAC, comparators, op-amp blocks. Sensor interfaces: thermistor linearization (Steinhart-Hart), RTD, thermocouple + cold junction, load cell + HX711, hall sensors, photodiodes/TIA.

**Build:** Timer-triggered, DMA-driven, 4-channel ADC scan at exactly 10 kSPS with a circular buffer. Characterize your ADC's real noise (histogram of a shorted input, compute ENOB). Read a thermistor and output °C with correct math. Drive an SSD1306 OLED over I²C and display live sensor values. Read the IMU and compute pitch/roll with a complementary filter.

---

## Week 20 — Datasheets, Firmware Architecture & Debugging
**Theory:** How to attack a 1,500-page reference manual: find the block diagram, find the register map, find the "functional description," ignore the rest. Reading errata sheets (and believing them). Application notes as design shortcuts. Firmware architecture: super-loop vs cooperative scheduler vs RTOS; non-blocking state machines; hardware abstraction layers; module interfaces and dependency inversion; separating driver / service / application layers; software timers; event queues; error propagation strategy; assert and fail-fast; logging levels and a UART logger that doesn't block. Bootloader-friendly structure. Configuration and persistent settings in flash/EEPROM (with wear consideration and dual-copy CRC).

**Build:** Refactor everything from weeks 15–19 into a clean layered project: `hal/`, `drivers/`, `services/`, `app/`. Build a cooperative scheduler with software timers. Build a UART shell with commands (`help`, `read`, `set`, `dump`, `reboot`). Add an assert handler and a fault handler that dumps registers. Get the whole thing building in CI with GitHub Actions.

---

## Week 21 — Integration Sprint
No new theory. Build the milestone.

### ⛳ Milestone 4 / GATE G3 — Bare-Metal Data Logger
On an STM32 (Nucleo or your Board v1), with **no vendor HAL**:
- Timer-triggered ADC + DMA sampling at a configurable rate
- I²C IMU read at 100 Hz
- Timestamped records written to SPI flash or SD card with a simple filesystem or circular log
- UART shell for start/stop/dump/config, with DMA RX
- Stop-mode sleep between samples, with measured average current and a battery-life calculation
- Watchdog, fault handler, assert, versioned build info
- README with architecture diagram, current measurements, and logic-analyzer captures

---

# PHASE 5 — PCB ENGINEERING
### Weeks 22–26 · 150 hours · Goal: you can design a manufacturable multi-layer board and bring it up

## Week 22 — Schematic Engineering & Component Selection
**Theory:** Schematic as communication, not just netlist. Hierarchical sheets and block decomposition. Net classes and net naming discipline. Power tree diagrams: input → protection → regulation → rails, with current budget per rail (make an actual spreadsheet). Reference designator conventions. ERC rules and power flags. Design reuse blocks. DNP/assembly variants. Documentation on the schematic: revision block, notes, calculations, part rationale.

**Component selection criteria:** function → package → ratings (with derating: 50% voltage on ceramics, 80% on current, 20 °C thermal margin) → tolerance & tempco → lifecycle status (Active/NRND/EOL) → **real-time stock and price at 1/100/1000 qty** → second source available → LCSC basic vs extended parts (assembly cost impact) → footprint availability → AEC-Q qualification if relevant.

**Library management:** Create symbols and footprints yourself for 5 parts. IPC-7351 land pattern density levels (Most/Nominal/Least). Courtyard, assembly, fabrication layers. Pin-1 markers on silkscreen *and* fab layer. 3D model attachment (STEP). Linking MPN, manufacturer, and distributor part number as symbol fields so the BOM generates itself.

**Build:** Draw the schematic for **Board v2** (see Week 26): STM32G0/G4 or STM32F4 + USB-C + buck or LDO + IMU + CAN or RS-485 transceiver + SWD header + expansion connector + status LEDs. Build a power-tree spreadsheet. Create every custom footprint from the datasheet drawing.

---

## Week 23 — Stackup, Placement & Routing Fundamentals
**Theory:** Why 4 layers beat 2 for almost everything (SIG-GND-PWR-SIG vs SIG-GND-GND-SIG and when to choose each). 6- and 8-layer stackups. Dielectric materials (FR-4 Tg/Dk/Df), prepreg vs core, copper weight (0.5/1/2 oz), finished thickness. **Return current paths** — the single most important concept in PCB design: at DC it takes the lowest resistance, above ~10 kHz it takes the path directly under the trace; any split or gap in the reference plane forces a detour and creates a loop antenna. Trace width vs current (IPC-2152, internal vs external, temperature rise). Trace resistance, voltage drop, and fusing current. Vias: through, blind, buried, microvia; via current capacity; via inductance (~1 nH each); stitching vias for plane continuity and for shielding. Thermal relief vs direct connect. Placement strategy: connectors at edges, power in from one corner, sensitive analog far from switchers, crystals close to the MCU with a local ground island, decoupling caps on the *same side* and directly at the pin, mechanical/keepout constraints first. Copper pours: when to pour, when not to (floating copper islands, thermal antennas).

**Build:** Do the placement and routing of Board v2. Route power first, then critical nets (crystal, USB, ADC reference), then everything else. Keep an unbroken ground plane on layer 2. Run interactive length tuning where needed. Take a screenshot of every layer and annotate it with why you did what you did.

---

## Week 24 — Power Distribution Network & Thermal
**Theory:** PDN concept: the IC needs current in nanoseconds; the regulator responds in microseconds; capacitors bridge the gap. Target impedance Z_target = ΔV_allowed / ΔI_max. Impedance vs frequency of the whole network: VRM (low f) → bulk electrolytic/tantalum → ceramic 10 µF → 100 nF → plane capacitance (high f). Capacitor self-resonant frequency; why parallel different values can cause anti-resonance peaks; why 10× 100 nF beats 1× 1 µF sometimes and not others. Mounting inductance: pad-to-via distance dominates — via-in-pad or via-adjacent, short fat traces, two vias per cap. Ferrite beads: only for filtering noisy rails, never in a fast-transient path, watch DC resistance and saturation, watch the LC resonance with the bulk cap (add damping). Plane splits vs unified ground — Rick Hartley's argument. Analog/digital partitioning by *placement*, not by cutting planes.

**Switching regulator layout (memorize this):** identify the **hot loop** — the loop carrying discontinuous current (input cap → high-side FET → low-side FET → back to input cap for a buck). Minimize its physical area above all else. Input cap as close as physically possible to VIN/GND pins. Feedback trace routed away from the switch node, referenced to quiet ground, connected at the load. Switch node kept small in area (it's a dV/dt antenna) but wide enough for current. Ground plane directly beneath. Boot cap tight. Sense resistor Kelvin connected.

**Thermal:** power dissipation per component, θJA vs θJC vs ΨJT, copper area as heatsink, thermal vias under QFN/DFN pads (count, size, tenting), airflow, ambient assumptions, thermal simulation basics, IR camera verification.

**Build:** Redo your Board v2 power section layout to textbook standard. Take a "before/after" screenshot. Compute the PDN target impedance for your MCU and choose the decoupling network deliberately. Add thermal vias under the regulator.

---

## Week 25 — DFM, DFA, DFT & Manufacturing Output
**Theory:** Fab capability tables: minimum trace/space, min drill, annular ring, aspect ratio, solder mask dam and sliver rules, silkscreen minimum line width and height, edge clearance, copper-to-edge. Solder mask expansion, NSMD vs SMD pads. Paste layer and stencil design: aperture reduction, area ratio, thickness, window-pane for large thermal pads. Panelization: V-score vs tab-route vs mouse bites, rails, fiducials (global and local), tooling holes, spacing for the pick-and-place machine's clamp. Assembly: polarity/pin-1 markings, part orientation in the CPL file (0402 rotation errors are the #1 assembly defect), courtyard clearance, hand-solder access, double-sided reflow considerations. Test: test points on every rail and critical net, ICT vs flying probe, boundary scan/JTAG chain, programming header vs pogo-pin test pads, a self-test firmware mode.

**Output files:** Gerber X2 / ODB++, Excellon drill, netlist for testing, BOM (with MPN, quantity, designators, DNP marked), centroid/CPL (with correct origin, rotation, and layer), assembly drawing, fab drawing with stackup and notes, README for the fab house. IPC-A-610 acceptance classes 1/2/3 and what changes.

**Build:** Run a full DFM audit on Board v2 against JLCPCB's capability table. Generate every output file. Upload and inspect the online gerber viewer *carefully* — this catches ~30% of first-time mistakes. Cross-check the CPL rotations for every part against the JLCPCB parts library orientation.

---

## Week 26 — Fabricate, Assemble & Bring-Up
**Theory:** Bring-up procedure (write it *before* the board arrives):
1. Visual inspection under microscope; check for bridges, tombstones, missing parts, wrong orientation.
2. Resistance check: every rail to ground with power off. A short = stop.
3. Apply power through a **current-limited** supply at low limit; watch current draw against your predicted budget.
4. Measure every rail voltage and ripple.
5. Check reset, crystal oscillation, and clock output.
6. Connect debugger; confirm the target is recognized.
7. Flash blinky; confirm.
8. Bring up peripherals one at a time, lowest-level first.
9. Log every anomaly and every bodge wire. Photograph everything.
10. Write the v3 change list while it's fresh.

**Build:** Order Board v2 (4-layer, assembled or hand-assembled). While waiting, write the bring-up plan and the test firmware. Then bring it up.

### ⛳ Milestone 5 / GATE G4
Your own 4-layer board, brought up, running your Milestone-4 firmware. Deliverables: schematic PDF, layer plots, stackup, BOM, assembly drawing, power-tree spreadsheet, bring-up log with measurements, and a written design review of your own board listing 10 things to improve.

---

# PHASE 6 — ADVANCED EMBEDDED
### Weeks 27–34 · 240 hours · Goal: production-grade firmware — concurrent, updatable, tested, secure

## Week 27 — RTOS Fundamentals (FreeRTOS)
**Theory:** Why an RTOS: concurrency, determinism, responsiveness. Tasks, task states, TCB, per-task stacks, stack sizing and high-water marks. Scheduler: preemptive priority-based, tick rate, time slicing, idle task, tickless idle. Context switch mechanics (PendSV, PSP). Priorities and priority assignment strategy (rate-monotonic). Blocking vs busy-waiting. Synchronization: binary/counting semaphores, mutexes, recursive mutexes, **priority inversion** and priority inheritance, deadlock and the four conditions. Communication: queues, stream/message buffers, direct-to-task notifications (fastest), event groups. ISR-safe API variants (`...FromISR`) and `portYIELD_FROM_ISR`. Critical sections and `configMAX_SYSCALL_INTERRUPT_PRIORITY`. Memory schemes heap_1 through heap_5, static allocation. Timing analysis: WCET, CPU load measurement, runtime stats, SEGGER SystemView tracing.

**Build:** Port your Milestone-4 logger to FreeRTOS: sensor task, logging task, shell task, LED/status task, communicating by queues and notifications. Instrument CPU load and stack high-water marks. Deliberately create a priority inversion, observe it in SystemView, then fix it with a mutex.

---

## Week 28 — Zephyr, Portability & Embedded C++
**Theory (Zephyr):** Philosophy vs FreeRTOS. `west` workspace and module system. Kconfig layered configuration. **Devicetree**: nodes, bindings, `compatible`, `DT_NODELABEL`, overlays, how the build generates device pointers. Driver model and subsystems (GPIO, SPI, sensor, logging, settings, shell, networking). Boards and board porting. Threads, k_work queues, k_msgq, k_sem. Power management framework. Building the same app for 3 different boards to prove portability.

**Theory (C++ in embedded):** What's safe (classes, RAII, templates, `constexpr`, `enum class`, references, `std::array`, `<type_traits>`) and what's not (exceptions, RTTI, dynamic allocation, iostreams, unbounded templates). Zero-cost abstraction for register access. CRTP for static polymorphism instead of virtuals. Compile-time pin configuration. Design patterns for firmware: HAL interface + concrete driver, observer for events, state pattern for FSMs, dependency injection for testability.

**Build:** Re-implement your sensor node in Zephyr and build it for two different MCU families from one codebase. Write a small C++ register-abstraction layer and compare generated assembly to the C version at `-Os`.

---

## Week 29 — Bootloaders, OTA & Firmware Lifecycle
**Theory:** Boot flow: ROM bootloader → your bootloader → application. Flash partitioning (bootloader / slot 0 / slot 1 / scratch / settings). Vector table relocation (`SCB->VTOR`). Jumping to the application safely (deinit peripherals, set MSP). Image format: header, version, size, CRC32 or SHA-256, signature. Update transports: UART/XMODEM, USB DFU, SD card, BLE, Wi-Fi/HTTPS, LoRa. Update strategies: single-bank with a risky window, dual-bank A/B swap, swap-with-scratch, in-place with rollback. Confirming an image ("test mode" boot + application self-confirm, else revert). Anti-rollback counters. MCUboot: architecture, image trailers, key management, `imgtool`. Manufacturing programming: SWD gang programmers, factory test firmware, serial number & calibration data provisioning, protecting the debug port (RDP levels) — and what you lose when you do.

**Build:** Write your own minimal bootloader from scratch (UART + XMODEM or a custom protocol, CRC-verified, dual-slot). Then redo it with MCUboot + signed images. Implement OTA over BLE or Wi-Fi on an ESP32/nRF52 with rollback on failure. Deliberately power-cycle mid-update and prove the device still boots.

---

## Week 30 — Industrial Comms: CAN, RS-485, Isolation
**Theory (CAN):** Differential bus, dominant/recessive, 120 Ω termination at both ends only, node arbitration by ID (non-destructive, priority = lower ID). Frame formats: standard/extended, data/remote/error/overload, DLC, CRC, ACK slot. Bit timing: time quanta, sync/prop/phase segments, sample point (~75–87.5%), SJW, and calculating registers for a given bitrate. Error handling: TEC/REC, error-active/passive/bus-off, and recovery. Acceptance filters and masks. CAN-FD: BRS, larger payloads, dual bit rates. Transceivers, split termination, common-mode chokes, bus fault protection. Higher layers: DBC files, J1939, CANopen, UDS/OBD-II basics.

**Theory (RS-485 & isolation):** Differential half-duplex, DE/RE control and turnaround timing, biasing resistors, failsafe receivers, stub length, daisy-chain topology. Modbus RTU: frame format, function codes, CRC-16, inter-frame timing (3.5 char), master/slave discipline. Isolation: why (ground loops, safety, common-mode), optocouplers vs digital isolators (capacitive/magnetic), CMTI, isolated DC-DC, creepage & clearance, reinforced vs basic isolation, IEC 60664 basics.

**Build:** Two boards on a CAN bus exchanging sensor data with proper bit timing you calculated yourself. Add a USB-CAN adapter and sniff the bus with `candump`/SavvyCAN; write a small DBC. Implement a Modbus RTU slave over RS-485 and talk to it from a PC master tool. Scope the differential signals and measure the eye.

---

## Week 31 — USB, Ethernet & Wireless
**Theory (USB):** Topology, enumeration sequence, descriptors (device/config/interface/endpoint/string), endpoint types (control/bulk/interrupt/isochronous), transfer scheduling, USB 2.0 FS/HS signaling, D+/D− differential 90 Ω, USB-C CC pins and 5.1 kΩ, PD basics. Classes: CDC-ACM (virtual COM), HID, MSC, DFU, WinUSB/vendor class. TinyUSB.

**Theory (Ethernet/IP):** MAC vs PHY, MII/RMII, magnetics, differential pairs and 100 Ω, auto-negotiation. TCP/IP stack basics: ARP, IP, ICMP, UDP, TCP, DHCP, DNS. lwIP configuration and memory tuning. MQTT (topics, QoS, retain, LWT), HTTP/HTTPS, TLS on MCU (mbedTLS), cert handling and memory cost.

**Theory (wireless):** BLE — GAP roles, advertising, connection intervals & latency, GATT services/characteristics/descriptors, notifications vs indications, MTU, pairing/bonding, security modes, power profiling. Wi-Fi — station/AP/provisioning, power save modes, throughput vs current. LoRa/LoRaWAN — chirp spread spectrum, SF/BW/CR trade-offs, link budget, duty cycle limits, classes A/B/C, OTAA vs ABP. Thread/Matter — mesh, border router, commissioning. Choosing a radio: range vs data rate vs power vs cost. Antennas: chip vs PCB trace vs external, matching network, ground plane requirements, keep-out zones, certification (pre-certified modules vs your own RF).

**Build:** USB CDC device with TinyUSB on your board (virtual COM shell). A BLE peripheral (nRF52 or ESP32) exposing a custom GATT service with your sensor data, read from a phone (nRF Connect). An MQTT sensor publisher over Wi-Fi with TLS. Measure the current profile of a BLE advertisement burst.

---

## Week 32 — Embedded Linux
**Theory:** When Linux instead of an MCU (need: filesystem, networking stack, display, multiple apps, > ~100 MB RAM). Boot chain: ROM → SPL/MLO → U-Boot → kernel + DTB → initramfs → rootfs → init (systemd). U-Boot environment and commands. Kernel vs userspace, syscalls, /proc and /sys. **Devicetree** in depth: describing hardware to the kernel, overlays, pinmux, clocks, regulators. Kernel modules: build, load, `printk`, character device drivers, file operations, ioctl, sysfs attributes, interrupt handling, `devm_` APIs. Userspace hardware access: libgpiod, spidev, i2c-dev, iio, PWM sysfs, serial termios. Cross-compilation and toolchains, sysroots. **Buildroot** (fast, simple) then **Yocto** (layers, recipes, BitBake, bbappend, SDK generation). Root filesystem layout, read-only rootfs + overlayfs, systemd services and targets, journald. Real-time: PREEMPT_RT, latency measurement (cyclictest), CPU isolation, priority setup.

**Build:** Boot a Raspberry Pi / BeagleBone with a Buildroot-built minimal image you configured. Write a devicetree overlay for a SPI sensor. Write a simple character-device kernel module and load it. Write a userspace daemon (C or Python) that reads your MCU board over UART/CAN and publishes to MQTT, running as a systemd service, auto-starting on boot. Then reproduce the image in Yocto.

---

## Week 33 — Testing, CI & Security
**Theory (quality):** Test pyramid for firmware. Unit testing on host with Unity + CMock or GoogleTest; designing for testability (dependency injection, hardware behind interfaces). Mocking registers with a fake memory map. Integration tests on target. **HIL (hardware-in-the-loop)**: a test rig with a controller board stimulating your DUT, automated from Python (pytest + pyserial/pyvisa), scope/DMM automation over SCPI. Code coverage (gcov/lcov). Static analysis: `cppcheck`, `clang-tidy`, compiler warnings as errors, `-fanalyzer`. Sanitizers on host builds (ASan/UBSan). MISRA C:2012 — categories, common rules, deviations, tooling. Code review practice. CI for firmware: build matrix, artifact publishing, size tracking, running host tests and (with a self-hosted runner) target tests.

**Theory (security):** Threat modeling (STRIDE) for a connected device. Attack surfaces: debug port, firmware extraction, bus sniffing, glitching, network. Secure boot chain of trust, ROM keys, immutable bootloader. Crypto primitives on MCU: AES-GCM, SHA-256, HMAC, ECDSA/Ed25519, ECDH; hardware accelerators and TRNG quality. Key storage: OTP/fuses, secure elements (ATECC608, SE050), TPM, PUF. Debug lock (RDP/JTAG disable) and its trade-offs. Secure provisioning in manufacturing. Side channels: timing, power analysis, fault injection — awareness level. Regulatory: EU CRA, ETSI EN 303 645, IEC 62443 overview.

**Build:** Add a full unit test suite for your driver and protocol layers, running on host in GitHub Actions with coverage reporting. Build a simple HIL rig: a second MCU that injects UART/CAN traffic and toggles inputs, driven by a pytest suite. Implement signed firmware verification in your bootloader with Ed25519. Run cppcheck and fix everything it finds.

---

## Week 34 — Embedded DSP & Control Implementation
**Theory:** Fixed-point vs floating-point on M0/M4F, CMSIS-DSP library, SIMD instructions. Digital filters: moving average, exponential (IIR one-pole), FIR design (windowed sinc, Parks-McClellan) vs IIR (Butterworth via bilinear transform), filter order vs latency vs CPU, coefficient quantization, biquad cascades (Direct Form I vs II transposed). FFT: windowing (Hann/Hamming/flat-top), bin resolution, leakage, real-FFT, magnitude/phase, using it for vibration or audio analysis. Sensor fusion: complementary filter, Kalman filter derivation (predict/update, Q and R tuning), extended Kalman filter, Madgwick/Mahony AHRS. **PID in firmware**: discrete forms, sample-rate selection (≥10× bandwidth), integral windup and clamping/back-calculation, derivative on measurement (not error) plus low-pass filtering, bumpless transfer, feedforward, output saturation, deadband, fixed-point implementation.

**Build:** Implement a biquad LPF in fixed-point and verify against a Python/scipy reference. Run a 256-point FFT on accelerometer data and detect a vibration frequency. Implement a complementary filter and an EKF for IMU attitude; compare drift over 10 minutes. Implement a fully-featured PID class with anti-windup and derivative filtering, unit-tested on host.

### ⛳ Milestone 6 / GATE G5 — Connected Multi-Node System
Two or three of your own boards + a Linux gateway:
- FreeRTOS or Zephyr on the nodes, sensors sampled and filtered on-device
- CAN or BLE between nodes; gateway aggregates and publishes to MQTT over TLS
- Signed OTA firmware update, tested with mid-update power loss
- Unit tests + static analysis in CI; HIL smoke test
- Documented power budget and measured battery life

---

# PHASE 7 — HIGH-SPEED PCB, SIGNAL/POWER INTEGRITY & EMC
### Weeks 35–39 · 150 hours · Goal: you can design boards that pass compliance the first time

## Week 35 — Transmission Line Theory
**Theory:** When is a trace a transmission line? The rule: if the propagation delay of the trace exceeds ~1/6 of the signal's **rise time**, treat it as one. (Note: rise time, not clock frequency — a 1 MHz clock with a 500 ps edge is a high-speed signal.) Signal bandwidth ≈ 0.35/tr. Characteristic impedance Z₀ from geometry: microstrip, stripline, coplanar waveguide with ground, embedded microstrip. Dk and Df of FR-4 vs Rogers, and Dk's frequency dependence. Propagation velocity and delay (~150 ps/inch microstrip, ~180 ps/inch stripline). Reflections: reflection coefficient Γ = (ZL−Z₀)/(ZL+Z₀), ringing, overshoot/undershoot, TDR concept. Termination strategies: series (source) termination, parallel, Thévenin, AC/RC, diode clamps — and when each is used. Stub effects. Impedance control: telling the fab what you need, the fab adjusting trace width, impedance test coupons, ±10% tolerance.

**Build:** Use Saturn PCB Toolkit and KiCad's built-in calculator to design 50 Ω single-ended and 90/100 Ω differential geometries for a 4-layer 1.6 mm stackup. Simulate a driver into an unterminated line in LTspice using a lossy T-line model; watch the ringing; add series termination; watch it disappear. If you have a fast-edge scope, build a simple trace and observe real reflections.

---

## Week 36 — Signal Integrity
**Theory:** Crosstalk mechanisms: mutual capacitance and mutual inductance; near-end (NEXT) and far-end (FEXT); the 3W guideline and why it's a crude approximation; coupling vs trace separation and vs height above plane (halving the dielectric height halves the crosstalk — plane proximity matters more than spacing). Guard traces: usually useless unless stitched with vias every λ/20. Differential signaling: common-mode rejection, why the pair should be loosely coupled over a solid plane rather than tightly coupled with no plane, intra-pair skew (length matching, target <5 mil for USB/Ethernet, tighter for DDR/SerDes), inter-pair skew, symmetric routing, avoiding splitting a pair around obstacles. Serpentine tuning rules. Via effects: via stub resonance, back-drilling, via transitions needing adjacent return vias (**always place a ground via near a signal via that changes reference plane** — this is one of the highest-value habits you can build). Layer transitions between planes of different net. Eye diagrams, jitter (random vs deterministic, ISI, DCD), bit error rate, S-parameters (S11 return loss, S21 insertion loss), IBIS models, channel simulation.

**Build:** Route a USB 2.0 HS differential pair to spec on a real board: 90 Ω, length matched, no plane crossings, ground vias at layer transitions, ESD protection with low capacitance placed near the connector. Use KiCad's differential pair router and length tuner. Do a self-review against a written SI checklist you create.

---

## Week 37 — Power Integrity
**Theory:** PDN as a frequency-domain problem. Target impedance derivation from allowed rail ripple and transient current. Impedance profile contributions: VRM output impedance and control-loop bandwidth (~10–100 kHz), bulk caps (100 kHz–1 MHz), ceramics (1–100 MHz), package + on-die capacitance (>100 MHz). Capacitor model (C + ESR + ESL), self-resonant frequency, mounting inductance dominating above ~50 MHz. Anti-resonance between different-valued caps and how to damp it (use fewer distinct values, or add ESR deliberately). Plane capacitance and how thin dielectric between power and ground planes helps at high frequency. Plane resonances and cavity modes. Simultaneous switching noise (SSN) / ground bounce. Decoupling placement rules by frequency. Measuring PDN impedance in the lab (2-port shunt-through with a VNA). Rail ripple measurement technique: 1× probe on a short ground spring, 20 MHz bandwidth limit off, AC coupling.

**Build:** Model your board's PDN in a spreadsheet or with a free tool; plot Z vs f; compare to target. Measure your board's 3.3 V rail ripple correctly (ground spring vs 6-inch ground lead — photograph the difference). Add/remove decoupling caps and measure the change.

---

## Week 38 — EMC / EMI
**Theory:** The two currencies: **emissions** (you polluting) and **immunity** (you being polluted). Radiated vs conducted, differential-mode vs common-mode emissions (CM usually dominates radiated emissions and comes from cables). Radiation from current loops: E ∝ f²·A·I — minimize loop area, everywhere, always. Cables as antennas driven by common-mode voltage between the board ground and chassis. Clock harmonics and spread-spectrum clocking. Slew rate control (slower edges = less EMI; use gate resistors, ferrites, series R on clocks). Filtering: pi filters, common-mode chokes on cables and on differential pairs, feedthrough capacitors, shielded connectors, shield termination (360° at the connector, not a pigtail). Shielding: enclosure apertures, seams, the λ/20 rule, board-level cans. Grounding for EMC: chassis ground, stitching capacitors, single-point vs multi-point.
**Immunity:** ESD (IEC 61000-4-2, contact and air discharge, ±8 kV typical) — TVS placement at the connector *before* anything else, low-capacitance parts on data lines, ground path to chassis. EFT/burst (61000-4-4), surge (61000-4-5), conducted immunity (61000-4-6), radiated immunity (61000-4-3), power quality (dips/interruptions). Standards landscape: CISPR 32 / EN 55032 (emissions, Class A vs B), CISPR 35 immunity, FCC Part 15 B, automotive CISPR 25, medical IEC 60601-1-2, industrial IEC 61000-6-2/-6-4. Certification path, notified bodies, test house cost, and why **pre-compliance testing saves you $20k**.

**Build:** Build a pre-compliance setup: near-field E and H probes + TinySA Ultra (or a real spectrum analyzer if you can get lab access). Scan your own boards; find your loudest emitters (usually the switching regulator hot loop, the crystal, and any cable). Make a change (add a ferrite, shrink a loop, add a CM choke) and measure the dB improvement. Build an ESD gun substitute (piezo lighter) and zap your board's connectors with and without TVS protection. **Document with before/after spectrum plots.**

---

## Week 39 — Applied High-Speed & Special PCBs
**Theory & applied layout rules for:**
- **USB 2.0 HS / USB 3.x**: 90 Ω diff, matching, ESD, USB-C orientation, SS pair routing away from the connector
- **Ethernet 10/100/1000**: magnetics placement, chassis ground island under the RJ45, Bob Smith termination, 100 Ω pairs, isolation gap rules
- **DDR3/DDR4**: fly-by topology, address/command vs data groups, write leveling, VREF, ZQ, termination (ODT), tight length matching per byte lane, why DDR is where you graduate to a real field solver
- **MIPI CSI-2/DSI**: low-swing differential, tight matching, short runs, ground reference continuity
- **RF**: 50 Ω coplanar waveguide with ground, matching networks (pi/L), antenna keep-out zones, ground plane size as part of the antenna, module vs discrete RF, using a NanoVNA to check return loss
- **Flex & rigid-flex**: bend radius, no plated holes in bend areas, hatched ground planes, stiffeners, coverlay, teardrops
- **HDI**: microvias, via-in-pad (filled and capped), stacked vs staggered, sequential lamination, when BGA pitch forces it (≤0.5 mm)

**Build:** Design **Board v3**, a genuinely high-speed board — e.g. an MCU board with USB HS + Ethernet, or an RP2040/STM32H7 with a camera (MIPI or parallel) — as a 4- or 6-layer controlled-impedance stackup. Write an SI/PI/EMC design justification document alongside it.

### ⛳ Milestone 7 / GATE G6
Board v3 fabricated with controlled impedance, plus a design-justification document covering: stackup and impedance targets, return path strategy, PDN target impedance and decoupling plan, differential pair rules applied, EMC mitigation decisions, and pre-compliance near-field scan results before and after mitigations.

---

# PHASE 8 — ROBOTICS
### Weeks 40–48 · 270 hours · Goal: an autonomous robot on hardware you designed

## Week 40 — Mathematical Foundations
**Theory:** Vectors, matrices, matrix multiplication as composition, determinant, inverse, pseudo-inverse, rank, null space, eigenvalues/eigenvectors, SVD (and its use for least squares and calibration). Coordinate frames and the notation discipline (`^A T_B`). Rotation matrices: properties (orthonormal, det = 1), composition order, fixed vs moving axes. Euler angles (roll-pitch-yaw), gimbal lock. Axis-angle. **Quaternions**: definition, Hamilton product, rotation by conjugation, normalization, SLERP, quaternion↔rotation matrix↔Euler conversions, why they beat Euler for integration. Homogeneous transformation matrices, chaining, inverting. Twists, screw theory intro. Probability refresher: Gaussian, covariance, Bayes' rule, marginalization/conditioning.

**Build:** In Python (numpy + matplotlib), write from scratch: rotation matrix and quaternion classes with full conversions, a transform-tree resolver, and a 3D visualizer showing a frame rotating under each representation. Demonstrate gimbal lock numerically.

---

## Week 41 — Kinematics
**Theory:** Configuration space, degrees of freedom, joint types (revolute, prismatic), Grübler's formula. **Forward kinematics** by transform chaining; Denavit-Hartenberg parameters (classic and modified) and the Product-of-Exponentials alternative. Workspace (reachable vs dexterous), singularities and what happens near them. **Inverse kinematics**: analytical/closed-form (2-link planar, 6-DOF with spherical wrist — Pieper's condition), numerical (Jacobian transpose, pseudo-inverse, damped least squares/Levenberg-Marquardt, CCD), multiple solutions and branch selection, joint limits. **Jacobian**: geometric and analytic, velocity mapping, force/torque duality (τ = Jᵀ F), manipulability ellipsoid, singularity detection via condition number. **Mobile robot kinematics**: differential drive (unicycle model), wheel odometry and its error accumulation, Ackermann steering, omniwheel/mecanum kinematics matrices, nonholonomic constraints.

**Build:** Code and visualize FK/IK for a 2-DOF and a 3-DOF planar arm (analytical), then a 6-DOF arm numerically with damped least squares. Simulate differential-drive odometry with wheel-slip noise and plot drift over a 20 m loop.

---

## Week 42 — Actuators & Motor Control
**Theory:** **Brushed DC**: equivalent circuit, back-EMF constant Ke, torque constant Kt, speed-torque curve, stall current, H-bridge topology, shoot-through and dead time, sign-magnitude vs locked-antiphase PWM, PWM frequency vs audible noise vs switching loss, current decay modes (fast/slow/mixed), braking vs coasting, regenerative energy and where it goes.
**Steppers**: full/half/microstepping, current chopping, decay modes, torque vs speed (and why they lose steps), open-loop vs closed-loop steppers, drivers (A4988/DRV8825/TMC2209 with StealthChop).
**BLDC/PMSM**: construction, pole pairs, electrical vs mechanical angle, trapezoidal (six-step) commutation with hall sensors, sensorless back-EMF zero-crossing, **FOC**: Clarke transform (abc→αβ), Park transform (αβ→dq), d-axis and q-axis current control, inverse transforms, SVPWM, field weakening. Rotor position sensing: hall, incremental encoder + index, absolute encoder (SPI/SSI/BiSS), resolver, magnetic (AS5047). Current sensing: shunt placement (inline, low-side, three-shunt), amplifiers (INA240), ADC synchronization to PWM. Gate drivers, bootstrap, desat protection.
**Mechanics**: motor sizing (torque, speed, inertia matching, duty cycle, thermal), gearboxes (spur, planetary, harmonic, cycloidal), backlash, efficiency, belts, lead screws, bearings, series-elastic actuators. Servos (hobby PWM), linear actuators, pneumatics overview.
**Power**: LiPo/Li-ion chemistry, C-rating, BMS, balance charging, safety, current spikes, bulk capacitance near drivers, e-stop design.

**Build:** Closed-loop velocity control of a brushed DC motor with a quadrature encoder (hardware timer mode) and a PID at 1 kHz — plot step response and tune it. Then run a gimbal BLDC under FOC using SimpleFOC (or ODrive), and scope the phase currents. **Design a motor driver PCB** (dual H-bridge or a 3-phase inverter stage) applying everything from Phase 5 and 7 — this is a serious board with high di/dt.

---

## Week 43 — Control Theory
**Theory:** System modeling: first-principles ODEs for a DC motor, mass-spring-damper, inverted pendulum. Laplace transform, transfer functions, poles & zeros, stability, damping ratio ζ and natural frequency ωn, step response metrics (rise time, overshoot, settling time, steady-state error), system type and error constants. Block diagram algebra. Root locus intuition. Frequency response, gain margin and phase margin, Nyquist criterion, bandwidth vs response speed vs noise sensitivity. **PID in depth:** each term's effect, tuning methods (Ziegler-Nichols, relay auto-tuning, manual loop-shaping), cascade control (current loop 10 kHz → velocity loop 1 kHz → position loop 100 Hz, each ~5–10× faster than the outer), feedforward (velocity/acceleration/gravity), integral windup handling, derivative kick and setpoint weighting. Discretization: Tustin/bilinear, ZOH, aliasing of the derivative, choosing sample rate, computational delay as extra phase lag. **Modern control:** state-space (A, B, C, D), controllability/observability, pole placement, **LQR** (Q/R weighting intuition), observers/Luenberger, LQG, integral action augmentation. Intro to MPC: horizon, constraints, cost, when it's worth the CPU. Trajectory generation: trapezoidal and S-curve profiles, jerk limits, splines, time-optimal paths.

**Build:** Simulate a DC motor in Python (`python-control`/scipy); design PID by loop shaping; verify on hardware and compare sim vs reality. Build a physical inverted pendulum (cart or reaction wheel) and stabilize it with LQR — this is the single best control-theory project there is. Implement trapezoidal motion profiling on a real axis.

---

## Week 44 — Sensors & State Estimation
**Theory:** **IMU**: MEMS accelerometer & gyroscope physics, bias, bias instability, random walk, scale factor and cross-axis errors, temperature drift, Allan variance for characterizing noise, calibration (6-position accel, gyro static bias, ellipsoid fit). Magnetometer: hard-iron and soft-iron calibration, local disturbances, why indoor heading is unreliable. Barometer for altitude. **Encoders**: incremental quadrature (x4 decoding), index pulse homing, absolute encoders, resolution vs accuracy, noise/EMI on encoder lines (differential RS-422 encoders). **Range sensors**: ultrasonic (beam width, crosstalk), IR ToF (VL53L1X), 2D LiDAR (scan rate, angular resolution, range accuracy, motion distortion), 3D LiDAR, radar. **Cameras**: pinhole model, intrinsics (fx, fy, cx, cy), distortion coefficients, extrinsics, calibration with a checkerboard, rolling vs global shutter, stereo baseline & disparity, RGB-D (structured light vs ToF). Force/torque sensors, current-based torque estimation, tactile sensing.
**Estimation:** sensor timestamping and synchronization (the most underrated robotics problem), interpolation, outlier rejection. Complementary filter. **Kalman filter**: state, process model, prediction, measurement update, Kalman gain, tuning Q and R, divergence. EKF (linearization, Jacobians), UKF (sigma points), particle filter. Applications: attitude estimation, wheel-odom + IMU fusion, GPS/INS.

**Build:** Characterize your IMU: log 2 hours of static data, compute Allan variance, extract bias instability and random walk. Write full calibration routines. Implement complementary, EKF, and Madgwick filters and compare against ground truth (a phone or a rotating rig). Calibrate a camera with OpenCV and undistort a live feed. Fuse wheel odometry + IMU yaw in an EKF and measure loop-closure drift improvement.

---

## Week 45 — ROS 2
**Theory:** Architecture: DDS middleware, discovery, nodes, executors and callback groups, QoS profiles (reliability, durability, history, deadline) and how a wrong QoS silently breaks everything. Topics, services, actions, parameters (and parameter callbacks). `rclcpp` vs `rclpy`. Workspaces, packages, `colcon` build, `ament_cmake`/`ament_python`, dependencies via `rosdep`. Launch files (Python launch), namespaces, remapping, composable nodes. **TF2**: transform tree, static vs dynamic transforms, buffers and listeners, time travel/extrapolation errors, `base_link`/`odom`/`map` frame conventions (REP-105). **URDF/xacro**: links, joints, visual/collision/inertial, meshes, `robot_state_publisher`, `joint_state_publisher`. Simulation: Gazebo/Ignition, plugins, sensor simulation, `ros2_control` (hardware interfaces, controllers, controller manager). Tooling: `rviz2`, `rqt`, `ros2 bag`, `ros2 topic hz/echo`, tracing. **micro-ROS** on the MCU: agent, transports (serial/UDP/CAN), memory constraints — this is how your Phase 4–6 firmware joins the robot.

**Build:** Build a ROS 2 workspace with your own packages. Write a URDF for your robot and visualize it in RViz with a moving joint. Bring up Gazebo with a differential-drive plugin and drive it with teleop. Run micro-ROS on your STM32 board publishing IMU + encoder data as real ROS 2 topics. Record and replay a bag.

---

## Week 46 — Perception
**Theory:** Image formation, color spaces, histogram operations. Filtering: Gaussian, median, bilateral, morphological ops. Edges (Canny), contours, Hough lines/circles. Thresholding and segmentation. Features: Harris, FAST, ORB, SIFT/SURF concepts; descriptors and matching; RANSAC for robust fitting; homography and perspective transform. Fiducials: ArUco/AprilTag detection and pose estimation (PnP), and why they're the practical shortcut in real robots. Optical flow (Lucas-Kanade), background subtraction, object tracking (KCF, CSRT, SORT/DeepSORT). Stereo depth: rectification, block matching, disparity→depth. Point clouds with PCL: voxel downsampling, passthrough, plane segmentation (RANSAC), Euclidean clustering, normal estimation, ICP registration. **Edge ML**: CNN basics, object detection (YOLO family), semantic segmentation, transfer learning, quantization (int8), pruning, TFLite Micro / CMSIS-NN on MCU, ONNX Runtime / TensorRT on SBC, accelerators (Coral TPU, Jetson, Hailo), latency vs accuracy trade-offs, dataset collection and labeling.

**Build:** OpenCV pipeline: detect and track a colored object, publish its position as a ROS 2 topic. ArUco marker pose estimation for robot localization. Segment the ground plane from a LiDAR/depth point cloud and cluster obstacles. Train a small object detector by transfer learning and run it quantized on a Pi/Jetson; measure FPS and latency. Run a keyword-spotting or motion-classification TFLite Micro model on your STM32.

---

## Week 47 — Navigation & SLAM
**Theory:** The localization problem. Odometry sources and their error models. Probabilistic localization: Bayes filter → **Monte Carlo Localization / AMCL** (particle filter with a known map), motion model, sensor model (beam vs likelihood field), resampling, kidnapped robot problem. **SLAM**: the chicken-and-egg problem; filter-based (EKF-SLAM, FastSLAM/gmapping) vs graph-based (pose graph, front end/back end, loop closure, g2o/GTSAM/Ceres); scan matching (ICP, correlative), Cartographer, occupancy grid mapping, log-odds updates. Visual SLAM: ORB-SLAM3, VINS-Fusion, visual-inertial odometry. Map representations: occupancy grid, costmap layers (static, obstacle, inflation), octree/OctoMap, ESDF. **Planning**: global — Dijkstra, A* (heuristics, admissibility), D* Lite, Theta*, sampling-based RRT / RRT* / PRM, Hybrid A* for car-like robots; local — DWA, TEB, MPPI, pure pursuit, obstacle avoidance, velocity obstacles. Recovery behaviors. **Nav2**: behavior trees, planner/controller/smoother servers, costmap configuration, lifecycle nodes, tuning parameters that actually matter.

**Build:** Run gmapping/slam_toolbox on a simulated then a real robot with a real LiDAR; produce a map of your room. Localize with AMCL and measure position error against tape-measure ground truth. Configure Nav2 end-to-end: send a goal in RViz and have the robot get there while avoiding a box you place in its path. Implement A* yourself on a grid so you actually understand what Nav2 is doing.

---

## Week 48 — Manipulation, Real-Time & Industrial Robotics
**Theory:** Manipulator control: joint space vs task space, computed torque control, impedance and admittance control, force control, compliance. **MoveIt 2**: planning scene, collision checking (FCL), OMPL planners, IK solvers (KDL, TRAC-IK, IKFast), Cartesian paths, pick-and-place pipeline, grasp generation. Grasping: force closure, antipodal grasps, suction vs fingers, learned grasping (GraspNet/Dex-Net awareness). **Real-time systems for robots:** why jitter matters, PREEMPT_RT, cyclictest, thread priorities, CPU isolation, lock-free comms, EtherCAT (distributed clocks, cycle times, SOEM/IgH master), CANopen (CiA 402 drive profile), PROFINET/EtherNet-IP overview. **Industrial & safety:** robot classes, ISO 10218-1/-2 (industrial robot safety), ISO/TS 15066 (collaborative — power & force limiting, speed & separation monitoring), ISO 13849 performance levels (PL a–e) and IEC 62061 SILs, risk assessment, safety relays, safe torque off (STO), light curtains, e-stop categories 0/1/2, dual-channel redundancy, functional safety in firmware (self-tests, watchdogs, diverse redundancy). Fleet/warehouse robotics: AGV vs AMR, traffic management, docking/charging, VDA 5050.

**Build:** Simulate a 6-DOF arm in MoveIt and execute a pick-and-place in Gazebo. Measure control-loop jitter on your Linux SBC with and without PREEMPT_RT (cyclictest histograms). Implement a hardware e-stop with safe torque off on your motor driver board and verify it in every failure mode you can think of.

### ⛳ Milestone 8 / GATE G7 — Autonomous Robot on Your Own Hardware
A differential-drive robot where:
- The motor driver board and the main controller board are **your PCB designs**
- FOC or closed-loop PID motor control runs on your STM32 firmware, with encoder feedback and current limiting
- micro-ROS bridges the MCU to a Linux SBC running ROS 2
- IMU + wheel odometry fused in an EKF; LiDAR SLAM builds a map
- Nav2 autonomously navigates to a commanded goal while avoiding dynamic obstacles
- A camera-based task (find and approach an ArUco tag or a colored object)
- Hardware e-stop, battery monitoring with low-voltage cutoff, and a documented safety analysis

---

# PHASE 9 — INDUSTRY PRACTICE & CAPSTONE
### Weeks 49–52 · 120 hours · Goal: think like a senior engineer, not a hobbyist

## Week 49 — Systems Engineering & New Product Introduction
**Theory:** Requirements engineering: stakeholder needs → system requirements → subsystem requirements; writing testable requirements ("shall" statements with measurable acceptance criteria); traceability matrices. Architecture: block diagrams, interface control documents (ICDs), partitioning decisions (what goes in FPGA vs MCU vs SBC vs cloud), make vs buy, module vs custom RF. Trade studies with weighted criteria matrices. Design reviews: concept review, PDR, CDR, and how to run and survive one; review checklists; how to give and take criticism on your design. Risk register, mitigation plans, technical debt. **NPI phases:** Proto → **EVT** (does the design work?) → **DVT** (does it meet all specs across corners and environments?) → **PVT** (can the factory build it repeatably at yield?) → **MP**. Gate criteria for each. Build quantities, timeline realities, why hardware schedules slip. Prototype iteration budgeting.

**Build:** Write a complete requirements document and architecture spec for your robot, retroactively. Run a formal self-design-review with a written checklist. Build a trade study comparing three MCU options for it.

---

## Week 50 — Reliability, Compliance & Test
**Theory:** Derating guidelines (MIL-HDBK-338 / vendor tables): voltage, current, power, temperature. Component temperature limits and lifetime: electrolytic cap lifetime doubling per 10 °C, MLCC cracking and flex, tantalum failure modes, connector mating cycles. Reliability math: failure rate λ, FIT, MTBF vs useful life vs bathtub curve, series system reliability, redundancy. **FMEA**: process (PFMEA) and design (DFMEA), severity/occurrence/detection, RPN, action items; FMEDA for functional safety. Accelerated testing: HALT (find margins), HASS (screen production), temperature cycling, humidity (85/85), vibration/shock, drop, IP ingress ratings, salt fog. Burn-in. Field failure analysis: 8D process, root cause, cross-section and X-ray, decapping. **Compliance landscape:** safety (IEC/UL 62368-1 for IT/AV, IEC 60601 medical, UL 61010 lab equipment), EMC (as in Week 38), radio (FCC Part 15C, RED EN 300 328/301 489), environmental (RoHS, REACH, WEEE, conflict minerals, Prop 65), battery shipping (UN 38.3, IEC 62133), functional safety (IEC 61508, ISO 26262 ASILs, IEC 62304 medical software). CE marking / UKCA / FCC process, technical file contents, declarations of conformity, test-house engagement and cost.

**Build:** Write a DFMEA for your robot's power system. Do a derating audit of every component on Board v3 and fix violations. Draft a compliance plan: which standards apply, what testing, estimated cost and timeline.

---

## Week 51 — Cost, Supply Chain & Engineering Process
**Theory:** BOM cost engineering: cost drivers by category, price breaks at 1/100/1k/10k, cost of layers and board area, cost of assembly (part count, unique parts, double-sided, hand-soldered items, LCSC basic vs extended). Should-cost analysis. Design-to-cost: eliminating parts, consolidating values, choosing packages, integrating functions. NRE vs unit cost (stencil, tooling, test fixtures, certification amortized over volume). **Supply chain:** lead times and how they explode, allocation, MOQ/MPQ, franchised vs broker vs gray market (and counterfeit risk), authorized distributors, contract manufacturers, turnkey vs consigned. **Lifecycle management:** part status (Active/NRND/Obsolete), PCN/EOL notices, last-time buy, second sourcing and AVL, cross-references and drop-in alternates, designing for substitution. **Process:** hardware version control (git for KiCad — text formats, diffs, `.gitignore`, releases and tags, binary asset handling), PLM systems, ECO/ECN change control, revision schemes, part numbering, documentation packages, manufacturing work instructions, functional test fixture design (bed-of-nails, pogo pins, test firmware, pass/fail limits, traceability database, serialization).

**Build:** Build a full costed BOM for your robot at 1, 100, and 1,000 units. Do a cost-reduction exercise: cut 25% from the BOM cost and document what you traded away. Set up a proper release process in git with tagged hardware and firmware versions and a release checklist. Design a functional test fixture concept for Board v3.

---

## Week 52 — Capstone Consolidation & Career
**Do:**
1. **Portfolio.** One public GitHub org/repo per major project, each with: a README that opens with a photo/GIF of the working thing, a problem statement, an architecture diagram, key design decisions and trade-offs, measured results, and what you'd do differently. This is what gets you hired — not certificates.
2. **Write up 3 deep technical posts.** e.g. "Why my first switching regulator failed EMC and what fixed it," "Bare-metal STM32 from an empty folder," "Tuning a cascade FOC loop with a $12 encoder." Publishing separates you from 95% of self-taught engineers.
3. **Documentation package** for your capstone: requirements, architecture, schematics, layer plots, stackup, BOM, assembly drawing, firmware architecture, test reports, safety analysis, user manual.
4. **Interview prep** by track — build a question bank and answer each out loud:
   - *Analog:* op-amp stability, why decoupling, ADC aliasing, MOSFET switching losses, thermal calculation
   - *Digital:* setup/hold, metastability, CDC, FSM design, timing closure
   - *Embedded:* volatile vs atomic, ISR rules, priority inversion, ring buffer without locks, linker script, debugging a HardFault, why not malloc, stack overflow detection
   - *PCB:* return current path, decoupling placement, when a trace is a transmission line, buck hot loop, why not to split the ground plane
   - *Robotics:* quaternions vs Euler, EKF predict/update, PID anti-windup, why cascade loops, SLAM loop closure
5. **Choose your specialization** for year two — you cannot be a top expert in all four. Pick the one whose problems you enjoyed most.
6. Contribute to one open-source project (KiCad libraries, Zephyr driver, ROS 2 package, FreeRTOS port, an OSHW board).

### ⛳ GATE G8
A complete, manufacturable, documented product package that a contract manufacturer could build from without emailing you a single question.

---

# Appendix A — Project Ladder (the thing that actually gets you hired)

| # | Week | Project | Skills proven |
|---|---|---|---|
| 1 | 4 | Enclosed RC/RLC filter, measured vs simulated | Fundamentals, lab technique, soldering |
| 2 | 8 | Bench power supply, 0–12 V, current limited | Analog design, power, thermal, documentation |
| 3 | 12 | FPGA UART + FSM in Verilog | Digital, HDL, timing |
| 4 | 13 | **Board v1** — 2-layer USB-C MCU board | Full PCB workflow, manufacturing |
| 5 | 21 | Bare-metal data logger (no HAL) | Register-level embedded, DMA, protocols, power |
| 6 | 26 | **Board v2** — 4-layer custom MCU board, brought up | PCB engineering, PDN, DFM, bring-up |
| 7 | 34 | Connected multi-node system with signed OTA | RTOS, comms, Linux, security, CI |
| 8 | 39 | **Board v3** — high-speed controlled-impedance board | SI/PI/EMC, high-speed layout |
| 9 | 42 | Motor driver PCB + FOC | Power electronics, high di/dt layout, control |
| 10 | 43 | Inverted pendulum with LQR | Control theory, real hardware |
| 11 | 48 | **Autonomous robot on your own boards** | Everything, integrated |
| 12 | 52 | Full production documentation package | Systems engineering, industry readiness |

# Appendix B — The 20 Habits That Separate Engineers From Hobbyists

1. Read the datasheet **before** you buy the part, not after it doesn't work.
2. Read the errata sheet too.
3. Calculate before you build. Then measure. Then explain the difference.
4. Always current-limit a new board's first power-up.
5. Never measure ripple with the 6-inch ground clip.
6. Put test points on every rail and every critical net. Always.
7. Keep an unbroken ground plane. Watch where the return current goes.
8. Place decoupling caps at the pin, with the shortest possible loop to the plane.
9. Minimize the hot loop in every switching converter.
10. Put a ground via next to every signal via that changes reference planes.
11. Derate everything: 50% voltage on ceramics, 80% current, 20 °C thermal margin.
12. Check part lifecycle and stock before you commit to a design.
13. Version-control hardware and firmware together; tag releases.
14. Write the bring-up plan before the board arrives.
15. Log everything: measurements, bodges, failures, dead ends.
16. `volatile` is not atomic. Disable interrupts or use a lock-free structure.
17. ISRs are short. Set a flag, defer the work.
18. Never trust a sensor value you haven't calibrated and range-checked.
19. Assume your first design is wrong; budget for v2 and v3 in time and money.
20. Explain your design to someone else. If you can't, you don't understand it.

# Appendix C — If You Fall Behind

You will. It's fine. Priority order when time is short:
1. **Never skip Block C (build).** Theory can be caught up; skipped hardware time cannot.
2. Extend the phase rather than skipping the gate. The gates are the plan; the weeks are just a suggestion.
3. If you must compress: Phase 3's FPGA week (W12) and Phase 8's manipulation week (W48) are the most cuttable. Phases 4, 5, and 7 are not.
4. If you're aiming at one job track, deepen that phase and lighten the others — but do all eight gates at least once. The whole point of this path is that the boundary skills (firmware people who can lay out a board, PCB people who can debug firmware) are the rare and valuable ones.
