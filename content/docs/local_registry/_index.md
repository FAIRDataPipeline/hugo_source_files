---
weight: 3
title: "Local registry"
---

# Local registry


The documentation for the registry is available [here](https://data.scrc.uk/docs/), and is the same for the local and remote registry.

## Installation

### Dependencies

The registry relies on the [```graphviz```](https://www.graphviz.org) package to produce the schema visualisation, so you will need to follow [graphviz installation process](https://www.graphviz.org/download/) for your system before initialising a local registry.

#### Windows Dependencies

To install and run the local registry on windows the following dependencies are required:

  - [Chocolatey](https://chocolatey.org/)
    
    Once Chocolatety is installed the following dependencies can be installed using chocolatey:
    
      - [Python 3](https://community.chocolatey.org/packages/python/3.9.7)
      - [CURL](https://community.chocolatey.org/packages/curl)
      - [GIT](https://community.chocolatey.org/packages/git)

### Install local registry (Linux / MAC OS)

To initialise a local registry, run the following command from your terminal:

```
/bin/bash -c "$(curl -fsSL https://data.scrc.uk/static/localregistry.sh)"
```

This will install the registry and all the related files will be stored in `~/.fair`.

To run the server, run the `~/.fair/registry/scripts/start_fair_registry` script, then navigate to http://localhost:8000 in your browser to check that the server is up and running. A token will be automatically generated in `~/.fair/registry/token`.

To stop the server, run the `~/.fair/registry/scripts/stop_fair_registry` script.

### Install local registry (Windows)

To initialise a local registry on windows, run the following commands from command prompt

```
curl https://data.scrc.uk/static/localregistry.bat > localregistry.bat

localregistry.bat
```

This will install the registry and all the related files will be stored in `C:\Users\<username>\.fair`

To run the server, run the `C:\Users\<username>\.fair\registry\scripts\start_fair_registry_windows.bat` script, this will spawn the server in a new window.
Navigate to http://localhost:8000 in you browser to check the server is up and running. A token will be automatically generated in `C:\Users\<username>\.fair\registry\token`.

To stop the server switch to the server window and press control + break or run: `taskkill /IM Python.exe /F`. However this will kill **all** Python scripts.

### Default Credentials

By default the local registry creates a superuser for the admin console with the username: `admin` and the password: `admin`
