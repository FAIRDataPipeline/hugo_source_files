Use Case 3. QuickStart Exploratory Dataset Use/Analysis
=======================================================

**Benefit:** Modeller able to make efficient and accurate assessment of
usefulness of dataset for their purposes

**Actor:** A modelling or data scientist who wants to investigate and
visualise a dataset programmatically in the pipeline to determine if it
is suitable for their application.

**Preconditions:**

-   Dataset actor is interested in is available via data pipeline

-   Actor has some technical proficiency in at least one language used
    by the pipeline, an interest in data, ability to visualise data
    within their language of choice

**Basic flow:**

-   Actor searches for a data resource, system's search ability provides
    a link to the data and a pointer to a description. Actor decides to
    investigate use of data resource further

-   Actor installs pipeline in their language of choice

-   Actor accesses data via pipeline from their local machine, system
    provides data into a data structure usable in actor's preferred
    language

    -   We'll need sub-steps for this one, these might include:

    -   Actor defines data they want (YAML file according to some spec)

    -   Actor defines config according to some spec

    -   System recognises YAML/config files and provides data flow along
        with logs of access

    -   Locally-installed pipeline generates log files on actor's
        machine

-   Actor loads data locally, performs plotting and exploration tasks

**Postconditions:**

-   Log files on actor's local machine recording data access and use via
    pipeline

-   Actor has plots and/or exploratory description of dataset allowing
    them to judge suitability

-   Log files on registry of access by actor if desired?

**Questions:**

-   Authentication in this workflow? Not for registry but maybe for
    individual datasets. How to show access restrictions to users in a
    convenient way?

-   Thinking needed about how to make this use case convenient for good
    1^st^ impression

-   Local log files vs live local registry?