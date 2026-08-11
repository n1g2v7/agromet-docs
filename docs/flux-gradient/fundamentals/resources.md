# Resources

## Further Reading

!!! info "Key References"
    1. **Businger et al. (1971)**. Flux-profile relationships in the atmospheric surface layer.
       *Journal of Atmospheric Sciences*, 28, 181–189. — *Stability functions used in the pipeline.*

    2. **Brown, S.E., Wagner-Riddle, C., & Conrad, B. (2024)**. Low-power flux gradient measurements
       for quantifying the impact of agricultural management on nitrous oxide emissions.
       *Agricultural and Forest Meteorology*, 353, 110027. — *CWR Lab FG system design and validation.*

    3. **Melman, E.A., et al. (2024)**. Increasing complexity in Aerodynamic Gradient flux calculations
       inside the roughness sublayer applied on a two-year dataset.
       *Agricultural and Forest Meteorology*, 355, 110107. — *FG method in the roughness sublayer.*

    4. **Wagner-Riddle, C., et al. (2017)**. Globally important nitrous oxide emissions from croplands
       induced by freeze–thaw cycles. *Nature Geoscience*, 10(4), 279–283. — *N₂O application.*

    5. **Foken, T. (2006)**. 50 years of the Monin-Obukhov similarity theory.
       *Boundary-Layer Meteorology*, 119, 431–447.

## Next Steps

- [TGA System](../tga-system/overview-and-cycle.md) — TGA100A operation and diagnostic variables
- [Processing Pipeline](../processing-pipeline.md) — MATLAB script workflow
- [Site Initialization](../site-initialization.md) — Configuring a new site

<!-- FIX LINKS -->

!!! question "Quick Check"
    **Why does the pipeline set K = NaN for ζ > 2 rather than using the stable formula?**

    !!! success "Answer"
        Under very stable conditions (ζ > 2), MOST breaks down: turbulence becomes
        intermittent, the logarithmic profile assumption fails, and the Businger-Dyer
        stability functions are no longer reliable. Using the extrapolated formula would
        produce physically unrealistic diffusivities. Setting K = NaN explicitly excludes
        these periods rather than propagating a large systematic error into the flux record.