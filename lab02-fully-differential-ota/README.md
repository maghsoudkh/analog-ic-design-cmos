# Lab 02: fully differential current-mirror OTA

Chapter 2 of the [report](../report/AICD_lab_report.pdf) has the full write-up.

The OTA has a p-MOS input pair, current-mirror loads that add gain on the way to the output branches, and common-mode feedback.

## Design steps

1. We simulated the initial design's DC operating point, the g<sub>m</sub> and r<sub>o</sub> of each device, and the current steering in the input pair. It gave A<sub>dd0</sub> = 22.6 dB and f<sub>u</sub> = 690 MHz, both below specification.
2. The common-mode gain is very low, so the CMRR is high.
3. A Monte Carlo run with N = 100 gave an offset of 7.28 mV for the initial design.
4. We re-biased the input pair to I<sub>D</sub> ≈ 188 µA, then widened it from 20 µm to 33 µm to raise g<sub>m1</sub> and reach the GBW target.

## Final design against the specification

| Parameter | Specification | Simulated |
|---|---|---|
| A<sub>dd0</sub> | > 30 dB | 31.86 dB |
| GBW | ≥ 1 GHz | 1.01 GHz |
| V<sub>OS</sub>, σ from Monte Carlo | < 4 mV | 3.38 mV |

![OTA schematic](figures/schematic.png)
![Bode plot of the final design](figures/final-bode.png)
![Offset distribution of the final design](figures/final-offset-montecarlo.png)
