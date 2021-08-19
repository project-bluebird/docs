# About
Here we have some information about the different packages and scaffolds used in the project, information on running them can be found in the [install](install.md) section

## BlueBird
![Python Version](https://img.shields.io/badge/python-3.7-blue)
![License](https://img.shields.io/github/license/project-bluebird/bluebird)
![Code Style](https://img.shields.io/badge/code%20style-black-000000.svg)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)

[BlueBird](../reference/bluebird-server.md) provides a common [Flask](https://github.com/pallets/flask)-based API to multiple air traffic simulators. In addition to basic communication, it also includes features such as state caching, performance metrics (via [Aviary](https://github.com/project-bluebird/aviary)), and logging of scenario data. The main purpose of BlueBird is to provide a common interface to ease the research & development of AI for air traffic control.


## BlueSky
[BlueSky](https://github.com/project-bluebird/bluesky) is the currently supported open-source simulator.


## Aviary
[![Build Status](https://travis-ci.com/project-bluebird/aviary.svg?branch=develop)](https://travis-ci.com/alan-turing-institute/aviary)

[Aviary](../reference/aviary.md) is an air traffic scenario generation package developed as part of the BlueBird project. It aims to make available a large number of simple (but non-trivial) air traffic control scenarios suitable for the training of an artificial agent via reinforcement learning. The package also includes a set of evaluation metrics for measuring performance in the air traffic control challenge.