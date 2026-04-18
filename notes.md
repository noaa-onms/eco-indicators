
## 2026-04-17

In `@copernicus.qmd`, add another section "## Show timeseries per sanctuary, without uncertainty" and create the associated figure with a suffix _without_uncertainty.png that removes from the plot the variables that end in name with _uncertainty

⏺ Added section "## Show timeseries per sanctuary, without uncertainty" with a
  plot_var_facets_without_uncertainty() function that filters out variables
  ending in _uncertainty and saves PNGs with the _without_uncertainty.png
  suffix, followed by a panel-tabset displaying them per sanctuary.

How can I retrieve a list of all the variables extracted with a description and units? Should be in copernicusmarine API

⏺ Each dataset description already carries variable metadata. Navigate into
  products > datasets > versions > parts > services > variables — each variable
   has short_name, standard_name, units, and sometimes
  long_name/bbox/coordinates.

  Minimal snippet that works with your existing get_dataset_description():

  ```r
  get_dataset_variables <- function(dataset_id) {
    services <- get_dataset_description(dataset_id) |>
      pluck("products", "datasets", 1, "versions", 1, "parts", 1, "services",
  1)
    i_ts <- which(services$service_name == "arco-time-series")
    pluck(services, "variables", i_ts) |>
      as_tibble() |>
      select(any_of(c("short_name", "standard_name", "units")))
  }

  map_dfr(names(datasets), \(id) get_dataset_variables(id) |> mutate(dataset =
  id, .before = 1))
  ```

  This gives you a tibble of dataset, short_name (e.g. thetao), standard_name
  (CF description, e.g. sea_water_potential_temperature), and units. If you
  want fuller prose, the product-level description field under products[[1]]
  has the human-readable abstract.

Add section `## Dataset Variables` after `## Setup dataset parameters` that produces a CSV of all variable information in a row, including dataset code and description, time periods, depths, etc. Output this as a DT::datatable().

⏺ Added ## Dataset Variables section that queries copernicusmarine$describe()
  per dataset, extracts product metadata (id, title), time range (via existing
   get_dataset_times()), plus per-variable short_name, standard_name, units,
  and depth/lon/lat ranges from the variable's coordinates list. Output is
  written to data/copernicus_variables.csv and shown via datatable() with
  horizontal scrolling.


