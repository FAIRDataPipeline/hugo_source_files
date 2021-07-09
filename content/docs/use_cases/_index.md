---
weight: 7
title: "Uses cases"
bookCollapseSection: true
---
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

Use Case 5. Parameter inference coupled with model simulation
=============================================================

This requires repeated application of **two component use cases** shown
below:

1.  Use case: **draw multiple data from data pipeline/registry** for use
    in analysis (data for inference)

2.  Use case: **Run model/analysis that generates multiple
    reps/samples** from a potentially high dimensional distribution and
    then to add these to the data pipeline/registry tracking data
    dependencies (parameter inference)

3.  Use case: draw multiple data from data pipeline/registry for use in
    analysis (data to run model including inferred parameters)

4.  Use case: Run model/analysis that generates multiple reps/samples
    from a potentially high dimensional distribution and then to add
    these to the data pipeline/registry tracking data dependencies
    (parameter inference)

Actor: Researcher undertaking significant inference or analysis exercise
couple with model simulation where repeated sampling and recording is
required

Benefit: really useful as a way of archiving derivatives of complex
queries, potentially linking otherwise separate datasets and generating
multiple iterations. Careful nomenclature of such files, as well as
stoarge capacity seem very important considerations

Questions:

-   We don't really have a way of doing write-then-read at the moment -
    would this be a good reason to adopt local SQLite (or
    other) registry?

-   How do we think about multiple runs with potentially thousands of
    outputs and encapsulate them in a single larger-scale output? Would
    RO Crate help here?

Use Case 6. Flag and Track issues in data and model/analysis-code
=================================================================

Subsequent revisions to the inference algorithm (step-2), data used for
inference (step-1) or additional data used for simulation (step-3) would
then flag subsequent model outputs as needing revision. If outputs from
step-4 are used in further analysis want to track dependencies i.e. if
the data or analysis in any step is flagged I want to see this when I
look at downstream outputs.

This requires application of four further **component use cases** shown
below:

1.  Use case: **Flag data as problematic --** an error or revision of
    data is uncovered. How do I flag this in data pipeline/registry?

2.  Use case: **Flag model/analysis code as problematic --** a
    model/analysis code error is detected or the code revised. How do I
    flag this in data pipeline/registry?

3.  Use case: **Track issues --** I am looking at the output of some
    analysis/model. How do I see issues flagged in ancestral data or
    model/analyisis?

4.  Use case: **View meta data --** I want to extract meta data about a
    particular dataset or model code

Actor: Data/code producer (5 & 6). Data/software user (7 & 8)

Benefit: Results are linked to any known issues with their dependencies,
and potential users are aware of any known issues

**Question**:

-   Are models/analysis in the data pipeline/registry? - Yes, linked to
    particular Github hashes

-   How do we implement tracing flagged items through the dependency
    links and alerting users of them?

-   How are problems flagged / quality assessments recorded? Issues can
    be attached to any object in the registry (data products, software
    releases, \...). Can also have active quality assessments recorded
    (eg scorecards completed, data quality assessments) but should not
    rely on that being done for every object in the chain.



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



Use Case 8. Finding and assessing alternative datasets from registry
====================================================================

**Actor:** Modeller who has data files pre-registered, and who needs to
decide which data resources to use in an output run

**Preconditions**: Actor has an account (if required) to access data
registry

**Basic Flow:**

-   Actor collates list of data resources required for model run

-   Actor interrogates registry to review status of all prerequisite
    data resources

-   Where a data resource is flagged as 'at risk', or has some other
    property (too recent? Might want to roll back to an earlier version)
    actor can request a list, with summary metadata (tbc), of other
    'views/components/distributions' or versions of that data resource

-   Actor selects view for use in this run

**Postconditions:**

-   The actor has been able to make an informed choice of data resource
    views

**Questions:** Do we want to flag up data status/issues via web
interface and also during programmatic access?



Use Case 9. Review of current status of a pipeline validated output
===================================================================

**Actor:** Policy broker who has an output, previously generated and
registered within the pipeline. There is a need to assess whether the
output has been superseded, and if so, in what ways. Or modeller has an
analysis that they have previously done, wants to know if they ran it
again are any of the data products or model code updated?

**Preconditions**: Actor has an account (if required) to access data
registry.

**Basic Flow:**

-   Actor finds code run or data output to investigate

-   Actor accesses registry entry for the specified output

-   Actor queries registry to establish the status of the data resources
    relative to the current state of the registry

-   Registry produces list of pre-requisite data resources, and
    (optionally) the status of these at the time the output was
    generated (I assume these latter are available from the metadata of
    the output itself)

**Postconditions:**

-   No change to registry

-   Actor has sufficient information to assess the output to assess
    whether the data is

    -   Up to date

    -   Is there a newer version of any of the data or model code?

    -   Has any of the existing data now got attached warnings /
        invalidated

-   Actor has sufficient information to have an informed discussion with
    modeller as to the current validity of the past output

Use Case 10. Retrospective assessment of status, when generated, of a pipeline validated output
===============================================================================================

**Actor:** Policy broker who has a query about the provenance of an
output, previously generated and registered within the pipeline. There
is a need to confirm whether the output had appropriate caveats attached
when circulated. (Sorry to be negative, but I can see this happening...
)

**Preconditions**: Actor has an account (if required) to access data
registry.

**Basic Flow:**

-   Actor accesses registry entry for the specified output

-   Actor queries registry to recover the status of the data resources
    used at the time the output was generated (I assume these latter are
    available from the metadata of the output itself; if these are not
    available, is there sufficient information in the metadata for them
    to be reconstructed?)

**Postconditions:**

-   No change to registry

-   Actor has sufficient information to assess the output from the point
    of view of the needs of policy customers

**Exception cases:**

-   The obvious one is the situation where the output has not been
    registered in the registry, but where there is sufficient knowledge
    of the data resources used to be confident about what was actually
    used. However, I think we should not seek to cover this scenario,
    since the users have already broken the system, and the existence of
    a tool to retrospectively cover everyone's back might just encourage
    poor behaviour..

Questions: How would we keep track of history of status/issues to be
able to re-create status reports from past points in time? If status
consists of timestamped issues and QA reports that are then immutable,
then this would be possible.

How important is it that this is easy / convenient vs "possible by
digging into the database"?



Use Case 11. Understanding of local data
========================================

**Actor:** Modeller has datasets locally on computer, wants to know if
they are already on registry, and if so what they are

**Preconditions**: Actor has an account (if required) to access data
registry.

**Basic Flow:**

-   Actor finds file / files to investigate

-   Actor queries registry to recover the status of the data

**Postconditions:**

-   No change to registry

-   Actor has sufficient information to assess the output to assess
    whether the data is

    -   In registry at all (from checksum)

    -   Up to date -- is there a newer version?

    -   Has attached warnings / invalidated

**Exception cases:**

-   What if the data was in the registry but has been corrupted or
    accidentally edited, is there some way of telling what it
    (probably?) should have been?

**Notes:** Possible a tool for data import to the registry that
calculates checksums could be run over the directory



Use Case 12. Actor wants to understand provenance of reported results
=====================================================================

Similar to use cases 9 or 10, but no preconditions about accounts, and
actor may not have access to report, or may only have document

**Actor:** Member of public wants to understand provenance of reported
results

**Basic Flow:**

Possible ways this could work:

1\. Via a searchable interface to the data registry

2\. Have access to PDF (or other format) of policy document

-   can use PDF directly to identify provenance report to display

2\. Have access to pdf of report and can use pdf to identify provenance
report to display

-   PDF has embedded DOI or link to provenance report in registry

-   PDF is uploaded by user and the system identifies it via a checksum

-   PDF has a unique title/identifier used to look up provenance report

**Notes:** Report documents must be (manually?) added to registry for
this to work. Or must be part of workflow for latex document creation.

Use Case 13. Actor wants to identify changes between model outputs
==================================================================

Any user of the model outputs (e.g. modeller, policy maker) wants to
know what changed between two published model outputs / reports, and
generates a diff between the provenances

**Basic Flow:**

This requires use case 12, plus a mechanism for displaying a
comprehensible diff.



Use Case 14. From a screen on the visualisation platform, the user wants to follow a link to a provenance report for the underlying data and processing
=======================================================================================================================================================

Possible ways this could work:

1\. visualisation platform itself uses traceability framework within it
to generate provenance reports

2\. visualisation platform manually links back to provenance of the
components that are interactively selected

Use Case 15. Initial quick look at dataset visualisations online
================================================================

Any user (policy maker, modeller, etc.) may either want to investigate
public datasets registered in data registry visually, or may be
investigating a provenance reports and want to see what a dataset is
that is traced in report.

**Basic flow:**

Links directly from data pipeline to visualisation infrastructure, no
programming



Use Case 16. Actor wants to do a model run inside a safe haven
==============================================================

**Preconditions**: Actor has an account (if required) to access data
registry, actor has access to safe haven, metadata is public

**Basic Flow:**

Possible ways this could work:

1\. Registry sits inside safe haven, as does all data required for
analysis -- full pipeline runs inside safe haven

-   Registry must sync with an external registry (at simplest just a
    read-only copy) or have a direct external public interface to ensure
    public availability of provenance data, otherwise many use cases
    will break -- especially anything policy- or public-facing, where
    users will not have access to safe haven

2\. Registry sits outside safe haven, public data can be hosted outside
safe haven, but is pulled in as required to be used in the modelling run
along with the private data. Pipeline run generates log files that are
then pushed back to registry after run.

Then as use case 4.

**Notes:**

Potential issue with 1 -- how does post-processing of results generated
in a safe haven (e.g. to produce reports) work if write access to
registry is only available inside safe haven?

Use Case 17. Actor wants to run a model with some non-publicly accessible data
==============================================================================

**Preconditions**: Actor has an account (if required) to access data
registry, metadata is public, actor has access to the private data which
is registered in registry

**Basic Flow:**

How this could work:

Local pipeline scripts have to know about local cache of private files,
then pipeline can execute as normal in use case 4.