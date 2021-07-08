Use Case 1. (Pre-process and) upload a new dataset using script/config file
===========================================================================

**Actor:** A Data Curator wants to upload a dataset to the registry --
this will likely involve a pre-processing step to convert a 'raw
dataset' into a suitable 'processed dataset' that can be used by a
model. Has knowledge of system and required config files to produce an
upload script

**Preconditions**: Actor has an account (if required) to access data
registry and a local copy of the dataset they want to upload (QUESTION:
what formats are acceptable?)

**Basic Flow:**

-   Actor generates metadata file for dataset

-   Actor generates a config file that gives name and location for data,
    metadata, desired name on registry

    -   Substeps needed?

    -   Do we want an Actor to confirm here that they have permission to
        upload/share the data?

-   Actor logs into system, system authenticates (Question: or should
    this be part of the config file?)

-   (optionally) Actor runs processing script to turn a dataset into the
    data format required

-   Actor runs upload script, system responds and ingests data and
    metadata

    -   Included in system response: system compares to existing data
        (possible exception case: user tries to upload dataset already
        in the registry)

-   System generates report summarising upload, including date and hash,
    etc

**Postconditions:**

-   Datasets are now in registry with metadata - both the raw dataset
    and the processed dataset

-   Pre-processing script stored as code run associated with the dataset

-   A response code from the API confirms that the upload has completed
    successfully