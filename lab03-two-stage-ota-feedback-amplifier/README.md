# Lab 03: two-stage OTA in a capacitive-feedback amplifier

Chapter 3 of the [report](../report/AICD_lab_report.pdf) has the full write-up.

## Starting point

The given OTA sits in a capacitive-feedback loop with β = 0.33 and an ideal gain C<sub>s</sub>/C<sub>f</sub> = 2. It had T<sub>0</sub> = 37.8 dB, f<sub>c</sub> = 251 MHz and a phase margin of only 23°, and its closed-loop response showed strong peaking and ringing.

## Redesign from the specification

- A static error of at most 0.2 % needs T<sub>0</sub> ≥ 1/ε<sub>0</sub>, so A<sub>dd0</sub> must be about 1500 or more.
- A dynamic error of at most 0.2 % at 20 ns needs ω<sub>c</sub> ≥ −ln(0.002)/20 ns, so f<sub>c</sub> ≈ 50 MHz.
- Each branch is biased at I<sub>D</sub> = 225 µA with V<sub>OV</sub> = 0.15 V, so g<sub>m</sub> = 3 mS. The required r<sub>o</sub> sets the lengths, and the square-law model sets the widths.
- Compensation uses a Miller capacitor C<sub>C</sub> ≈ 1.6 pF with a nulling resistor R<sub>Z</sub>, both tuned in simulation.

## Final results

| Metric | Value |
|---|---|
| Loop gain T<sub>0</sub> | 58.2 dB |
| Crossover f<sub>c</sub> | 50.5 MHz |
| Phase margin | 61.4°, specification 60 to 70° |
| Input offset V<sub>OS</sub>, Monte Carlo with N = 100 | 0.90 mV, specification ≤ 2 mV |
| Power | 1.20 mW, I<sub>TOT</sub> ≈ 1 mA at 1.2 V |
| Closed-loop gain | 1.92 against an ideal 2 |

Two specifications were not met. The static error is 4.1 % and the dynamic error is 5.2 %, against targets of 0.2 %. The report traces both to a non-dominant pole near crossover, which breaks the single-pole settling assumption, and discusses the trade-off.

![Loop gain](figures/loop-gain.png)
![Step response](figures/step-response.png)
![Offset distribution](figures/offset-montecarlo.png)
