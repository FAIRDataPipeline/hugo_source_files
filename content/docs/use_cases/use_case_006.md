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

5.  Use case: **Flag data as problematic --** an error or revision of
    data is uncovered. How do I flag this in data pipeline/registry?

6.  Use case: **Flag model/analysis code as problematic --** a
    model/analysis code error is detected or the code revised. How do I
    flag this in data pipeline/registry?

7.  Use case: **Track issues --** I am looking at the output of some
    analysis/model. How do I see issues flagged in ancestral data or
    model/analyisis?

8.  Use case: **View meta data --** I want to extract meta data about a
    particular dataset or model code

Source: Glenn Marion

Actor: Data/code producer (5 & 6). Data/software user (7 & 8)

Benefit: Results are linked to any known issues with their dependencies,
and potential users are aware of any known issues

**Questions**:

-   Are models/analysis in the data pipeline/registry? - Yes, linked to
    particular Github hashes

-   How do we implement tracing flagged items through the dependency
    links and alerting users of them?

-   How are problems flagged / quality assessments recorded? Issues can
    be attached to any object in the registry (data products, software
    releases, \...). Can also have active quality assessments recorded
    (eg scorecards completed, data quality assessments) but should not
    rely on that being done for every object in the chain.