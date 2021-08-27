# About
Here we have some information about the different packages and scaffolds used in the project, information on running them can be found in the [install](install.md) section


## BlueSky
[BlueSky](https://github.com/project-bluebird/bluesky) is the currently supported open-source simulator. BlueSky is meant as a tool to perform research on Air Traffic Management and Air Traffic Flows. 
Citation info: J. M. Hoekstra and J. Ellerbroek, [BlueSky ATC Simulator Project: an Open Data and Open Source Approach](https://www.researchgate.net/publication/304490055_BlueSky_ATC_Simulator_Project_an_Open_Data_and_Open_Source_Approach), Proceedings of the seventh International Conference for Research on Air Transport (ICRAT), 2016. 

## BlueBird
![Python Version](https://img.shields.io/badge/python-3.7-blue)
![License](https://img.shields.io/github/license/project-bluebird/bluebird)
![Code Style](https://img.shields.io/badge/code%20style-black-000000.svg)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)

[BlueBird](../reference/bluebird-server.md) provides a common [Flask](https://github.com/pallets/flask)-based API to multiple air traffic simulators. In addition to basic communication, it also includes features such as state caching, performance metrics (via [Aviary](https://github.com/project-bluebird/aviary)), and logging of scenario data. The main purpose of BlueBird is to provide a common interface to ease the research & development of AI for air traffic control.

## Twitcher
[Twitcher](https://github.com/project-bluebird/twitcher) is a front-end for BlueBird for monitoring the simulation via a browser. Twitcher is built using .NET Core and Fable, then compiled to Javascript.

## Aviary
[![Build Status](https://travis-ci.com/project-bluebird/aviary.svg?branch=develop)](https://travis-ci.com/alan-turing-institute/aviary)

[Aviary](../reference/aviary.md) is an air traffic scenario generation package developed as part of the BlueBird project. It aims to provide a platform for agent training, by synthetically generating air traffic control scenarios and providing a set of evaluationmetrics for measuring performance.