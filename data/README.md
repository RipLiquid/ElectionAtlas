# Data

This folder contains the compact data package required by the QGIS project.

## Files

### `election_boundaries.gpkg`

GeoPackage containing:

- `us_states` — U.S. state polygons
- `michigan_counties` — Michigan county polygons

The boundaries originate from U.S. Census Bureau TIGER/Line data used in the original project.

### `2020_michigan_county_results.csv`

2020 presidential election results for Michigan counties.

### `2024_michigan_county_results.csv`

2024 presidential election results for Michigan counties.

### `2024_us_state_results.csv`

2024 presidential election results aggregated at the state level, with vote-share fields used by the national map.

### `2020_us_state_results.csv`

Supporting 2020 state-level results retained for comparison and future extension of the project.

## Election Result Source

County-level election data used in the original project came from Tony McGovern's public GitHub repository:

`tonmcg/US_County_Level_Election_Results_08-24`

The source repository notes that the dataset compiles results from multiple media/data sources and is not an authoritative primary election-results source. For research requiring official certification, results should be checked against state election authorities.

## Geographic Identifiers

County joins use five-digit FIPS codes. State identifiers are stored as two-digit FIPS strings so leading zeros are preserved.
