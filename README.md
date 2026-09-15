# Transfer-function dataset

This supplementary dataset contains the spreading-integrated response amplitude operators (RAOs) and synthetic-case definitions used in the accompanying manuscript.

## Files

| File              | Contents                                                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `raos.npz`        | RAO array with shape `(10 sensors, 5 spreading values, 24 headings, 30 frequencies)` and the corresponding coordinate vectors. |
| `raos.csv`        | The same 36,000 RAO values in long format.                                                                                     |
| `scenarios.csv`   | Definitions of the 120 sea-state, heading, and wave-phase scenarios.                                                           |
| `noise_cases.csv` | Definitions of the 1,920 synthetic measurement-noise cases.                                                                    |
| `noise_seeds.csv` | Per-sensor Gaussian-noise seeds used in each case.                                                                             |

The `.npz` and `.csv` files contain equivalent RAO data.

## Experimental grid

Ten representative sea states from NDBC station 41002 were combined with six relative headings and two wave-phase realizations, giving $10 \times 6 \times 2 = 120$ scenarios. The RAO grid contains 24 headings from $0^\circ$ to $345^\circ$ in $15^\circ$ increments, spreading parameters $s \in {1,2,3,4,5}$, and 30 frequencies from 0.0400 to 0.3333 Hz.

Measurement-noise cases and their random seeds are provided in the corresponding CSV files.

## RAO convention

The supplied values are scalar strain-response amplitudes per unit wave amplitude, already integrated over directional spreading. They are not squared.

For sensor $i$, the structural response spectrum is obtained from

$$
S_{y_i}(f)
=
G_i(f,\theta,s)\,S_{\eta}(f),
$$

where $S_{\eta}(f)$ is the incident wave spectrum and the spectral response gain is

$$
G_i(f,\theta,s)
=
\left[
\mathrm{RAO}_i(f,\theta,s)
\right]^2.
$$

The supplied RAOs therefore correspond to the spreading-integrated response amplitudes used to construct $G_i$ in the formulation presented in the manuscript.

## Reproducibility

The software implementation is proprietary and is not distributed. The mathematical formulations and evaluation procedure are provided in the manuscript, while the supplied RAOs and scenario definitions provide the inputs required to independently reimplement the pairwise and multichannel estimators.

Random seeds are included for scenario traceability and documentation of the paired noise design.
