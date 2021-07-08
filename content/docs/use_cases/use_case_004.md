Use Case 4. Model run
=====================

**Benefit:** Modeller is able to easily analyse dataset(s), generate
output and upload to registry

Similar to use case 3, but end to end run, including outputs generated
and upload of results to registry and data stores

**Actor:** A modelling or data scientist who wants to programmatically
run an analysis and add the results to the pipeline

**Preconditions:**

-   Dataset(s) actor is interested in is available via data pipeline

-   Actor has some technical proficiency in at least one language used
    by the pipeline, an interest in data, ability to visualise data
    within their language of choice

**Basic flow:**

-   Actor searches for data resource(s), system's search ability
    provides a link to the data and a pointer to a description. Actor
    decides to conduct analysis using data resources

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

-   Actor loads data locally, performs analysis, generates outputs, all
    of which actions are traced using the pipeline API

**Postconditions:**

-   Log file use on actor's local machine recording data access and use
    and outputs generated via pipeline

-   Actor has analytical results to investigate

-   if model run was successful then outputs are uploaded to data stores
    and logs of access and creation of files by actor are stored on
    registry

**Questions:**

-   Authentication in this workflow? Not for registry but maybe for
    individual datasets. How to show access restrictions to users in a
    convenient way?

-   Local log files vs live local registry?