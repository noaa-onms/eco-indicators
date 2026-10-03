# Event catalog

`events_catalog.csv` lists documented environmental events for the 13 analyzed National Marine Sanctuaries,
2003-01 to 2025-09, one row per sanctuary and event. It is used by `trajectories.qmd` to ask whether each
sanctuary's monthly environmental trajectory registers events that were documented independently.

| column | meaning |
|---|---|
| `event_id` | `<NMS>_<YYYY-MM>_<type>` |
| `nms`, `name`, `type` | sanctuary code; short name; one of heatwave, cold, enso, storm, freshwater, hypoxia, upwelling, hab, other |
| `date_start`, `date_end` | documented window (month precision; "dates approximate" in `impacts` when the sources give no months) |
| `vars_expected` | state variables expected to respond and their direction, e.g. `sst+;sbt+;chl-` |
| `scale` | "regional, multi-month", "regional, short" or "local or short" |
| `resolvable` | decided before any result was looked at: TRUE only if the event lasted two months or more, acted at or beyond the scale of the sanctuary, and should move at least one sanctuary-mean monthly state variable; otherwise FALSE (these are the negative controls) |
| `impacts`, `response` | documented ecological or human impact; documented management response, if any |
| `source`, `url` | short citation(s) and DOI or report URL(s) |

Compiled on 2026-10-03 from literature notes with AI assistance (Claude). Dates, impacts and sources should be
checked against the cited works before publication.
