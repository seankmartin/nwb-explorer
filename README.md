[![Build Status](https://travis-ci.org/MetaCell/nwb-explorer.svg?branch=development)](https://travis-ci.org/MetaCell/nwb-explorer)
[![codecov](https://codecov.io/gh/MetaCell/nwb-explorer/branch/development/graph/badge.svg)](https://codecov.io/gh/MetaCell/nwb-explorer)
[![Twitter Follow](https://img.shields.io/twitter/follow/metacell.svg?label=follow&style=social)](https://twitter.com/metacell)

# NWB Explorer

NWB Explorer is a web application that can be used by scientists to read, visualize and explore
the content of NWB files.

Learn more about the [Neurodata Without Borders](https://www.nwb.org/).

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Below you will find the software you need to install to use nwb explorer (and the versions we used):

* Git (2.17.0).
* Node (9.11.1) and npm (6.0.0).
* Python 3 (3.6+), pip (10.0.1)

#### Python Dependencies

We recommend the use of a new python 3 virtual environment:

```bash
python3 -m venv nwb-explorer
source nwb-explorer/bin/activate
```

Or, with conda

```bash
conda create -n nwb-explorer python=3.7
conda activate nwb-explorer
```

### Local installation

Instructions to get a development environment running.

```bash
git clone -b development https://github.com/MetaCell/nwb-explorer
cd nwb-explorer/utilities
python install.py
```

## How to run NWB Explorer

After the installation is complete, run the script:

```bash
cd nwb-explorer
./NWBE
```

If everything worked, the default browser will open on `http://localhost:8888/geppetto`

### Run with docker

Under k8s folder we can find the dockerfile required to build a container for NWB-Explorer:

```bash
cd nwb-explorer/k8s
docker build -t nwb-explorer .
docker run -it -p8888:8888 nwb-explorer
```

## How to use NWB Explorer

When the application is started, no file will be loaded.

1. Use the interface to load the file from a public url or just load a sample
1. Specify the parameter nwbfile in your browser. Example: `http://localhost:8888/geppetto?nwbfile=https://github.com/OpenSourceBrain/NWBShowcase/raw/master/NWB/time_series_data.nwb`

After the file is loaded, a Jupyter notebook will be available.
From the notebook the current loaded file can be accessed through the variable `nwbfile`.
For further information about the Python API, see the [PyNWB docs](https://pynwb.readthedocs.io/en/stable/)

## How to develop

The application is built as a Jupyter extenesion via [Geppetto Jupyter].(https://github.com/openworm/org.geppetto.frontend.jupyter).
The application pages, the web resources and apis are served by Tornado handlers.

### Python code

In order to have all the Python files redeployed, the application and the dependencies must be installed in development mode, i.e. with the command

```bash
pip install -e .
```

### Javascript code

To check if a dependency is installed in development mode, run `pip list`.

JS/HTML code can be found inside `static/org.geppetto.frontend/src/main/webapp/`. The code needs to be rebuilt with webpack everytime there is a change. The recommended way is to do so using the Webpack development serverer running in `/static/org.geppetto.frontend/src/main/webapp/` this command:

```bash
npm run build-dev-noTest:watch
```

## Built With

* [Geppetto](http://www.geppetto.org/) - Used to build a web-based application to interpret and visualize the NWB:2 files.
* [PyNWB](https://github.com/NeurodataWithoutBorders/pynwb) - Used to read and manipulate NWB:2 files
* [Jupyter notebook](https://jupyter.org/) - Jupyter notebook is used as a backend.


## Background

The NWB Explorer was initially created by MetaCell to showcase the features of the Geppetto platform to share
neurophysiological data in Neurodata Without Borders format. It was further developed as part of a
Google Summer of Code project with the OpenWorm project. It is currently being extended as part of the Open Source Brain
project to provide both a standalone and online application for visualising and analysing the contents of NWB files.
This work is currently funded by the Wellcome Trust.

## Authors

* Matteo Cantarelli ([MetaCell](http://metacell.us))
* Giovanni Idili ([MetaCell](http://metacell.us))
* Filippo Ledda ([MetaCell](http://metacell.us))
* Rodriguez Facundo ([MetaCell](http://metacell.us))

See also the list of [contributors](https://github.com/Metacell/nwb-explorer/contributors) who participated in this project.
