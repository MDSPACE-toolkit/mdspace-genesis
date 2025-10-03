# NMMD / MDSPACE — Extension of GENESIS 2.1.6

To build GENESIS:

```bash
cd /path/to/genesis
autoreconf -fi
./configure
make install
````

---

## Usage: NMMD

The NMMD input file is similar to GENESIS (see [usage guide](https://www.r-ccs.riken.jp/labs/cbrt/usage/)).

To use NMMD, choose `integrator = NMMD` in the `[DYNAMICS]` section and add a `[NMMD]` section in the input file:

```text
[DYNAMICS]
integrator = NMMD

[NMMD]
nm_number = 10
nm_mass   = 10.0
nm_file   = /path/to/nm/file
nm_dt     = 0.001
```

### Parameters

| Parameter | Description                                                                            | Default |
| --------- | -------------------------------------------------------------------------------------- | ------- |
| nm_number | Number of normal modes to use after skipping the first 6 modes (e.g., 10 → modes 7–16) | 10      |
| nm_mass   | Mass value for normal modes                                                            | 10.0    |
| nm_file   | File containing the normal mode vectors                                                | —       |
| nm_dt     | Normal mode integration time step                                                      | 0.001   |

### Limitations

* NMMD is available **only** for ATDYN.
* NMMD requires **LANGEVIN** temperature control in the NVT ensemble.
* SHAKE/RATTLE algorithms must be **turned off**.

---

## Usage: MDSPACE

The MDSPACE extension allows fitting images instead of volumes.

Example configuration in `[EXPERIMENTS]`:

```text
[EXPERIMENTS]
emfit = YES                            # YES/NO
emfit_type = IMAGE                     # VOLUME/IMAGE
emfit_target = path/to/image/file.spi  # 2D SPIDER file
emfit_sigma = 2.0                      # Sigma of 2D Gaussian
emfit_tolerance = 0.01                 # Gaussian truncation threshold
emfit_period = 1                        # Not used
emfit_roll_angle = 0.0                  # Euler roll angle (degrees)
emfit_tilt_angle = 0.0                  # Euler tilt angle (degrees)
emfit_yaw_angle = 0.0                   # Euler yaw angle (degrees)
emfit_shift_x = 0.0                     # Shift in x direction (pixels)
emfit_shift_y = 0.0                     # Shift in y direction (pixels)
emfit_pixel_size = 1.0                  # Size of a pixel in Angstrom
```

### Limitations

* MDSPACE is available **only** for ATDYN.

---

## GENESIS Source Code

* **GENESIS 2.1.5**: See the [GENESIS website](https://mdgenesis.org/) for source code and documentation.
>>>>>>> 6ce2139 ([feat] update readme)
