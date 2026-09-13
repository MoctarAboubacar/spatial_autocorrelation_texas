# Local Indicators of Spatial Autocorrelation — Harris County, Texas

A worked analysis of spatial autocorrelation in residency by race across census tracts in Harris County, Texas, using American Community Survey five-year estimates.

Standard regression assumes errors are independent and identically distributed. Where observations are spatially related, that assumption fails and inference drawn from it is unreliable. The first step is to test whether spatial dependence is present at all, using Moran's I as a global statistic.

But a global statistic collapses the whole map to one number. It tells you clustering exists without telling you where. Local indicators of spatial autocorrelation (LISA) decompose Moran's I into tract-level contributions, identifying specific clusters of high-high and low-low similarity and the outliers that sit against their neighbours. Harris County contains Houston and has a documented history of discriminatory housing policy including redlining, so it is a case where the local statistics locate residential clustering that the global figure only summarises.

I treat ACS estimates as point values here, setting aside the pooled survey design and associated error measures. Tract-level ACS estimates carry non-trivial margins of error, so that simplification is worth noting.

Rendered write-up: [moctaraboubacar.github.io/spatial_autocorrelation_texas](https://moctaraboubacar.github.io/spatial_autocorrelation_texas/)

## Methods

Global Moran's I, local indicators of spatial autocorrelation (LISA), spatial weights matrix construction, `spdep`, ACS data access via `tidycensus`.

## Files

| File | Purpose |
|---|---|
| `Spatial Autocorrelation 1.Rmd` | Full analysis with narrative |
| `index.html` | Rendered output |

## Data

Data are pulled directly from the Census API at run time, so nothing needs to be downloaded manually. A free API key is required.

Request a key at [api.census.gov/data/key_signup.html](https://api.census.gov/data/key_signup.html), then create a `.Renviron` file in the repository root containing:

```
CENSUS_API_KEY=your_key_here
```

The key is read from the environment and is not stored in the code. `.Renviron` is git-ignored.

## Reproducing

```r
install.packages(c("tidyverse", "tidycensus", "spdep", "sf", "RColorBrewer", "here"))

rmarkdown::render("Spatial Autocorrelation 1.Rmd")
```

## License

MIT — see [LICENSE](LICENSE).
