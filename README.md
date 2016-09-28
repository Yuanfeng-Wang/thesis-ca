# Contents
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Contents](#contents)
- [Project Abstract](#project-abstract)
- [Installation](#installation)
	- [Running the code](#running-the-code)
	- [System Variables](#system-variables)

<!-- /TOC -->

# Project Abstract
This project is part of the Author's requirements to fulfil as part of attaining an Honour's degree within Civil Engineering at the University of Sydney.

At the heart of the project is an implementation of the [Nagel-Schreckenberg (NS) model](https://en.wikipedia.org/wiki/Nagel%E2%80%93Schreckenberg_model) for vehicular traffic simulation, written in MATLAB. The Nagel-Schreckenberg model is a theoretical model - a simple Cellular Automata model for the simulation of freeway traffic. The model is able to reproduce phenomena such as traffic jams/congestion as a result of increased vehicle density and/or the slowing down of nearby vehicles. [TRANSIMS](https://en.wikipedia.org/wiki/Transims) - an integrated set of tools for conducting real-world regional transportation analyses, is based on the Nagel-Scheckenberg model.

Extending on the NS model, the information theoretic concept of [Transfer Entropy (TE)](https://en.wikipedia.org/wiki/Transfer_entropy) (Schreiber, 2000) is a relatively new method of considering information flows in complex systems.

The aim of this project is to ascertain whether the infomration theoretic application of Transfer Entropy can be used a predictor of traffic congestion within a simple implementation of the Nagel-Schreckenberg model.

# Installation
This project is written in MATLAB and is intended for use in tandem with the JIDT (Written by Joseph Lizier).

Steps:

1. Clone/download the `master` branch to a new folder of your choosing
2. Visit the JIDT [here](https://github.com/jlizier/jidt) and clone/download the `master` branch as well.
3. Your folder structure should look like this:
  ```
  ├── YourNewFolder
      ├── thesis-ca
      └── infodynamics-dist-1.3

  ```
4. You should be ready to rumbleeeee!

## Running the code
1. Open `ns_model.m` in MATLAB
2. View and edit any `Variable System Parameters` if required (see below section)

## System Variables
These variables control the parameters of the simulation such as:
- System size:
	- `n` - number of timesteps (rows)
	- `m` - length of roadway (columns)
- `v_max`: Maximum number of cells a vehicle can move in a timestep i.e. Maximum velocity. This is recommended to be set as a value from 1-5
- `initialisation_method`: Chooses a method of initialising all the vehicles at the beginning of a simulation instance, `random` mode is recommended as the other methods have not/will not been updated for large scale simulation use.
- `num_sims`: The number of simulations to be run (more simulations run, the better - 1,000+ recommended).
	- Note that the number of simulations specified in `num_sims` is effectively multiplied by 10.
	- This is as the main simulation runs 10 smaller simulations with system sizes starting at size `m/10` (`m` divided by 10) and increasing in increments of `m/10` until the system reachs size `m`.
- `plotGraph`: Plots three graphs:
	- Averaged Flow vs Density (Multiple sized systems)
	- Averaged TE vs Density (Multiple sized systems)
	- Averaged TE vs Density (Single system only)
- `calcTE`: Leave as `true` on to calculate Averaged Transfer Entropy
- `plotTE`: Leave as `false` to not get spammed on every loop if running multiple simulation instances.
