# Eddy-Covariance Instrumentation

The ON1 site can be configured with one of two EC system setups. Verify the current configuration.

## Configuration 1: IRGASON

![IRGASON Sensor](../../images/irgason.jpg){ align=right width="300" }

**Integrated CO₂/H₂O Open-Path Gas Analyzer and 3-D Sonic Anemometer**

The IRGASON combines gas analysis and wind measurement in a single, co-located instrument, minimizing flux loss from sensor separation.

### Specifications

| Parameter | Value |
|-----------|-------|
| Manufacturer | Campbell Scientific |
| Maximum measurement rate | 60 Hz |
| User-programmable output | 5, 10, 12.5, or 20 Hz |
| Gas analyzer path length | 15.37 cm |
| CO₂ calibrated range | 0-1000 μmol/mol |
| H₂O calibrated range | 0-72 mmol/mol |

### Advantages
- Co-located measurements reduce flux loss
- Simplified installation
- Single power supply and data connection
- Integrated heating for cold weather operation

## Configuration 2: CSAT-3 + Li-7500

### Component A: CSAT-3 Sonic Anemometer

![CSAT-3](../../images/csat3.jpg){ align=right width="250" }

**Three-Dimensional Sonic Anemometer**

Measures wind velocity components and sonic temperature at high frequency.

**Key Specifications:**

- **Manufacturer**: Campbell Scientific
- **Measurement frequency**: 60 Hz (typical operation at 10 or 20 Hz)
- **Measured variables**:
    - 3-D wind components (Ux, Uy, Uz)
    - Sonic temperature (Ts)
- **Wind offset specification**:
    - Horizontal: < ±8.0 cm/s
    - Vertical: < ±4.0 cm/s

!!! note "Coordinate System"
    The CSAT-3 measures wind in its own coordinate system, which requires rotation to align with mean wind direction (coordinate rotation is part of standard EC processing).

### Component B: Li-7500 Open-Path Analyzer

![Li-7500](../../images/li7500.jpg){ align=right width="250" }

**Open-Path CO₂/H₂O Gas Analyzer**

Measures CO₂ and H₂O concentrations using infrared absorption.

**Key Specifications:**

- **Manufacturer**: LI-COR Biosciences
- **Measurement bandwidth**: 5, 10, or 20 Hz (software selectable)
- **Path length**: 12.5 cm
- **Precision (RMS)**:
    - CO₂: 0.2 mg/m³
    - H₂O: 0.004 g/m³

!!! warning "Open-Path Considerations"
    Open-path analyzers are affected by:

    - Rain and fog (contamination)
    - Temperature fluctuations (WPL corrections required)
    - Dust and debris accumulation

    Regular cleaning and maintenance are essential.