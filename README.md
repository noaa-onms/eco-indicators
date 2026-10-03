# eco-indicators
multivariate ordination for ecological indicators across the Sanctuaries

Results so far:

- [copernicus](https://noaa-onms.github.io/eco-indicators/copernicus.html)
- [erddap](https://noaa-onms.github.io/eco-indicators/erddap.html)
- [trajectory_checks](https://noaa-onms.github.io/eco-indicators/trajectory_checks.html): pilot stress tests of the AEM–RDA regime workflow (replication, sign invariance, no-shift surrogates, known events, full-series alternative)
- environmental trajectories of 14 sanctuaries, 2003–2025 (branch `trajectory-checks`; the links go live once it is merged to `main`). Notebooks run in this order, each reading the CSVs written by the ones before it:
  - [state](https://noaa-onms.github.io/eco-indicators/state.html): monthly state variables per sanctuary (GLORYS12 temperature, salinity and mixed-layer depth; GlobColour chlorophyll; IMERG precipitation), with shelf and optically-deep masks → `data/state/`
  - [events](https://noaa-onms.github.io/eco-indicators/events.html): catalog of documented events, marine heatwave and cold-spell days (OSTIA), degree heating weeks, tropical cyclones → `data/events/`
  - [context](https://noaa-onms.github.io/eco-indicators/context.html): climate indices (ONI, PDO, NPGO, NAO, AMO), OC-CCI chlorophyll for comparison, condition report ratings → `data/context/`
  - [trajectories](https://noaa-onms.github.io/eco-indicators/trajectories.html): departure from the 2003–2012 baseline envelope with a stationary null model, status/trend/form, event correspondence, time scales (AEM–RDA), climate modes, sensitivity → `data/trajectories/`
  - [manuscript_figures](https://noaa-onms.github.io/eco-indicators/manuscript_figures.html): figures 1–7 of the draft manuscript → `figures/manuscript/`
