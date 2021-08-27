# Project BlueBird Documentation

This is the documentation site for Project BlueBird, a prosperity partnership between The Alan Turing Institute and NATS, supported by EPSRC.

The research vision for this project is to deliver the world’s first artificial intelligence (AI) system to control a section of airspace in live trials using digital twinning and machine learning technologies, and tools and methods that promote safe and trustworthy use of AI.

This documentation site will guide users through the use of simulators and the BlueBird API used in this project. It will also discuss air traffic control simulation and scenario generation and evaluation. 

:::{note}
The codebase is under heavy development.
:::

## About 
The workflow is outlined in the image below. 

![Dependency flow using BlueBird](/images/bluebird_dependency_flow.png)

The project uses - [Bluebird](https://github.com/alan-turing-institute/bluebird) - a Flask-based API that handles communication with multiple air traffic simulators (it currently supports the open source [BlueSky](https://github.com/alan-turing-institute/bluesky) simulator and will potentially support the physics-based [Phoenix](https://github.com/project-bluebird/phoenix) simulator at a later date.

[Twitcher](https://github.com/project-bluebird/twitcher) is a front-end for BlueBird to allow monitoring and communication during simulations. The simulation can also be monitored and modified via the [Dodo](https://github.com/alan-turing-institute/dodo) scaffold which provides commands for communicating with BlueBird in Python (PyDodo) and R (rdodo).

## License

## Citing Project BlueBird

## Get in touch

BlueBird has a [twitter](https://twitter.com/bluebirdai) account. More information on the project can be found on the [Turing website](https://www.turing.ac.uk/research/research-projects/project-bluebird-ai-system-air-traffic-control).  
