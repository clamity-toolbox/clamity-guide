# Data Packs

**Clamity** data packs are a means of providing contextual data associated with
the platform or platform sub-component. As infrastructure resources are deployed
in an aabstracted way, the details of the environment (things like account
numbers, server endpoints, resource IDs, etc...) aren't readily available in
static configurations. Clamity's solution for working with contexts like this is
to identity a **current data pack**. A typical example could be a platform that
defines a **production** and a **development (non-production)** set of resources
in which services operate.  By installing **production** and **development**
data packs, one could easily change context between them.

There's only support for **git repository** data packs where installation of one
is effectively cloning a repo and keeping it current is automatically handled by
running **git pulls** when info is requested from it. Not overly efficient but
good enough for now.

Use the `clamity context data-pack` command for more.
