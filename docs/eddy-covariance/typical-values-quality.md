# Typical Values & Data Quality

## Typical Values

### Daily Cycle Example

| Time | CO₂ Flux<br/>(μmol/m²/s) | H<br/>(W/m²) | LE<br/>(W/m²) | u*<br/>(m/s) |
|------|----------------------|------------|-------------|------------|
| 06:00 | +2 | -20 | 50 | 0.15 |
| 12:00 | -15 | 250 | 300 | 0.45 |
| 18:00 | +5 | 80 | 150 | 0.30 |
| 24:00 | +8 | -30 | 20 | 0.12 |

!!! note "Sign Conventions"
    - **Negative flux**: Downward (into surface)
    - **Positive flux**: Upward (from surface)

    For CO₂: Negative = ecosystem uptake (photosynthesis)

## Data Quality Considerations

### High-Quality Data Requires:

✓ **Sufficient turbulence**: $u_* > 0.1$ m/s (threshold varies by site)
✓ **Stationarity**: Flux covariance quality test
✓ **Horizontal homogeneity**: Footprint within target area
✓ **Proper sensor function**: No spikes, offsets, or drift
✓ **Complete data**: < 10% missing high-frequency data

### Common Issues

=== "Insufficient Turbulence"
    **Problem**: Stable atmospheric conditions (nighttime)
    **Solution**: Use $u_*$ threshold filtering

=== "Sensor Malfunction"
    **Problem**: Dirty optics, calibration drift
    **Solution**: Regular maintenance and calibration

=== "Rain Events"
    **Problem**: Water on sensor windows
    **Solution**: Automated detection and flagging