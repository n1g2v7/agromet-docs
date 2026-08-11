# Using This Glossary

!!! info "Usage Notes"
    - All variables computed at 30-minute intervals
    - Typical ranges are site-specific
    - Establish baselines during commissioning
    - Cross-reference with instrument manuals

## Quick Navigation

- [Flux-Gradient Variables](flux-gradient-variables.md)
    - TGA Pressures, TGA Flows, Gas Concentrations
- [Eddy Covariance Variables](eddy-covariance-variables.md)
    - Wind Components, Turbulent Fluxes, Turbulent Statistics
- [Shared Variables](shared-variables.md)
    - Temperature, Humidity, Radiation

## For New Users

1. **Start with basics**: Understand main flux variables first
2. **Learn QA/QC**: Focus on quality control parameters
3. **Cross-reference**: Use with method chapters for context

## For Data Analysis

1. **Variable selection**: Choose appropriate variables for analysis
2. **Units**: Verify unit consistency
3. **Quality flags**: Apply appropriate filtering
4. **Typical ranges**: Use to identify outliers

## For Troubleshooting

1. **Check diagnostics**: Start with pressure/flow variables
2. **Compare typical ranges**: Identify deviations
3. **Time series analysis**: Look for trends
4. **Cross-validation**: Compare FG and EC when available

## Measurement Schedule

| Variable Type | Measurement Frequency | Output Interval |
|--------------|---------------------|-----------------|
| TGA diagnostics | 10 Hz | 30 minutes |
| EC raw data | 10 Hz | Stored as 10 Hz |
| EC fluxes | Computed from 10 Hz | 30 minutes |
| Meteorology | 1 Hz or slower | 30 minutes |

## References

For complete details on variables and measurement principles:

- **Introduction**: [FG vs. EC](../introduction/overview/data-and-methods.md)
- **EC Variables**: [EC Theory](../eddy-covariance/theory.md)
- **FG Variables**: [FG Theory](../flux-gradient/fundamentals/theory.md)
- **TGA System**: [TGA System Details](../flux-gradient/tga-system/overview-and-cycle.md)
- **References**: [Scientific Literature](../references/literature-theses.md)

---

*This glossary is based on the ON1 Variables Glossary Documentation (Version 1.0, December 2025)*