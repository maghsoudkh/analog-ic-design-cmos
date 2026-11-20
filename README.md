# Analog CMOS integrated circuit design: from current mirrors to a bandgap reference

Lab work from the Analogue Integrated Circuit Design course, M.Sc. in Electronic Engineering, University of Padova, academic year 2025/2026.

The four labs are transistor-level designs in a 130 nm CMOS process with V<sub>DD</sub> = 1.2 V, designed and simulated in Cadence Virtuoso ADE. Each lab starts from hand calculations with a simple device model, moves to a schematic and testbench, refines the design in simulation, and checks it against the specification with process corners and Monte Carlo mismatch analysis.

[Full report, 57 pages (PDF)](report/AICD_lab_report.pdf) · LaTeX source in [`report/latex`](report/latex)

## Main results

| Lab | Circuit | Results |
|---|---|---|
| [01](lab01-current-mirrors/) | Simple and wide-swing cascode current mirrors | Corners TT, SS and FF from −20 to 85 °C, and Monte Carlo with N = 100. The simulated σ(ΔI<sub>OUT</sub>) of 5.18 µA is close to the Pelgrom estimate of 6.32 µA. Scaling L raises the cascode R<sub>out</sub> to 147 kΩ. |
| [02](lab02-fully-differential-ota/) | Fully differential current-mirror OTA with CMFB | Meets every specification: A<sub>dd0</sub> = 31.9 dB against > 30 dB, GBW = 1.01 GHz against ≥ 1 GHz, V<sub>OS</sub> = 3.38 mV against < 4 mV. |
| [03](lab03-two-stage-ota-feedback-amplifier/) | Two-stage Miller OTA in a capacitive-feedback amplifier | The redesign raises the phase margin from 23° to 61.4°, with T<sub>0</sub> = 58.2 dB, f<sub>c</sub> = 50.5 MHz, V<sub>OS</sub> = 0.90 mV and P = 1.2 mW. |
| [04](lab04-low-voltage-bandgap/) | Low-voltage bandgap voltage reference | V<sub>REF</sub> = 800.05 mV. V<sub>REF</sub> varies by about 0.25 mV from −40 to 85 °C, or about 2.5 ppm/°C, and the local TC at 27 °C is 3.4 ppm/°C. Line sensitivity is 113 mV/V. |

## Methods used

- Hand sizing from g<sub>m</sub>/I<sub>D</sub> and overdrive voltage, refined in simulation.
- Frequency compensation with a Miller capacitor and nulling resistor, checked with loop-gain and phase-margin analysis on an opened-loop testbench.
- Fully differential circuits with common-mode feedback, and differential and common-mode AC analysis.
- Process corners, temperature sweeps, Monte Carlo mismatch, Pelgrom-model checks and input-referred offset.
- PTAT/CTAT compensation, resistor tuning for a low TC, and supply sensitivity.
- The effect of finger count and gate length on mirror accuracy.

## Repository layout

```
lab01-current-mirrors/                    Simple and wide-swing cascode mirrors
lab02-fully-differential-ota/             Current-mirror OTA with CMFB
lab03-two-stage-ota-feedback-amplifier/   Two-stage OTA in a capacitive-feedback amplifier
lab04-low-voltage-bandgap/                Low-voltage bandgap reference
report/                                   Full report as PDF, and its LaTeX source
```

## Authors

- Amirkhashayar Maghsoud
- Simone Sbrescia

## License

The report, its LaTeX source, the figures and the text are licensed under [CC BY 4.0](LICENSE). You may reuse them with credit to the authors listed above.
