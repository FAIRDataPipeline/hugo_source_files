Use Case 7. Production of a pipeline validated policy briefing
==============================================================

**Actor:** Modeller who has some data files pre-registered, and a policy
request for information that requires a rerun of model code.

**Preconditions**: Actor has an account (if required) to access data
registry, local copies of any further datasets they need to upload, and
a valid model code release registered.

**Basic Flow:**

-   Actor collates/reviews list of data resources required for model run

-   Actor identifies any gaps in data and uploads local copies to
    registry

-   Actor interrogates registry to review status of all prerequisite
    data resources

-   Actor iterates choice of data resources, preferably to remove 'at
    risk' selections, and to make time specific selections as they see
    fit

-   Actor interrogates registry to confirm status of all prerequisite
    data resources

-   Actor runs registered. released version of model software using
    selected data resources (likely to be multiple runs)

-   Output from model uploaded to registry

-   Model output used in rmd-type framework to generate policy briefing

-   Policy briefing uploaded to registry with links to dependencies

-   Status reports for any given model run and for the entire the
    briefing can be generated (listing dependencies, provenance,
    flagging up QA status and issues)

-   *\[Status of policy briefing reviewed prior to circulation\]*

-   *\[Brief either circulated with appropriate cover based on
    meta-data, or rejected and referred back to be re-generated\]*

**Postconditions:**

-   Newly uploaded data products are in registry with associated
    metadata

-   Model output and policy brief are in registry with associated
    metadata

-   Actor has a brief with known provenance ready for onward circulation

**Questions:**

-   Again -- what do we do with the data types (like the reports) that
    are not in a core data format?

-   Could provenance reports and QA info be generated for any "object"
    in the registry?