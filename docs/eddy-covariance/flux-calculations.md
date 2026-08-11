# Flux Calculations

## Basic Steps

```mermaid
flowchart LR
    A[Raw 10 Hz Data] --> B[Despiking]
    B --> C[Coordinate Rotation]
    C --> D[Linear Detrending]
    D --> E[Covariance Calculation]
    E --> F[WPL Correction]
    F --> G[Quality Flags]
    G --> H[30-min Flux]

    style A fill:#e1f5ff
    style H fill:#c8e6c9
```

### 1. Coordinate Rotation

Rotate coordinate system so mean vertical velocity is zero:

- **Double rotation**: Most common method
- **Planar fit**: For complex terrain (requires long-term data)

### 2. Linear Detrending

Remove low-frequency trends that aren't turbulent:

$$
x'(t) = x(t) - [a + bt]
$$

### 3. Covariance Calculation

For CO₂ flux:

$$
F_{CO_2} = \overline{w'c'} = \frac{1}{N}\sum_{i=1}^{N} w'_i \cdot c'_i
$$

### 4. WPL Correction

**Webb-Pearman-Leuning (WPL) correction** accounts for density effects:

$$
F_{CO_2,corrected} = F_{CO_2,measured} + \mu \cdot \overline{c} \cdot E + (1 + \mu \cdot \sigma) \cdot \overline{c} \cdot \frac{H}{\overline{T}}
$$

where:

- $E$ = water vapor flux
- $H$ = sensible heat flux
- $\mu$ = ratio of molecular masses
- $\sigma$ = ratio of molar densities

!!! warning "Critical for Open-Path Sensors"
    WPL corrections are essential for open-path analyzers and can be 10-20% of measured flux.

## Example Fluxes

### CO₂ Flux

**Daytime (Photosynthesis)**:

$$
F_{CO_2} < 0 \quad \text{(uptake)}
$$

**Nighttime (Respiration)**:

$$
F_{CO_2} > 0 \quad \text{(emission)}
$$

### Latent Heat Flux

Evapotranspiration from surface:

$$
LE = \lambda \cdot E = \lambda \cdot \overline{w'\rho_v'}
$$

where:

- $\lambda$ = latent heat of vaporization (2.45 MJ/kg)
- $E$ = water vapor flux
- $\rho_v$ = water vapor density

### Sensible Heat Flux

$$
H = \rho \cdot c_p \cdot \overline{w'T'}
$$

where:

- $\rho$ = air density
- $c_p$ = specific heat of air (1005 J/kg/K)
- $T$ = temperature

### Momentum Flux (Friction Velocity)

$$
u_* = \left[\left(\overline{u'w'}\right)^2 + \left(\overline{v'w'}\right)^2\right]^{1/4}
$$

Friction velocity ($u_*$) characterizes turbulent intensity and is crucial for:

- Flux-gradient calculations
- Footprint modeling
- Quality control