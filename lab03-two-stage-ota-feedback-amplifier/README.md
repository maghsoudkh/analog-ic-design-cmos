# Lab 03 — Two-Stage OTA and Capacitive-Feedback Amplifier

Full write-up: Chapter 3 of the [report](../report/AICD_lab_report.pdf).

## Starting point

The given OTA in a capacitive-feedback loop (β = 0.33, ideal gain C<sub>s</sub>/C<sub>f</sub> = 2) had T<sub>0</sub> = 37.8 dB, f<sub>c</sub> = 251 MHz and only **23° phase margin**. The closed-loop response showed strong peaking and ringing.

## Redesign from the specifications

- **Static error ≤ 0.2 %** → T<sub>0</sub> ≥ 1/ε<sub>0</sub> → A<sub>dd0</sub> ≳ 1500.
- **Dynamic error ≤ 0.2 % at 20 ns** → ω<sub>c</sub> ≥ −ln(0.002)/20 ns → f<sub>c</sub> ≈ 50 MHz.
- **Biasing:** I<sub>D</sub> = 225 µA per branch, V<sub>OV</sub> = 0.15 V, g<sub>m</sub> = 3 mS. Lengths set from the required r<sub>o</sub>, and widths from the square-law model.
- **Compensation:** Miller capacitance C<sub>C</sub> ≈ 1.6 pF with a nulling resistor R<sub>Z</sub>, then tuned in simulation.

## Final results

| Metric | Value |
|---|---|
| Loop gain T<sub>0</sub> | 58.2 dB |
| Crossover f<sub>c</sub> | 50.5 MHz |
| Phase margin | **61.4°** (spec 60–70°) |
| Input offset V<sub>OS</sub> (Monte Carlo, N = 100) | **0.90 mV** (spec ≤ 2 mV) |
| Power | 1.20 mW (I<sub>TOT</sub> ≈ 1 mA at 1.2 V) |
| Closed-loop gain | 1.92 (ideal 2) |

**Specifications not met:** the static (4.1 %) and dynamic (5.2 %) errors missed the very tight 0.2 % targets. The report traces this to a non-dominant pole near crossover, which breaks the single-pole settling assumption, and discusses the trade-off.

![Loop gain](figures/loop-gain.png)
![Step response](figures/step-response.png)
![Offset distribution](figures/offset-montecarlo.png)
