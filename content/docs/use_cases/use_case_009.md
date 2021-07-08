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