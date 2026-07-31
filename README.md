# LOSVD_regeneration
# Mock IFU from EDF

A Python class for generating mock IFU observations from an extended distribution function (EDF) using `agama` and `popkinmocks`.

## Workflow

The `MockIFUFromEDF` class:

1. Samples particles from a galaxy model.
2. Assigns stellar ages and metallicities from the EDF.
3. Projects positions and velocities using the galaxy inclination and position angle.
4. Rescales the projected galaxy to the chosen IFU size.
5. Generates a mock IFU cube using MILES stellar population models.
6. Calculates and plots the light-weighted LOSVD of the brightest spaxel.

## Requirements

```text
numpy
matplotlib
astropy
agama
popkinmocks
```

## Usage

```python
mock = MockIFUFromEDF(
    edf=edf,
    actionfinder=actionfinder,
    potential=potential,
    N_samples=100000,
    N_mock=50000,
    inc_deg=60,
    pa_deg=30
)

mock.run()
```

### Key Parameters

* `N_samples`, `N_mock` — particle sampling
* `inc_deg` — inclination
* `pa_deg` — position angle
* `nx1`, `nx2` — spatial IFU resolution
* `nv` — velocity resolution
* `vrng` — velocity range

## Outputs

The main outputs are:

* `x1`, `x2`, `v` — projected particle positions and line-of-sight velocities
* `cube` — generated mock IFU cube
* `p_v_x` — light-weighted LOSVD
