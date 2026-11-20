# Lab 02 — Fully Differential Current-Mirror OTA

Full write-up: Chapter 2 of the [report](../report/AICD_lab_report.pdf).

**Topology:** p-MOS input differential pair, current-mirror loads with gain to the output branches, and common-mode feedback (CMFB).

## Process

1. **Initial design:** DC operating point, g<sub>m</sub> and r<sub>o</sub> per device, and current steering in the differential pair. A<sub>dd0</sub> = 22.6 dB and f<sub>u</sub> = 690 MHz, below specification.
2. **Common-mode analysis:** very low common-mode gain, so CMRR is high.
3. **Monte Carlo offset (N = 100):** V<sub>OS</sub> = 7.28 mV for the initial design.
4. **Redesign:** re-biased the input pair (I<sub>D</sub> ≈ 188 µA), then widened it from 20 µm to 33 µm to raise g<sub>m1</sub> and reach the GBW target.

## Final design vs specification

| Parameter | Specification | Simulated |
|---|---|---|
| A<sub>dd0</sub> | > 30 dB | **31.86 dB** |
| GBW | ≥ 1 GHz | **1.01 GHz** |
| V<sub>OS</sub> (σ, Monte Carlo) | < 4 mV | **3.38 mV** |

![OTA schematic](figures/schematic.png)
![Final Bode plot](figures/final-bode.png)
![Final offset distribution](figures/final-offset-montecarlo.png)
