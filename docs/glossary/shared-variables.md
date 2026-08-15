# Shared Variables

Variables common to both the flux-gradient and eddy covariance systems.

## Temperature

### Air Temperature

| | |
|---|---|
| **Symbol** | T_air |
| **Units** | °C or K |
| **Definition** | Ambient air temperature at measurement height |
| **Measurement** | Thermistor or thermocouple in aspirated shield |

### Sonic Temperature

| | |
|---|---|
| **Symbol** | T_sonic or T_s |
| **Units** | °C or K |
| **Definition** | Temperature derived from sonic anemometer (speed of sound) |
| **Relationship** | $T_s = T(1 + 0.51q)$ where q is specific humidity |

!!! note "Virtual Temperature"
    Sonic temperature includes moisture effects and must be corrected to obtain actual air temperature.

## Humidity

### Relative Humidity

| | |
|---|---|
| **Symbol** | RH |
| **Units** | % |
| **Definition** | Ratio of actual to saturation vapor pressure |
| **Typical Range** | 20-100% |

### Specific Humidity

| | |
|---|---|
| **Symbol** | q |
| **Units** | g/kg |
| **Definition** | Mass of water vapor per mass of moist air |
| **Calculation** | $q = 0.622 \frac{e}{P-0.378e}$ |

Where:

- $e$ = vapor pressure (Pa)
- $P$ = total pressure (Pa)

## Radiation

### Net Radiation

| | |
|---|---|
| **Symbol** | R_n |
| **Units** | W/m² |
| **Definition** | Net radiative flux at surface |
| **Calculation** | $R_n = SW_{in} - SW_{out} + LW_{in} - LW_{out}$ |

Components:

- SW_in: Incoming shortwave
- SW_out: Reflected shortwave
- LW_in: Incoming longwave
- LW_out: Outgoing longwave