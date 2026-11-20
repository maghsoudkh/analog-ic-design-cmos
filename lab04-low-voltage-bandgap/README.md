# Lab 04 — Low-Voltage Bandgap Voltage Reference

Full write-up: Chapter 4 of the [report](../report/AICD_lab_report.pdf).

**Target:** a sub-1 V reference, V<sub>REF</sub> = 0.8 V, from a 1.2 V supply, with near-zero temperature coefficient.

## Design

- **Hand design:** I<sub>1</sub> = 10 µA and diode area ratio N = 4. Then R<sub>1</sub> = U<sub>T</sub> ln N / I<sub>1</sub> sets the PTAT current, R<sub>2</sub> ≈ 54 kΩ cancels the CTAT slope, and R<sub>3</sub> scales the output to 0.8 V.
- **PMOS mirror:** L = 1.2 µm to suppress channel-length modulation, and W ≈ 8.6 µm from |V<sub>OV</sub>| = 0.25 V.
- **Characterisation:** PTAT and CTAT node voltages and branch currents across −40…85 °C. The initial TC is 32 ppm/°C.
- **Sequential resistor tuning:** R<sub>1</sub> sets I<sub>D1</sub> = 10.00 µA, R<sub>2</sub> zeroes the TC with coarse and fine sweeps, and R<sub>3</sub> sets the absolute V<sub>REF</sub>.

## Final results

| Metric | Value |
|---|---|
| V<sub>REF</sub> at 27 °C | **800.05 mV** |
| Local TC at 27 °C | ≈ 3.4 ppm/°C |
| Box-method TC, −40…85 °C | **≈ 2.5 ppm/°C** (total ΔV<sub>REF</sub> ≈ 0.25 mV; target 2 ppm/°C) |
| Line sensitivity dV<sub>REF</sub>/dV<sub>DD</sub> | 113 mV/V (V<sub>DD</sub> ± 10 %) |

The remaining curvature in V<sub>REF</sub>(T) is the expected second-order effect of the temperature dependence of I<sub>S</sub>, which the first-order hand model leaves out. The curve's minimum sits near 0 °C instead of the centre of the range. A slightly smaller R<sub>2</sub> would centre it and lower the full-range TC further.

![Bandgap schematic](figures/schematic.png)
![PTAT and CTAT](figures/ptat-ctat.png)
![V_REF vs temperature](figures/vref-vs-temperature.png)
![Supply sensitivity](figures/vdd-sensitivity.png)
