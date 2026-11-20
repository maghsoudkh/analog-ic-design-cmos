# Lab 01 — CMOS Current Mirrors

Full write-up: Chapter 1 of the [report](../report/AICD_lab_report.pdf).

## Simple n-MOS mirror (N = 2.5, I<sub>REF</sub> = 100 µA)

- **DC sweep:** I<sub>OUT</sub> equals N·I<sub>IN</sub> only at V<sub>OUT</sub> = 510.8 mV, where V<sub>DS1</sub> = V<sub>DS2</sub>. Elsewhere, channel-length modulation sets the error.
- **Output impedance:** R<sub>o</sub> ≈ 25 kΩ from the AC admittance. The output pole is predicted at 1.32 GHz and simulated at 2.88 GHz; the gap comes from parasitics outside the hand model.
- **Geometry:** sweeps of gate length (100–500 nm) and finger count (4 vs 10) show the layout-dependent shifts in V<sub>th</sub> and mirror accuracy.

![Simple mirror schematic](figures/schematic-simple-mirror.png)
![I_OUT vs V_OUT](figures/iout-vs-vout.jpg)

## Process spread and mismatch

| Corner | V<sub>IN</sub> [mV] | ΔI<sub>OUT</sub> [µA] |
|---|---|---|
| TT, 27 °C | 686.0 | −3.10 |
| SS, −20 °C | 751.4 | −5.52 |
| FF, 85 °C | 630.8 | −1.16 |

The Monte Carlo run (N = 100) gives μ(ΔI<sub>OUT</sub>) = −3.09 µA, the systematic error, and σ = 5.18 µA, the random mismatch. This agrees with the Pelgrom-model hand estimate of 6.32 µA.

![Monte Carlo current error](figures/montecarlo-current-error.jpg)

## Wide-swing cascode mirror

- Bias device M5 was sized by parametric sweep (W<sub>5</sub> = 1.06 µm) so that all four V<sub>DS</sub> values land near 250 mV.
- Scaling every L by √3 raises R<sub>out</sub> to **146.8 kΩ** (theory ≈ 110 kΩ), at the cost of 2.25× area.

![Wide-swing cascode](figures/schematic-wide-swing-cascode.png)
![Cascode output admittance](figures/cascode-output-admittance.png)
