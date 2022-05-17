---
weight: 7
title: "Repository Status"
---

Work in progress. All blank cells are TBDs. Idea is not to duplicate the software checklist or other information held in repositories, but to summarise it in one place.

# CI Dashboard
FAIRDataPipeline_FDP-Cpp-API
| Repository | CI Status | Coverage | Default branch | Static Analysis |
| --- | --- | --- | --- | --- |
| FAIR-CLI | [![FAIR Data Pipeline CLI](https://github.com/FAIRDataPipeline/FAIR-CLI/actions/workflows/fair-cli.yaml/badge.svg?branch=develop)](https://github.com/FAIRDataPipeline/FAIR-CLI/actions/workflows/fair-cli.yaml) | [![codecov](https://codecov.io/gh/FAIRDataPipeline/FAIR-CLI/branch/develop/graph/badge.svg)](https://codecov.io/gh/FAIRDataPipeline/FAIR-CLI) | `develop` | [![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=FAIRDataPipeline_FAIR-CLI&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=FAIRDataPipeline_FAIR-CLI) |
| data-registry | [![FAIR Data Registry](https://github.com/FAIRDataPipeline/data-registry/actions/workflows/fair-data-registry.yaml/badge.svg?branch=main)](https://github.com/FAIRDataPipeline/data-registry/actions/workflows/fair-data-registry.yaml) | [![codecov](https://codecov.io/gh/FAIRDataPipeline/data-registry/branch/main/graph/badge.svg)](https://codecov.io/gh/FAIRDataPipeline/data-registry) | `main` | **unknown** |
| cppDataPipeline| [![FDP C++ API](https://github.com/FAIRDataPipeline/cppDataPipeline/actions/workflows/fdp_cpp_api.yaml/badge.svg)](https://github.com/FAIRDataPipeline/cppDataPipeline/actions/workflows/fdp_cpp_api.yaml) | [![Coverage](https://sonarcloud.io/api/project_badges/measure?project=FAIRDataPipeline_FDP-Cpp-API&metric=coverage)](https://sonarcloud.io/summary/new_code?id=FAIRDataPipeline_FDP-Cpp-API) | `main` | [![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=FAIRDataPipeline_FDP-Cpp-API&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=FAIRDataPipeline_FDP-Cpp-API) |
| DataPipeline.jl | [![Package Testing](https://github.com/FAIRDataPipeline/DataPipeline.jl/actions/workflows/testing.yaml/badge.svg)](https://github.com/FAIRDataPipeline/DataPipeline.jl/actions/workflows/testing.yaml) | [![codecov](https://codecov.io/gh/FAIRDataPipeline/DataPipeline.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/FAIRDataPipeline/DataPipeline.jl) | `main` | **unknown** |
| javaDataPipeline | [![test with reg](https://github.com/FAIRDataPipeline/javaDataPipeline/actions/workflows/build-test-with-registry.yml/badge.svg)](https://github.com/FAIRDataPipeline/javaDataPipeline/actions/workflows/build-test-with-registry.yml) | [![codecov](https://codecov.io/gh/FAIRDataPipeline/javaDataPipeline/branch/master/graph/badge.svg?token=WHX17OYLBo)](https://codecov.io/gh/FAIRDataPipeline/javaDataPipeline) | `main` | Code style checked on commit (not automated) |
| pyDataPipeline | [![pyDataPipeline](https://github.com/FAIRDataPipeline/pyDataPipeline/actions/workflows/pyDataPipeline.yaml/badge.svg?branch=dev)](https://github.com/FAIRDataPipeline/pyDataPipeline/actions/workflows/pyDataPipeline.yaml) | [![codecov](https://codecov.io/gh/FAIRDataPipeline/pyDataPipeline/branch/dev/graph/badge.svg)](https://codecov.io/gh/FAIRDataPipeline/pyDataPipeline) | `dev` | **unknown** |
| rDataPipeline | [![rDataPipeline](https://github.com/FAIRDataPipeline/rDataPipeline/workflows/build/badge.svg?=1)](https://github.com/FAIRDataPipeline/rDataPipeline/actions) | [![codecov](https://codecov.io/gh/FAIRDataPipeline/rDataPipeline/branch/main/graph/badge.svg)](https://codecov.io/gh/FAIRDataPipeline/rDataPipeline) | `main` | **unknown** |
| cppSimpleModel | [![cppSimpleModel](https://github.com/FAIRDataPipeline/cppSimpleModel/actions/workflows/cpp_simple_model.yaml/badge.svg)](https://github.com/FAIRDataPipeline/cppSimpleModel/actions/workflows/cpp_simple_model.yaml) | NA | `main` | NA |
| *Julia example?* | | | |
| javaSimpleModel | ![build](https://github.com/FAIRDataPipeline/javaSimpleModel/actions/workflows/gradle-build.yml/badge.svg) ![run w fair cli](https://github.com/FAIRDataPipeline/javaSimpleModel/actions/workflows/runWithFairCli.yml/badge.svg) | NA | `master` | NA |
| pySimpleModel | ![build](https://github.com/FAIRDataPipeline/pySimpleModel/actions/workflows/pySimpleModel.yaml/badge.svg) | NA | `main` | NA |
| rSimpleModel | ![build](https://github.com/FAIRDataPipeline/rSimpleModel/actions/workflows/test-build.yaml/badge.svg) | NA | `main` | NA |

Note: static analyusis may nto be available or appropriate for all languages.

# Documentation

| Repository | Remarks |
| --- | --- |
| FAIR-CLI | Docs in readme and in `docs` folder, doscstrings not currently used to build docs. |
| data-registry | User docs on Hugo site. Dev docs in docs folder of repo. |
| cppDataPipeline | Automated docs built to website <https://www.fairdatapipeline.org/cppDataPipeline/> |
| DataPipeline.jl | Automated docs built to website <https://www.fairdatapipeline.org/DataPipeline.jl/stable/>, also <https://www.fairdatapipeline.org/docs/API/julia/> |
| javaDataPipeline |  Automated docs built to website <https://www.fairdatapipeline.org/javaDataPipeline/>, also user docs <https://www.fairdatapipeline.org/docs/API/Java/> |
| pyDataPipeline | Automated docs built to website <https://www.fairdatapipeline.org/pyDataPipeline/>, also <https://www.fairdatapipeline.org/docs/API/python/> |
| rDataPipeline | Automated docs built to website <https://www.fairdatapipeline.org/rDataPipeline/>, also <https://www.fairdatapipeline.org/docs/API/R/> |
| cppSimpleModel | <https://github.com/FAIRDataPipeline/cppSimpleModel#readme> |
| *Julia example?* | |
| javaSimpleModel |<https://github.com/FAIRDataPipeline/javaSimpleModel#readme> |
| pySimpleModel | <https://github.com/FAIRDataPipeline/pySimpleModel#readme> |
| rSimpleModel | <https://github.com/FAIRDataPipeline/rSimpleModel#readme> |

# Status

{{<repo_stat_table>}}
