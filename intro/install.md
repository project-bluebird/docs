# Installation Instructions
With an air traffic control (ATC) simulator (e.g., BlueSky) and BlueBird running, one can observe and interact with the simulation via BlueBird using Python (PyDodo), R (rdodo) or Twitcher. The Aviary package allows one to synthetically generate ATC scenarios of increasing complexity to train agents on and provides metrics to score performance.

## Quick Start Using Simurgh
### 1. Clone the Simurgh repository


```{bash}
git clone https://github.com/alan-turing-institute/simurgh.git
```

All commands described in the subsequent sections are meant to be run from inside the repo. After cloning the repo make sure to:

```{bash}
cd simurgh
```

### 2. Run BlueBird, BlueSky & Twicher with Docker

Make sure you have [Docker](https://www.docker.com/get-started) installed.

If you have Docker installed and have cloned this repo then run:

```{bash}
docker-compose up -d
```

This pulls down the pre-built images from DockerHub and
starts each container in the right order.

Then all one needs to do is go to
`http://localhost:8080` where Twitcher will be running.

_Note_: If this is the first time running this command, it may take some time to
download and extract all the layers involved.

Then to close this, run:

```
docker-compose down
```

This will shutdown the running instances.

### 3. Install PyDodo

PyDodo is the Python implementation of Dodo.

To install:

```bash
git clone https://github.com/alan-turing-institute/dodo.git
pip install dodo/Pydodo
```

If BlueSky and BlueBird are running (see previous step), then one can communicate with the simulator (via
BlueBird) using PyDodo:

```python
>>> import pydodo
>>>
>>> pydodo.reset_simulation()
True
>>>
```

Success!

See the Dodo [specification document](https://github.com/alan-turing-institute/dodo/blob/master/Specification.md) for a detailed overview of the supported commands.

### 4. Example usage

The [example notebook TODO_LINK]() shows how to interact with the simulation using PyDodo.

To run the example, launch the notebook using the command below (this will automatically open the notebook in your browser):

 ```{bash}
 jupyter lab <path-to-example>.ipynb
 ```

 ## Running from Source

 ### BlueBird and BlueSky
To run Bluebird with BlueSky from source, first clone both repos.

```bash
git clone https://github.com/project-bluebird/bluesky.git
git clone https://github.com/project-bluebird/bluebird.git
```

Open two terminals. In the first one, install and run BlueSky:

```bash
# Install Bluesky
cd bluesky
./install.sh --headless

# Run Bluesky
source venv/bin/activate
python BlueSky.py --headless
```

In your second terminal, install and run Bluebird:

```bash
# Install Bluebird
cd bluebird
./install.sh

# Run Bluebird, connected to Bluesky
source venv/bin/activate
python ./run.py
```

Bluebird should now be up and running, and listening for API requests on http://0.0.0.0:5001/.


If you are using a version of Aviary that isn't the on the develop branch, then edit the `requirements.txt` file in bluebird to point to the appropriate branch, or compile a version locally in the aviary repository root directory via

```bash
pip install .
```

Developer install:
```bash
pip install -e .
```

To verify the simulator is working, navigate to http://0.0.0.0:5001/api/v2/siminfo. This simple GET request returns a JSON Object containing information about the running simulator (BlueSky). You can then try out the other [API endpoints](#api-endpoints).

Note that BlueBird can be run with the following options:

```bash
python ./run.py [--sim-host=<address>] [--sim-mode=<mode>] [--reset-sim] [--log-rate=<rate>]
```

- the `--dev` option will also install dependencies needed for developing BlueBird
- If you need to connect to BlueSky on another host (i.e. on a VM), you may pass the `--sim-host` option to run.py.
- If passed, `--reset-sim` will reset the simulation on connection
- If passed, `--sim-mode` will start the simulation in a specific [mode](docs/SimulatorModes.md).

### Twitcher

Twitcher is used to visualise the progress of sectors and scenarios, including custom sectors defined in Aviary. 
The recommended way to run Twitcher is via a docker container. Simply clone the [repository](https://github.com/project-bluebird/twitcher) and run

```
docker-compose up --build
```

Then go to [http://localhost:8080/](http://localhost:8080/) in your browser.

Twitcher assumes that BlueSky and BlueBird are already running on the same machine.

