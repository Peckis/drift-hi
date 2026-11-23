# drifthi — a drift-scan HI (21 cm) pipeline for a small dish + RTL-SDR

WORK IN PROGRESS

End-to-end pipeline for a DIY hydrogen-line telescope:

> 80 cm offset TV dish → cantenna feed → SAWbird H1 (LNA + filter) →
> RTL-SDR Blog V4 → Raspberry Pi (acquisition) → any PC (processing)


## Tools

| command          | runs on | discription |
|------------------|---------|--------------|
| `hi-observe`     | Pi      | continuous frequency-switched acquisition via `rtl_tcp` |
| `hi-process`     | PC      | calibration → RFI flagging → LSR regridding → baselines → waterfalls → science extraction |
| `hi-fetch-hi4pi` | PC      | downloads the HI4PI survey tiles for your declination strip, builds a compact cache |
| `hi-compare`     | PC      | cross-correlates your data with HI4PI: **fits your true pointing** and absolute calibration, makes side-by-side/overlay plots |
| `hi-simulate`    | PC      | fakes a full raw session (sky + noise + bandpass + RFI) so you can test everything before the telescope is done |
| `hi-stack`       | PC      | combines several processed sessions into one deeper RA map |
| `hi-check`       | both    | hardware bench test: ADC health, bias tee, bandpass, noise vs. radiometer limit |
| `hi-spectrum`    | PC      | analyze any single HI spectrum CSV (e.g. from the PICTOR web telescope): baseline, Gaussians, LSR, HI4PI overlay + Kelvin calibration |
| `hi-sunscan`     | PC      | solar pointing calibration: fits the Sun's drift through the beam from a daytime session |
| `hi-skymap`      | PC      | all-sky Aitoff map of every beam-smeared track you've observed, with the Milky Way band and coverage percentages |

