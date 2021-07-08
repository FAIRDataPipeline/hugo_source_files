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