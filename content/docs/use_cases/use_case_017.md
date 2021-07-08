Use Case 17. Actor wants to run a model with some non-publicly accessible data
==============================================================================

**Preconditions**: Actor has an account (if required) to access data
registry, metadata is public, actor has access to the private data which
is registered in registry

**Basic Flow:**

How this could work:

Local pipeline scripts have to know about local cache of private files,
then pipeline can execute as normal in use case 4.