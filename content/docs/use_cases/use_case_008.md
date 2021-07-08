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