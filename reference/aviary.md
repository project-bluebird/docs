# Aviary

[![Build Status](https://travis-ci.com/project-bluebird/aviary.svg?branch=develop)](https://travis-ci.com/alan-turing-institute/aviary)

Aviary is an air traffic scenario generation package developed as part of the BlueBird project. It aims to make available a large number of simple (but non-trivial) air traffic control scenarios suitable for the training of an artificial agent via reinforcement learning. The package also includes a set of evaluation metrics for measuring performance in the air traffic control challenge.

Each aviary scenario consists of two parts:

1. An airspace sector definition. Three elemental sector types are supported:
   - I sector, representing a linear airway
   - X sector, representing a pair of intersecting linear airways
   - Y sector, representing a pair of merging airways.
   - C sector, customised sectors and waypoints corresponding to real-world ATC sectors

   Aviary scenarios take place in a sector of I, X, Y, or C type. 
   In addition to defining the airspace boundary, a sector includes a set of fixed waypoints and a corresponding set of routes through the sector, where a route is defined as a sequence of fix points.

   Sector definitions are serialised in GeoJSON format.

2. A sequence of aircraft whose routes pass through the sector. Each aircraft is defined by the following attributes:
```aircraft-attributes
   - callsign
   - aircraft type
   - initial position
   - arrival time relative to the scenario start time ("timedelta")
   - departure airport
   - destination airport
   - current flight level
   - cleared flight level
   - requested flight level
   - route (sequence of fix points crossing the sector)
```
   Aircraft definitions are serialised in JSON format.

## Installation

Install from the repository root directory:
```bash
pip install .
```

Developer install:
```bash
pip install -e .
```

## Usage

Aviary supports:
  - [Generation of I, X, Y, and C sector definitions](#sector-generation) in GeoJSON format
  - [Generation of aircraft definitions](#scenario-generation) in JSON format
  - [Translation](#scenario-translation) between aviary and [BlueSky](https://github.com/alan-turing-institute/bluesky) scenario formats
<!--  - Calculation of ATC performance metrics. -->

### Sector generation

Run the `sector_geojson.py` script passing the following command line arguments:
 - `sector_type` I, X or Y
 - `sector_name` Any string
 - `origin` Longitude/latitude coordinates separated by a comma
 - `lower_limit` Sector lower limit flight level
 - `upper_limit` Sector upper limit flight level
 - `filename_prefix` Output filename prefix (optional)
 - `output_path` Output file path (optional)

Example:
```
sector_geojson.py  --sector_type=X --sector_name="X-sector" --origin=-0.1275,51.5 --lower_limit=140 --upper_limit=400
```

![I, X, and Y sectors generated in Aviary](../images/aviary_ixy-sectors.png)



### Scenario generation

To generate a simple overflier-climber scenario, run the `overflier_climber.py` script, passing the following command line arguments:
 - `cruise_speed` A CSV file containing aircraft cruise speed by aircraft type and flight level
 - `cruise_speed_index` The name of the index column in the cruise speed CSV file
 - `climb time` A CSV file containing cumulative aircraft climb time by aircraft type and flight level
 - `climb_time_index` The name of the index column in the climb time CSV file
 - `downtrack_distance` A CSV file containing aircraft downtrack distance by aircraft type and flight level
 - `downtrack_distance_index` The name of the index column in the downtrack distance CSV file
 - `sector_type` I, X or Y (defaults to "I")
 - `aircraft_types` A comma-separated list of aircraft types to appear in the scenario
 - `flight_levels` A comma-separated list of flight levels to appear in the scenario
 - `thinking_time` A float, specifying the "thinking time" in seconds; this extends the scenario to make climbing ahead of the overflier a possibly optimal solution
 - `seed` A random seed
 - `filename_prefix` Output filename prefix (optional)
 - `output_path` Output file path (optional)

**Note:** to enable any user to generate overflier-climber scenarios, approximate CSV lookup tables for the aircraft cruise speed, climb time and downtrack distance are provided in the `aviary/resources` directory. Three aircraft types are included (A320, A343 and DH8D), each of which may be found in the BlueSky simulator's OpenAP aircraft performance model. These tables contain simple approximations, obtained by linear (in the case of cruise speed) and cubic spline (in the case of climb time and downtrack distance) interpolation, and should **not** be supposed to accurately represent aircraft performance at all levels. In particular, the climb time and downtrack distance approximations for the A320 & A343 aircraft types are **not** accurate above FL ~300.

Example:
```
overflier_climber.py --cruise_speed=cruise_speed.csv --cruise_speed_index=FL --climb_time=climb_time.csv --climb_time_index=fl_bins --downtrack_distance=downtrack_distances.csv --downtrack_distance_index=fl_bins --sector_type=I --aircraft_types=DH8D,A320,A343 --flight_levels=300,360,400 --thinking_time=60 --seed=22
```

### Scenario translation

[BlueSky](https://github.com/alan-turing-institute/bluesky) is an open source air traffic simulator. To convert an aviary scenario into the format expected by BlueSky, run the `parse_scenario.py` script passing the following command line arguments:
 - sector_geojson Full path to an aviary GeoJSON sector definition file
 - scenario_json Full path to an aviary JSON scenario file
 - `output_path` Output file path (optional)

Example:
```
parse-scenario.py --sector_geojson=I-sector.geojson --scenario_json=overflier-climber-22.json
```