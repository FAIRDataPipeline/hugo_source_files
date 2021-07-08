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

**Questions:**

-   We don't really have a way of doing write-then-read at the moment -
    would this be a good reason to adopt local SQLite (or
    other) registry?

-   How do we think about multiple runs with potentially thousands of
    outputs and encapsulate them in a single larger-scale output? Would
    RO Crate help here?