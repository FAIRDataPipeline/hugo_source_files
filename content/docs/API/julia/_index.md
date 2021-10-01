---
weight: 20
---

# DataRegistryUtils.jl

The `DataPipeline.jl` package contains functions used to interface with the FAIR Data Pipeline in Julia.

## Features
- Conveniently download Data Products from the SCRC [Data Registry](https://data.scrc.uk/).
- File hash-based version checking: new data is downloaded only when necessary.
- A SQLite layer for convenient pre-processing (typically aggregation, and the joining of disparate datasets based on common identifiers.)
- Easily register model code or realisations (i.e. 'runs') with a single line of code.

## Installation

The package is not yet registered and must be added via the package manager Pkg:

``` julia
using Pkg
Pkg.add(url="https://github.com/FAIRDataPipeline/DataPipeline.jl")
```

## Usage

See the [package documentation][docs] for instructions and examples.

## Source code

See the package's [code repo][repo].

[docs]: https://www.fairdatapipeline.org/DataPipeline.jl/stable/
[repo]: https://github.com/FAIRDataPipeline/DataPipeline.jl
