---
title: "Installation"
weight: 1
bookCollapseSection: true
---


# Local FAIR data registry


The documentation for the registry is available [here](https://data.fairdatapipeline.org/docs/), and is the same for the local and remote registry.

## Installation

Installation of the local registry is recommended through the [`FAIR CLI`]({{% ref "/docs/cli" %}}) and can be acheived by the following command:

```
fair registry install
```

Additionally the registry can be installed when initialising a FAIR repository using the command:

```
fair init
```

***Note:*** 

While the local registry will work out of the box, the [```graphviz```](https://www.graphviz.org) package is required to produce graphical [provenance reports]({{% ref "/docs/data_registry/prov_report" %}}#an-example-of-a-basic-provenance-diagram), therefore it is reccommeded that you install `graphviz` prior to installing the registry. To install graphviz please follow the instructions on the [graphviz website](https://www.graphviz.org).



