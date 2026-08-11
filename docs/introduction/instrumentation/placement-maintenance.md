# Sensor Placement & Maintenance

## Sensor Placement and Geometry

```mermaid
graph TB
    subgraph "Tower Configuration"
        A[Top Level<br/>EC Sensors<br/>Height: z_m]
        B[Upper FG Intake<br/>Height: z_2]
        C[Lower FG Intake<br/>Height: z_1]
        D[Ground Level<br/>z = 0]
    end

    A -.-> B
    B -.-> C
    C -.-> D

    style A fill:#e3f2fd
    style B fill:#fff9c4
    style C fill:#fff9c4
    style D fill:#e8f5e9
```

### Typical Heights (Site-Specific)

!!! example "Example Configuration"
    | Level | Height (m) | Measurement |
    |-------|-----------|-------------|
    | EC sensors | 3.0 | Direct fluxes |
    | FG upper intake | 2.5 | Concentration C₂ |
    | FG lower intake | 0.5 | Concentration C₁ |
    | Canopy height | 0.3 | Reference level |

## Maintenance Schedule

### Daily Checks
- [ ] TGA sample pressure and flow
- [ ] EC data quality flags
- [ ] Visual inspection of sensors
- [ ] Check data logger connection

### Weekly Checks
- [ ] Clean EC sensor windows
- [ ] Check TGA LN₂ level
- [ ] Inspect sampling lines for leaks
- [ ] Review data quality metrics

### Monthly Checks
- [ ] Full system calibration
- [ ] Replace inlet filters
- [ ] Check all electrical connections
- [ ] Backup data and logs

### Quarterly Maintenance
- [ ] Professional calibration service
- [ ] Replace consumables
- [ ] Detailed performance review
- [ ] Update site documentation