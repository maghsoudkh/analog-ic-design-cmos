# Lab 04: low-voltage bandgap voltage reference

Chapter 4 of the [report](../report/AICD_lab_report.pdf) has the full write-up.

The target is a sub-1 V reference, V<sub>REF</sub> = 0.8 V, from a 1.2 V supply, with a temperature coefficient close to zero.

## Design

We started the hand design from I<sub>1</sub> = 10 µA and a diode area ratio N = 4. R<sub>1</sub> = U<sub>T</sub> ln N / I<sub>1</sub> sets the PTAT current, R<sub>2</sub> ≈ 54 kΩ cancels the CTAT slope, and R<sub>3</sub> scales the output to 0.8 V. The PMOS mirror uses L = 1.2 µm to limit channel-length modulation, and W ≈ 8.6 µm follows from |V<sub>OV</sub>| = 0.25 V.

A first temperature sweep from −40 to 85 °C confirmed the PTAT and CTAT behaviour and gave a TC of 32 ppm/°C. We then tuned the resistors in order. R<sub>1</sub> sets I<sub>D1</sub> to 10.00 µA, R<sub>2</sub> minimizes the TC through a coarse and a fine sweep, and R<sub>3</sub> sets the absolute V<sub>REF</sub>.

## Final results

| Metric | Value |
|---|---|
| V<sub>REF</sub> at 27 °C | 800.05 mV |
| Local TC at 27 °C | ≈ 3.4 ppm/°C |
| TC over −40 to 85 °C, box method | ≈ 2.5 ppm/°C, with a total ΔV<sub>REF</sub> of about 0.25 mV. The target was 2 ppm/°C. |
| Line sensitivity dV<sub>REF</sub>/dV<sub>DD</sub> | 113 mV/V for V<sub>DD</sub> ± 10 % |

The remaining curvature of V<sub>REF</sub>(T) comes from the temperature dependence of I<sub>S</sub>, which the first-order hand model leaves out. The minimum of the curve sits near 0 °C, below the centre of the range. A slightly smaller R<sub>2</sub> would move it to the centre and lower the full-range TC.

![Bandgap schematic](figures/schematic.png)
![PTAT and CTAT voltages](figures/ptat-ctat.png)
![V_REF against temperature](figures/vref-vs-temperature.png)
![Supply sensitivity](figures/vdd-sensitivity.png)
