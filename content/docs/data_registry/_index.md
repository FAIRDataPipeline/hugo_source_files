---
weight: 3
title: "Local registry"
---

# FAIR Data Registry

The FAIR [Data Registry](https://github.com/FAIRDataPipeline/data-registry) is a component of FAIR data pipeline that provides a relational database storing metadata together with a user interface and access to the data through an Application Programming Interface (API). Metadata is kept locally and can be synchronised with a remote data registry.

The documentation for the registry is available [here](https://data.scrc.uk/docs/), and is the same for the local and remote data registry.

## Installation

### Dependencies

The data registry relies on the [```graphviz```](https://www.graphviz.org) package to produce the schema visualisation, so you will need to follow [graphviz installation process](https://www.graphviz.org/download/) for your system before initialising a local registry.

### Install local registry

To initialise a local data registry, run the following command from your terminal:

```
/bin/bash -c "$(curl -fsSL https://data.scrc.uk/static/localregistry.sh)"
```

This will install the registry and all the related files will be stored in `~/.fair`.

To run the server, run

 ```
 ~/.fair/registry/scripts/start_fair_registry
 ``` 
 
 
Then, navigate to [http://localhost:8000](http://localhost:8000) in your browser to check that the server is up and running. 

A token will be automatically generated in `~/.fair/registry/token`.

To stop the server, run: 

```
~/.fair/registry/scripts/stop_fair_registry
``` 
