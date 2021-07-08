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

**Questions:** How would we keep track of history of status/issues to be
able to re-create status reports from past points in time? If status
consists of timestamped issues and QA reports that are then immutable,
then this would be possible.

How important is it that this is easy / convenient vs "possible by
digging into the database"?