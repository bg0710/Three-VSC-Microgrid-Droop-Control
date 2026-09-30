# Three-VSC Microgrid with Droop-Based Power Control

MATLAB/Simulink implementation of a **three-VSC microgrid using decentralized P–f and Q–V droop control**, with synchronous `dq0` transformation, cascaded voltage/current PI control, filtered power measurement, and three parallel converter branches.

## Project Overview

The model contains:

- Three parallel voltage-source converters: **VSC 1, VSC 2 and VSC 3**
- Common three-phase AC bus/network
- Decentralized **P–f** and **Q–V** droop control
- `abc → dq0` synchronous-frame transformations
- Outer voltage control loop
- Inner current control loop
- dq-axis decoupling/feed-forward terms
- Active/reactive power calculation and low-pass filtering
- 700 V DC-link reference
- 50 Hz fundamental reference
- 10 kHz switching/control frequency

## Repository Structure

```text
Three-VSC-Microgrid-Droop-Control/
│
├── README.md
├── .gitignore
│
├── model/
│   └── Three_VSC_Microgrid_Droop_Control.slx
│
├── docs/
│   ├── Three_VSC_Microgrid_Droop_Control_Technical_Report.pdf
│   └── Three_VSC_Microgrid_Droop_Control_Technical_Report.docx
│
└── figures/
    ├── 01_microgrid_top_level.png
    ├── 02_vsc_control_structure.png
    ├── 03_current_controller.png
    ├── 04_voltage_controller.png
    ├── 05_abc_dq0_transformation.png
    └── 06_droop_controller.png
```

## Control Strategy

The primary droop relationships are:

```text
ωᵢ = ωₙ − mₚ Pᵢ

Vᵢ = Vₙ − nₚ Qᵢ
```

The dq-frame power calculation is:

```text
P = (3/2)(v_d i_d + v_q i_q)

Q = (3/2)(v_q i_d − v_d i_q)
```

The power signals are filtered before entering the droop gains. The resulting voltage/frequency references are passed to the cascaded voltage and current controllers.

## Main Model Parameters

| Parameter | Value |
|---|---:|
| Switching frequency, `fsw` | 10 kHz |
| Fundamental frequency, `fref` | 50 Hz |
| d-axis voltage reference, `Vodref` | 220√2 V |
| q-axis voltage reference, `Voqref` | 0 V |
| DC-link reference, `Vdc` | 700 V |
| Filter inductance, `Lf` | 3.5 mH |
| Filter resistance, `Rf` | 0.1 Ω |
| Filter capacitance, `Cf` | 50 μF |
| Interface inductance, `Lc` | 0.35 mH |
| Interface resistance, `Rc` | 0.05 Ω |
| Active-power droop coefficient, `mp` | 5×10⁻⁵ |
| Reactive-power droop coefficient, `np` | 3×10⁻³ |

## How to Open

1. Open MATLAB/Simulink.
2. Open `model/Three_VSC_Microgrid_Droop_Control.slx`.
3. Run the model initialization section contained in the model's initialization configuration.
4. Verify the model parameters and solver settings for your MATLAB release.
5. Run the simulation.
6. Observe `P1–P3`, `Q1–Q3`, voltage/current signals and the frequency/voltage references.

> The `.slx` file was supplied as the project model. Exact solver compatibility can depend on the MATLAB/Simulink release used to open it.

## What This Project Demonstrates

This project demonstrates:

- Converter-interfaced microgrids
- Droop-based decentralized power sharing
- Grid-forming-style P–f / Q–V control concepts
- Synchronous reference-frame control
- Cascaded voltage and current loops
- PI controller design
- dq-axis decoupling
- VSC modulation
- Active/reactive power computation
- MATLAB/Simulink system modelling

## Technical Report

The complete technical report is available in [`docs/`](docs/).

## Figures

The `figures/` directory contains the major model and subsystem diagrams used in the report.

## Future Extensions

- Add load-step and breaker-event waveform results
- Quantify P/Q sharing error among VSCs
- Compare different droop coefficients
- Add secondary voltage/frequency restoration
- Test unequal converter ratings
- Perform THD and harmonic analysis
- Evaluate controller sensitivity to filter and grid parameters

## Author

**Bhargab Gogoi**  
M.Tech – Smart Grid  
Electrical Engineering

