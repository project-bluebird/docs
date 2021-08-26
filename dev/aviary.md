# Aviary developer's guide

## Development

Scenario generation algorithms are implemented in aviary as [strategies](https://en.wikipedia.org/wiki/Strategy_pattern) in the context of the `ScenarioGenerator` class. The workflow for adding a new algorithms is:
 - Create a subclass of `ScenarioAlgorithm` and implement the `aircraft_generator` method. On each call, this method must yield a dictionary representing a new aircraft in the scenario, containing all of the [attributes listed above](#aircraft-attributes).
 - Optionally, add a python script (in the `scripts/` directory) to enable scenario generation from the command line. The existing script `overflier_climber.py` may be used as a template. Add the name of the script to the `scripts` option in `setup.py` (to make it callable from the project root directory).


## Tests

Run the tests from the project root with:
```bash
python -m pytest
```

or simply:
```bash
pytest
```