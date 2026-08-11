# Eddy Covariance Variables

This page documents diagnostic variables for the eddy covariance (EC) measurement system.

## Wind Components

### u - Longitudinal Wind

| | |
|---|---|
| **Symbol** | u, u' |
| **Units** | m/s |
| **Definition** | Horizontal wind component aligned with mean wind direction |
| **Typical Range** | -5 to +15 m/s (mean), ±5 m/s (fluctuations) |

### v - Lateral Wind

| | |
|---|---|
| **Symbol** | v, v' |
| **Units** | m/s |
| **Definition** | Horizontal wind component perpendicular to mean wind |
| **Typical Range** | Near 0 m/s (mean after rotation), ±3 m/s (fluctuations) |

### w - Vertical Wind

| | |
|---|---|
| **Symbol** | w, w' |
| **Units** | m/s |
| **Definition** | Vertical wind component |
| **Typical Range** | ~0 m/s (mean after rotation), ±2 m/s (fluctuations) |

!!! note "Coordinate Rotation"
    After proper coordinate rotation:
    - $\overline{v} \approx 0$
    - $\overline{w} \approx 0$
    - Only $\overline{u}$ should be non-zero

## Turbulent Fluxes

### CO₂ Flux

| | |
|---|---|
| **Symbol** | F_CO₂ or F_c |
| **Units** | μmol/m²/s |
| **Definition** | Vertical turbulent flux of CO₂ |
| **Calculation** | $F_{CO_2} = \overline{w'c'}$ |
| **Typical Range** | -30 to +15 μmol/m²/s |

**Sign Convention**:
- **Negative**: Downward flux (uptake by vegetation)
- **Positive**: Upward flux (respiration)

**Typical Daily Pattern**:

| Time | Typical Flux | Process |
|------|-------------|---------|
| 06:00 | +5 μmol/m²/s | Early respiration |
| 12:00 | -20 μmol/m²/s | Peak photosynthesis |
| 18:00 | -5 μmol/m²/s | Declining uptake |
| 24:00 | +10 μmol/m²/s | Nighttime respiration |

### Sensible Heat Flux

| | |
|---|---|
| **Symbol** | H |
| **Units** | W/m² |
| **Definition** | Vertical turbulent flux of sensible heat |
| **Calculation** | $H = \rho c_p \overline{w'T'}$ |
| **Typical Range** | -50 to +400 W/m² |

Where:
- $\rho$ = air density (kg/m³)
- $c_p$ = specific heat of air (1005 J/kg/K)
- $T$ = air temperature (K)

### Latent Heat Flux

| | |
|---|---|
| **Symbol** | LE or λE |
| **Units** | W/m² |
| **Definition** | Vertical turbulent flux of latent heat (evapotranspiration) |
| **Calculation** | $LE = \lambda \overline{w'\rho_v'}$ |
| **Typical Range** | 0 to +500 W/m² |

Where:
- $\lambda$ = latent heat of vaporization (2.45 MJ/kg)
- $\rho_v$ = water vapor density (g/m³)

## Turbulent Statistics

### Friction Velocity

| | |
|---|---|
| **Symbol** | u* |
| **Units** | m/s |
| **Definition** | Measure of turbulent intensity in surface layer |
| **Calculation** | $u_* = \left[(\overline{u'w'})^2 + (\overline{v'w'})^2\right]^{1/4}$ |
| **Typical Range** | 0.1 to 1.0 m/s |

**Importance**:
- Characterizes turbulent mixing
- Critical for flux-gradient calculations
- Quality control parameter (u* threshold)
- Footprint calculations

**Quality Threshold**:
- Nighttime fluxes typically filtered when $u_* < 0.1$ m/s (site-specific)

### Obukhov Length

| | |
|---|---|
| **Symbol** | L |
| **Units** | m |
| **Definition** | Characteristic length scale of atmospheric stability |
| **Calculation** | $L = -\frac{u_*^3 \overline{T}}{\kappa g \overline{w'T'}}$ |
| **Typical Range** | -∞ to +∞ |

**Interpretation**:

| L Value | Stability | Typical Time | Mixing |
|---------|-----------|--------------|--------|
| L < 0 | Unstable | Daytime | Enhanced |
| L → ±∞ | Neutral | Cloudy/Windy | Moderate |
| L > 0 | Stable | Nighttime | Suppressed |