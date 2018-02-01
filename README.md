This repository contains data used in [The Atlas Of Redistricting](https://projects.fivethirtyeight.com/redistricting-maps/). [Read more](https://fivethirtyeight.com/features/we-drew-2568-congressional-districts-by-hand-heres-how) about the project.

### [shp/](shp)
This directory contains shapefiles for all the maps used in the project. The shapefiles for current districts are those used in the 115th Congress, and are based on [Cartographic Boundary Shapefiles](https://www.census.gov/geo/maps-data/data/cbf/cbf_cds.html) from the Census Bureau, with some adjustments for water features. In cases where the current congressional map fulfilled the goals of a custom map for a state, a shapefile is not included. (See the `current_map` column of `districts.csv` for maps where this is the case.)

### [drf/](drf)
This directory contains XML files (with a `.drf` extension) for use in [Dave's Redistricting App](http://gardow.com/davebradlee/redistricting/launchapp.html), which was used to draw the custom districts for this project. In cases where the current congressional map fulfilled the goals of a custom map, a DRF file is not included. (See the `current_map` column of `districts.csv` for maps where this is the case.)

### [districts.csv](districts.csv)

Header | Definition
--- | ----------
statefp | State FIPS code
state | State postal abbreviation
maptype | Map type
district | District number (00 for at-large districts)
population | The district's 2010 population
population_18_over | The district's 2010 voting-age (18+) population
PVI | The district's Cook Partisan Voting Index
dem_chance | The probability of the district electing a Democrat. This is not a prediction for a specific election, but rather reflects the expected performance over the long run, across a variety of political conditions
Non-Hispanic White | The percentage of the district's 2010 voting-age (18+) population reported as "Not Hispanic or Latino: - Population of one race: - White alone" by the Census
African-American | The percentage of the district's 2010 voting-age (18+) population reported as "Not Hispanic or Latino: - Population of one race: - Black or African American alone" by the Census
Hispanic/Latino | The percentage of the district's 2010 voting-age (18+) population reported as "Hispanic or Latino"
Asian | The percentage of the district's 2010 voting-age (18+) population reported as "Not Hispanic or Latino: - Population of one race: - Asian alone" by the Census
Native American | The percentage of the district's 2010 voting-age (18+) population reported as "Not Hispanic or Latino: - Population of one race: - American Indian and Alaska Native alone" by the Census
Pacific Islander | The percentage the district's 2010 voting-age (18+) population reported as "Not Hispanic or Latino: - Population of one race: - Native Hawaiian and Other Pacific Islander alone" by the Census.
Other | The percentage of the district's 2010 voting-age (18+) population reported as a member of another race by the Census.
race_category | The district's race category, for the purposes of determining minority-majority districts. The value is either "Non-Hispanic White Majority" or "Maj-Min", with the majority racial category in parentheses. "Maj-Min (Coalition)" means a coalition of different minority groups make up the majority.
minority_chance | The probability of the district electing a minority representative, based on the racial composition of each district and its Cook PVI.
current_map | Whether the current map was used instead of drawing a new map.
impossible | Whether drawing this map was impossible. If so, the closest possible map was drawn.

### [states.csv](states.csv)

Header | Definition
--- | ----------
statefp | State FIPS code
state | State postal abbreviation
maptype | Map type
districts | The number of districts in the state
county_splits | The number of times counties are split on this map
efficiency_gap | The map's [efficiency gap](https://chicagounbound.uchicago.edu/cgi/viewcontent.cgi?article=1946&context=public_law_and_legal_theory), based on an average of 2012 and 2016 presidential results
efficiency_gap_extra_seats | The number of "extra seats" a party would get from this map based on the efficiency gap
district_perimeters | The sum of the perimeters of the map's districts
state_perimeter | The state's perimeter
interior_perimeter_measure | The interior perimeter of the map's districts (`district_perimeters-state_perimeter / 2`)
compactness_rank | The map's compactness rank, based on the districts' interior perimeters.

### [county_assignments.csv](county_assignments.csv)

Header | Definition
--- | ----------
statefp | State FIPS code
state | State postal abbreviation
maptype | Map type
countyfp | County FIPS code
county | County name
cd | Congressional district

## Sources
The boundaries of the `algorithmic-compact` districts are based on Census block lists created by [Brian Olson](http://bdistricting.com/2010/).

The boundaries of the `current` districts are based on [Cartographic Boundary Shapefiles](https://www.census.gov/geo/maps-data/data/cbf/cbf_cds.html) from the Census Bureau, with some adjustments for water features.

Demographic data is from the 2010 [Census](https://www.census.gov/).

## License

This data is licensed under the [Creative Commons Attribution-ShareAlike 3.0 Unported License](https://creativecommons.org/licenses/by-sa/3.0/).
