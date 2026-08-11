# Media

## Site Photographs

![Tower Setup](../../images/tower-overview.jpg){ width="600" }
*Figure 1: ON1 tower showing instrument placement*

<div class="grid" markdown>
![EC Sensor](../../images/ec-sensor.jpg){ width="300" }
*EC sensor configuration*

![TGA Analyzer](../../images/tga-system.jpg){ width="300" }
*TGA100A analyzer system*
</div>

## Data Flow Diagram

```mermaid
graph TD
    subgraph "Field Instruments"
        A[EC Sensors<br/>IRGASON/CSAT-3]
        B[TGA100A<br/>Gas Analyzer]
        C[Met Sensors]
    end

    subgraph "Data Processing"
        D[Data Logger]
        E[Quality Control]
        F[Flux Calculations]
    end

    subgraph "Output"
        G[Database]
        H[Analysis Tools]
    end

    A --> D
    B --> D
    C --> D
    D --> E
    E --> F
    F --> G
    G --> H

    style A fill:#bbdefb
    style B fill:#bbdefb
    style C fill:#bbdefb
    style G fill:#c8e6c9
```

## Video: Introduction to Flux Measurement

<div class="video-embed">
  <video width="100%" controls>
    <source src="../../videos/flux-intro.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>
<div class="video-placeholder">📹 Video: Basic principles of flux measurements (15 min) — available in the online documentation at the project site.</div>

*Video 1: Basic principles of flux measurements (15 minutes)*