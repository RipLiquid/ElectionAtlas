# Methodology

## 1. Spatial Boundaries

The analysis uses U.S. state and county polygon boundaries in NAD 1983 (EPSG:4269). For the portfolio repository, the original shapefiles were consolidated into `election_boundaries.gpkg` with two layers:

- `us_states`
- `michigan_counties`

Only Michigan counties are packaged because the county-level analysis is limited to Michigan.

## 2. Election Tables

County-level 2020 and 2024 presidential results include county FIPS identifiers, candidate vote totals, total votes, and candidate vote shares. Michigan records were retained for the county-level portion of the project.

State-level 2024 results are used for the national map. Candidate vote shares were calculated from vote totals to maintain a one-record-per-state join.

## 3. Joins

### Michigan counties

The spatial join key is:

`GEOID` (county boundary) ↔ `county_fips` (election table)

Both fields are treated as five-character strings so leading zeros are preserved.

### U.S. states

The national map uses a unique state-level election record for each state. This avoids mixing county-level observations with state-level polygons.

## 4. Vote Margin

For each geographic unit:

`margin = Democratic vote share - Republican vote share`

- Negative margin: Republican advantage
- Positive margin: Democratic advantage
- Values near zero: closer two-party margin

## 5. 2020–2024 Change

For Michigan counties:

`margin change = 2024 margin - 2020 margin`

- Negative change: shift toward the Republican candidate relative to 2020
- Positive change: shift toward the Democratic candidate relative to 2020

This is a change in aggregate county vote margin, not evidence that the same individual voters changed their vote.

## 6. Cartographic Design

A diverging colour scheme is used because the mapped variables have a meaningful midpoint at zero. The national and county maps are designed to show direction and magnitude while retaining county/state boundaries for geographic context.

## 7. Portfolio Data Quality Cleanup

The repository version validates that each map uses election results at the same geographic unit as its boundaries:

- state results → state polygons
- county results → county polygons

The Michigan comparison also maps the actual difference between 2024 and 2020 margins rather than using the 2020 margin alone as a proxy for change.
