---
weight: 40
title: "FAIR CLI functions"
---

# `fair` CLI functions

<span style="font-size:12pt; color:red">Note that this is a living document and the following is subject to change.</span>

A simple example of how the data pipline should run from the command line:

```bash
fair pull config.yaml
fair run config.yaml
fair push config.yaml
```

## `fair pull`

- download any data required by `read:` from the remote data store and record metadata in the data registry (whilst editing relevant entries, *e.g.* `storage_root`)
- pull meta data associated with all previous versions of these objects listed in `write:` from the remote data registry
- download any data listed in `register:` from the original source and record metadata in the data registry

## `fair run`

- read (and validate) the *config.yaml* file
- generate a working *config.yaml* file (see [Working example]({{% ref "/docs/interface/example1" %}}))
  - globbing is used to interpret `*` as all matching objects as well as the original string returned, *e.g.* if `real/data/1` version 0.0.1 and `real/data/thing/1` version 0.0.1 already exist in the registry, the user-written config:
  
    ```yaml
    write:
    - data_product: real/data/**
      description: general description for all data products
      use:
        namespace: someone
        version: ${{MINOR}}
    ```

    should return:
  
    ```yaml
    write:
    - data_product: real/data/1
      use:
        data_product: real/data/1
        description: general description for all data products
        version: 0.1.0
        namespace: someone
        public: TRUE
    - data_product: real/data/thing/1
      use:
        data_product: real/data/thing/1
        description: general description for all data products
        version: 0.1.0
        namespace: someone
        public: TRUE
    - data_product: real/data/**
      use:
        data_product: real/data/**
        description: general description for all data products
        version: 0.0.1
        namespace: someone
        public: TRUE
    ```

  - specific version numbers and any variables in `run_metadata:`, `register:`, `read:`, and `write:` are replaced with true values, *e.g.*
    - `${{CONFIG_DIR}}` is replaced by the directory within which the working *config.yaml* file resides
    - `release_date: ${{DATETIME}}` is replaced by `release_date: 2021-04-14 11:34:37`
    - `version: 0.${{DATE}}.0` is replaced by `version: 0.20210414.0`
    - `version: ${{PATCH}}` should increment version by patch; and
    - `version: 0.${{DATETIME-%Y%m%d}}.0` or any variants thereof are replaced by an appropriately formatted string.
  - if no version is given, then one should be written such that patch is incremented if the data product already exists, otherwise version should be set to 0.0.1.
  - `register:` is removed and `external_object`s are written to `read:` as `data_product`s
  - populate `public:` field in `write:` sections (default is `true`)
- `local_repo:` must always be given in the *config.yaml* file
  - ensure the repo is clean
  - get the hash of the latest commit and add to the working *config.yaml* file in `run_metadata: latest_commit:`
  - if `run_metadata: remote_repo:` is `false`, then `fair push` should copy the repo to the file store
  - if `run_metadata: remote_repo:` is absent or doesn't contain a URL, then `fair run` should try to get the remote repo url from the local repo
  - note that there are exceptions and the user may reference a script located outside of a repository
- save the working *config.yaml* file in the local data store, in *<local_store>/coderun/\<date>T\<time>/config.yaml*, e.g. *datastore/coderun/20210625T165552/config.yaml*
- save the submission script to the local data store in *<local_store>/coderun/\<date>T\<time>/script.sh*
  - note that *config.yaml* should contain either `script:` that should be saved as the submission script, or `script_path:` that points to the file that should be saved as the submission script
- save the path to *<local_store>/coderun/\<date>T\<time>/* in the global environment as `$FDP_CONFIG_DIR` so that it can be picked up by the script that is run after this has been completed
- execute the submission script

## `fair push`

- push new files (generated from `write:` and `register:`) to the remote data store
- record metadata in the data registry (whilst editing relevant entries, *e.g.* `storage_root`)
