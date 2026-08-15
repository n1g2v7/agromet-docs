# About the Site

## Location and Setting

!!! info "Site Coordinates"
    - **Site Code**: ON1
    - **Location**: [To be added]
    - **Coordinates**: [Latitude, Longitude]
    - **Elevation**: [meters above sea level]
    - **Time Zone**: [Local time zone]

## Land Use and Vegetation

### Current Land Use
[Description of current agricultural or natural land use at the site]

### Vegetation Characteristics

| Parameter | Value/Description |
|-----------|------------------|
| Dominant species | [List main plant species] |
| Canopy height (hc) | [meters] |
| Leaf Area Index (LAI) | [m²/m²] |
| Growing season | [Months/dates] |
| Management | [Tillage, fertilization, irrigation] |

### Seasonal Variation

=== "Spring"
    - Crop emergence
    - Typical canopy height: [height]
    - LAI development stage

=== "Summer"
    - Peak growth period
    - Maximum canopy height: [height]
    - Maximum LAI: [value]

=== "Fall"
    - Harvest period
    - Senescence stage
    - Crop residue management

=== "Winter"
    - Bare soil or cover crop
    - Minimal vegetation
    - Potential snow cover

## Climate

### Annual Climate Summary

| Parameter | Value | Notes |
|-----------|-------|-------|
| Mean annual temperature | [°C] | |
| Mean annual precipitation | [mm] | |
| Growing degree days | [GDD] | Base 5°C |
| Frost-free period | [days] | |
| Prevailing wind direction | [direction] | |

### Climate Normals (1991-2020)

![Climate Graph](../../images/climate-normals.png)
*Figure: Monthly temperature and precipitation normals*

## Soil Characteristics

### Soil Type and Classification

- **Soil Order**: [Classification]
- **Texture**: [Clay/Loam/Sand percentages]
- **Drainage**: [Well/Moderately/Poorly drained]
- **pH**: [value]
- **Organic matter content**: [%]

### Soil Profile

| Horizon | Depth (cm) | Description |
|---------|-----------|-------------|
| A | 0-20 | [Description] |
| B | 20-60 | [Description] |
| C | 60+ | [Description] |

## Site Diagram

```mermaid
graph TB
    A[ON1 Site] --> B[Eddy Covariance System]
    A --> C[Flux-Gradient System]
    B --> D[IRGASON or CSAT-3+Li-7500]
    B --> E[High-frequency 10 Hz data]
    C --> F[TGA100A Analyzer]
    C --> G[Multi-height sampling]
    D --> H[30-min fluxes]
    F --> H
    E --> H
    G --> H
```

## Photo Gallery

<div class="grid cards" markdown>

-   ![Tower Overview](../../images/tower-overview.jpg)

    **Tower Overview**

    View from south showing instrument placement

-   ![EC Sensors](../../images/ec-sensors-closeup.jpg)

    **EC Sensors**

    IRGASON mounted at measurement height

-   ![TGA System](../../images/tga-interior.jpg)

    **TGA System**

    Interior showing TGA100A installation

-   ![Site Context](../../images/aerial-view.jpg)

    **Aerial View**

    Tower location within field

</div>