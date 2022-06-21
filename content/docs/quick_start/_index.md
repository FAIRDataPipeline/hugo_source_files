---
weight: 1
title: "Quick Start"
bookCollapseSection: false
---

The FAIR Data Pipeline needs three components to be installed on your computer in order to run. These are:

- Command Line Interface (CLI)
- Data Registry
- A Modelling API (in whatever programming language you want to use)

## Install the Command Line Interface and Data Registry

The best way to install the Data Registry is via the CLI.

### Prerequisites

The CLI needs to be installed using `pip` (the package installer for Python), which means you will need a Python distribution installed on your computer. You will also need to [install Graphviz](https://graphviz.org/).

### Installation

[Instructions to install the CLI](https://github.com/FAIRDataPipeline/FAIR-CLI#installation) are in the [CLI GitHub repository](https://github.com/FAIRDataPipeline/FAIR-CLI), where there are also instructions on how to [install the Data Registry via the CLI](https://github.com/FAIRDataPipeline/FAIR-CLI#registry).

## Select and install a Modelling API

Installation instructions for the Modelling APIs are in their respective GitHub repositories:

- [C++](https://github.com/FAIRDataPipeline/cppDataPipeline#installation)
- Java (*ToDo: Find link*)
- [Julia](https://github.com/FAIRDataPipeline/DataPipeline.jl#installation)
- [Python](https://github.com/FAIRDataPipeline/pyDataPipeline#installation)
- [R](https://github.com/FAIRDataPipeline/rDataPipeline#installation)

## Try out an example

Example models using the FAIR Data Pipeline are provided in each of the supported languages. Instructions to install and run these examples can be found in their respective GitHub repositories:

- [C++](https://github.com/FAIRDataPipeline/cppSimpleModel)
- [Java](https://github.com/FAIRDataPipeline/javaSimpleModel)
- Julia (The Julia example is installed along with the Julia Modelling API)
- [Python](https://github.com/FAIRDataPipeline/pySimpleModel)
- [R](https://github.com/FAIRDataPipeline/rSimpleModel)