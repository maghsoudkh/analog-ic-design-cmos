# Analog CMOS Integrated Circuit Design — From Current Mirrors to a Bandgap Reference

Laboratory portfolio from **Analogue Integrated Circuit Design**, M.Sc. in Electronic Engineering, Università degli Studi di Padova (A.Y. 2025/2026).

Four transistor-level design labs in a **130 nm CMOS process** (V<sub>DD</sub> = 1.2 V), designed and verified in **Cadence Virtuoso (ADE)**. Each lab follows the same flow: hand calculations from a simple device model, schematic and testbench, simulation-based optimisation, then verification against the specifications. Verification uses process corners and Monte Carlo mismatch analysis.

📄 **[Full report (57 pages, PDF)](report/AICD_lab_report.pdf)** · LaTeX source in [`report/latex`](report/latex)

## Results at a glance

| Lab | Circuit | Key results |
|---|---|---|
| [01](lab01-current-mirrors/) | Simple and wide-swing cascode current mirrors | Corner analysis (TT/SS/FF, −20…85 °C) and Monte Carlo (N = 100). Measured σ(ΔI<sub>OUT</sub>) = 5.18 µA vs Pelgrom estimate 6.32 µA. Cascode R<sub>out</sub> = 147 kΩ after L-scaling |
| [02](lab02-fully-differential-ota/) | Fully differential current-mirror OTA with CMFB | **Meets all specs:** A<sub>dd0</sub> = 31.9 dB (> 30), GBW = 1.01 GHz (≥ 1), V<sub>OS</sub> = 3.38 mV (< 4) |
| [03](lab03-two-stage-ota-feedback-amplifier/) | Two-stage Miller OTA in a capacitive-feedback amplifier | Redesigned from PM = 23° to **PM = 61.4°**, T<sub>0</sub> = 58.2 dB, f<sub>c</sub> = 50.5 MHz, **V<sub>OS</sub> = 0.90 mV**, P = 1.2 mW |
| [04](lab04-low-voltage-bandgap/) | Low-voltage bandgap voltage reference | **V<sub>REF</sub> = 800.05 mV**, **≈ 2.5 ppm/°C** over −40…85 °C (ΔV<sub>REF</sub> ≈ 0.25 mV; 3.4 ppm/°C local at 27 °C), line sensitivity 113 mV/V |

## Skills demonstrated

- **Analog design methodology:** g<sub>m</sub>/I<sub>D</sub> and overdrive-based hand sizing, then simulation-driven refinement.
- **Frequency compensation:** Miller capacitance with a nulling resistor, and loop-gain and phase-margin analysis with an opened-loop testbench.
- **Fully differential circuits:** common-mode feedback (CMFB), differential- and common-mode AC analysis.
- **Robustness and yield:** process corners, temperature sweeps, Monte Carlo mismatch, Pelgrom-model checks, input-referred offset.
- **Precision references:** PTAT/CTAT compensation, resistor tuning for zero TC, supply sensitivity.
- **Layout-aware effects:** finger count and gate-length dependence of mirror accuracy.

## Repository structure

```
lab01-current-mirrors/                    Simple and wide-swing cascode mirrors
lab02-fully-differential-ota/             Current-mirror OTA with CMFB
lab03-two-stage-ota-feedback-amplifier/   Two-stage OTA in a capacitive-feedback amplifier
lab04-low-voltage-bandgap/                Low-voltage bandgap reference
report/                                   Full report (PDF) and LaTeX source
```

## Authors

- **Amirkhashayar Maghsoud**
- Simone Sbrescia
