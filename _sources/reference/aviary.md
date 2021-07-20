# Aviary

[![Build Status](https://travis-ci.com/project-bluebird/aviary.svg?branch=develop)](https://travis-ci.com/alan-turing-institute/aviary)

Aviary is an air traffic scenario generation package developed as part of the [Simurgh](https://github.com/alan-turing-institute/simurgh) project. It aims to make available a large number of simple (but non-trivial) air traffic control scenarios suitable for the training of an artificial agent via reinforcement learning. The package also includes a set of evaluation metrics for measuring performance in the air traffic control challenge.

Each aviary scenario consists of two parts:

1. An airspace sector definition. Three elemental sector types are supported:
   - I sector, representing a linear airway
   - X sector, representing a pair of intersecting linear airways
   - Y sector, representing a pair of merging airways.