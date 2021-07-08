Use Case 2. Uploading a new dataset via a GUI
=============================================

**Benefit:** This would enable people who don't know how to write
scripts to casually interact with the system

**Actor:** A person who has found a dataset that they want to upload to
the registry.

**Preconditions**: User has an account (if required) to access data
registry and a local copy of the dataset they want to upload (QUESTION:
what formats are acceptable?)

**Basic Flow:**

-   Actor logs into system, system authenticates

-   Actor selects web interface for adding a dataset to the registry,
    system loads page

-   Actor drags file to upload, system uploads and saves

-   System prompts Actor to confirm they have permission to upload/share
    these data

-   System prompts user for metadata, with form or upload option

-   Actor either uploads metadata file (Question: in what format?), or
    enters information in form

-   System records metadata with dataset, creates data product and adds
    to registry

-   System generates report summarising upload, including date and hash,
    etc

**Postconditions:**

-   Dataset is now in registry with metadata

-   Actor has a report describing the upload of the data including a
    hash and date, and knows how and where to find those data

**Exceptions:**

-   Data is already uploaded? Do we allow reuploads?

**Questions**

-   Where / how? Could happen in Django\... already thought about doing
    this in a shiny app, should it generate a script that can be
    uploaded (and run via use case 1)?

-   Supported formats for data and meta-data (eg supported data
    structures vs blobs)

-   Authorisation to write to certain namespaces?

-   Reproducing registry from scripts -- how to maintain if GUI route
    supported?