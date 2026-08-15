# Quality & Comparison

## Quality Thresholds

The MATLAB pipeline applies a hierarchical QC scheme:

1. **Instrument diagnostics** — CSAT diagnostic flags, TGA detector stability
2. **Data completeness** — half-hours with > 50 % NaN values are rejected
3. **Stability range** — ζ > 2 or ζ < −5 → K = NaN
4. **Site-specific filters** — TGA pressure range, detector stability thresholds
5. **Meteorological conditions** — fetch, wind direction sectors (site-specific)
6. **Manual QC** — CSV-based filter files for known instrument problems

Additional TGA-specific thresholds:

| Parameter | Threshold | Action |
|-----------|-----------|--------|
| Sample pressure | 30–40 kPa (300–400 mb) range check | Flag / reject |
| ΔSample pressure between intakes | > 0.075 kPa | Flag for review |
| Outliers per half-hour | > 100 outlier samples | Reject half-hour |
| Zero or negative concentrations | Any | Convert to NaN |

## Advantages and Limitations

### Advantages ✓

- **Compact footprint** — spatial averaging over shorter distances than EC
- **Multi-plot capability** — single TGA cycles through 4 plots simultaneously
- **Suitable for N₂O** — effective for low-flux gases where EC faces signal-to-noise challenges
- **Lower instrument requirements** — no ultra-fast response sensors needed

### Limitations ✗

- **MOST assumptions required** — horizontal homogeneity, steady-state, surface layer
- **Stability dependent** — accuracy decreases for ζ > 2 or ζ < −5
- **Requires ancillary data** — $u_*$, $L$ from sonic anemometer
- **Semi-empirical** — introduces additional uncertainty (~20–40 %)

### Comparison with EC

| Aspect | Flux-Gradient | Eddy Covariance |
|--------|--------------|-----------------|
| Measurement | Concentrations at 2+ heights | High-freq covariances |
| Minimum frequency | 1–10 Hz | 10–20 Hz |
| Theory base | MOST (semi-empirical) | Direct (fewer assumptions) |
| Footprint | Compact, height-dependent | Larger, stability-dependent |
| Stability range | Neutral–moderately unstable | All conditions |
| Multi-plot | Yes (TGA cycle) | No (single footprint) |
| Uncertainty | 20–40 % | 10–20 % |