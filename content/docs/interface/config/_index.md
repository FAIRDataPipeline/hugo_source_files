---
weight: 10
title: "config.yaml fields"
---

# *config.yaml* fields

<span style="font-size:12pt; color:red">Note that this is a living document and the following is subject to change.</span>

The Data Pipeline API hinges on a *config.yaml* file, which lets users specify metadata to be used during file lookup for read or write, and configure overall API behaviour. This user written *config.yaml* is translated into a working config file by `FAIR run`, which is then taken as input by the Data Pipeline API.

This page gives examples of the **user written** *config.yaml* file.

## Simple inputs and outputs

The following example reads various pieces of data and writes an external object.

```yaml
run_metadata:
  description: A simple analysis
  local_data_registry_url: https://localhost:8000/api/
  remote_data_registry_url: https://data.scrc.uk/api/
  default_input_namespace: SCRC
  default_output_namespace: johnsmith
  write_data_store: /datastore/
  local_repo: /Users/johnsmith/git/myproject/
  # `script:` points to the submission script (relative to local_repo)
  script: python path/submission_script.py ${{CONFIG_PATH}}
  # `script_path:` can be used instead of `script:`

read:
# Read version 1.0 of human/commutes
- data_product: human/commutes
  version: 1.0
# Read human/health from the cache
- data_product: human/health
  use:
    cache: /local/file.h5
# Read crummy_table with specific doi and title
- external_object: crummy_table
  doi: 10.1111/ddi.12887
  title: Supplementary Table 2
# Read secret_data with specific doi and title from the cache
- external_object: secret_data
  doi: 10.1111/ddi.12887
  title: Supplementary Table 3
  use:
    cache: /local/secret.csv
# Read weird_lost_file (which perhaps has no metadata) with specific hash
- object: weird_lost_file
  hash: b5a514810b4cb6dc795848464572771f

write:
# Write beautiful_figure and increment version number
- external_object: beautiful_figure
  unique_name: My amazing figure
  version: ${{MINOR}}
  public: false
```

- `run_metadata:` provides metadata for the run:
  - `description:` is a human readable description of the purpose of the config.yaml
  - `local_data_registry_url:` specifies the local data registry root, which defaults to https<!-- -->://localhost:8000/api/
  - `remote_data_registry_url:` specifies the remote data registry endpoint, which defaults to https<!-- -->://data.scrc.uk/api/
  - `default_input_namespace:` and `default_output_namespace:` specify the default namespace for reading and writing
  - `write_data_store:` specifies the file system root used for data writes, which is set here to /datastore. Note that if a file is referenced in the local filesystem (files specified in `read: use: cache:`) but that part of the local filesystem is not within a StorageRoot that the registry knows about, then the file will be copied into the `write_data_store` so that it can be referenced correctly in the registry.
  - The submission script itself should either be written in `script` or stored in a text file in `script_path`, which can be absolute or relative to `local_repo:` (the root of the local repository)
  - Any other fields will be ignored

- `read:` and `write:` provide references to data:
  - `data_product:` (within `read:` and `write:`), `external_object:` (`read:` and `write:`) and `object:` (`read:` only) specify metadata subsets that are matched in the read and write processes. The metadata values may use glob syntax, in which case matching is done against the glob.
  - For reads, a `cache:` may be specified directly, in which case it will be used without any further lookup.
  - If a write is carried out to a data product where no such `data_product:` entry exists, then a new data product is created with that name in the local namespace, or the patch version of an existing data product is suitably incremented. The level of incrementation or version number can be explicitly defined by `version:`.
  - If a write is carried out to an object that is not a data product and no such `external_object:` entry exists, then a new object is created with no associated external object or data product, and an issue is raised with the object to note the absence of an appropriate reference, referencing the name given in the write API call.
  - `version:` can be specified explicitly (*e.g.* `0.1.0` or `0.20210414.0`), by reference (*e.g.* `0.${{DATE}}.0`, meaning `0.20210414.0`), or by increment (*i.e.* `${{MAJOR}}`, `${{MINOR}}`, or `${{PATCH}}`). If an object already exists and no version is specified, it will be incremented by patch, by default.
  - `public:` can be specified for data products in `write:` and is taken to be `true` when absent

## Extended inputs and outputs

The following example registers a new external object and writes a data product component.

```yaml
run_metadata:
  description: Register a file in the pipeline
  local_data_registry_url: https://localhost:8000/api/
  remote_data_registry_url: https://data.scrc.uk/api/
  default_input_namespace: SCRC
  default_output_namespace: johnsmith
  write_data_store: /datastore/
  local_repo: /Users/johnsmith/git/myproject/
  script: # Points to the Python script, below (relative to local_repo)
    python path/submission_script.py {CONFIG_PATH}
# `script_path:` can be used instead of `script:`

register:
- external_object: records/SARS-CoV-2/scotland/human-mortality
  # Who owns the data?
  namespace_name: open_data_scotland_repository
  namespace_full_name: Scottish Government Open Data Repository
  namespace_website: https://statistics.gov.scot/
  # Where does the data come from?
  root: https://statistics.gov.scot/sparql.csv?query=
  path: |-
    PREFIX qb: <http://purl.org/linked-data/cube#>
    PREFIX data: <http://statistics.gov.scot/data/>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX dim: <http://purl.org/linked-data/sdmx/2009/dimension#>
    PREFIX sdim: <http://statistics.gov.scot/def/dimension/>
    PREFIX stat: <http://statistics.data.gov.uk/def/statistical-entity#>
    PREFIX mp: <http://statistics.gov.scot/def/measure-properties/>
    SELECT ?featurecode ?featurename ?areatypename ?date ?cause ?location ?gender ?age ?type ?count
    WHERE {
     ?indicator qb:dataSet data:deaths-involving-coronavirus-covid-19;
       mp:count ?count;
       qb:measureType ?measType;
       sdim:age ?value;
       sdim:causeOfDeath ?causeDeath;
       sdim:locationOfDeath ?locDeath;
       sdim:sex ?sex;
       dim:refArea ?featurecode;
       dim:refPeriod ?period.

       ?measType rdfs:label ?type.
       ?value rdfs:label ?age.
       ?causeDeath rdfs:label ?cause.
       ?locDeath rdfs:label ?location.
       ?sex rdfs:label ?gender.
       ?featurecode stat:code ?areatype;
         rdfs:label ?featurename.
       ?areatype rdfs:label ?areatypename.
       ?period rdfs:label ?date.
    }
  # Metadata
  title: Deaths involving COVID19
  description: Nice description of the dataset
  unique_name: Scottish deaths involving COVID19  
  alternate_identifier_type: ods_name
  file_type: csv
  release_date: ${{DATETIME}}    
  version: 0.${{DATE}}.0       
  primary: True
  
write:
- data_product: records/SARS-CoV-2/scotland/human-mortality/results
  description: human mortality data
  version: 0.${{DATE}}.0
```

- `register:` will take exactly one of `unique_name:` and `alternate_identifier_type`, or `identifier:`.

## Flexible inputs and outputs

The following example describes an analysis which typically reads *human/population* and writes *human/outbreak-timeseries*. Instead, a test model is run using Scottish data, whereby *scotland/human/population* is read from the *eera* namespace, rather than *human/population*. Likewise, the output is written as *scotland/human/outbreak-timeseries* rather than *human/outbreak-timeseries*.

```yaml
run_metadata:
  description: A test model
  local_data_registry_url: https://localhost:8000/api/
  remote_data_registry_url: https://data.scrc.uk/api/
  default_input_namespace: SCRC
  default_output_namespace: johnsmith
  write_data_store: /datastore/
  local_repo: /Users/johnsmith/git/myproject/
  script: # Points to the Python script, below (relative to local_repo)
    python path/submission_script.py {CONFIG_PATH}
    
read:
- data_product: human/population
  use:
    namespace: eera
    data_product: scotland/human/population

write:
- data_product: human/outbreak-timeseries
  use:
    data_product: scotland/human/outbreak-timeseries
- data_product: human/outbreak/simulation_run
  use:
    data_product: human/outbreak/simulation_run-${{RUN_ID}}
```

- `read:` and `write:` provide references to data:
  - The corresponding `use:` sections contain metadata that is used to update the call metadata before the file access is attempted
  - Any part of a `use:` statement may contain the string `${{RUN_ID}}`, which will be replaced with the run id, otherwise a hash of the config contents and the date will be used
