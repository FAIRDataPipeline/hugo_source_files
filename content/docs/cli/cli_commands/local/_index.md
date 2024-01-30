---
weight: 2
title: "CLI Local Command(s)"
bookCollapseSection: false
---

# `fair` CLI Local Command(s)

By default the CLI requires a [remote registry]({{< relref "/docs/data_registry/remote_registry/" >}}), however the CLI can run without a remote registry using the `--local` flag.

N.B. the CLI currently requires internet access to work regardless of whether you are using a [remote registry]({{< relref "/docs/data_registry/remote_registry/" >}}).

## The `--local` flag

The following commands support the local flag:

`fair init`

`fair pull`

`fair run`

## A local workflow example

With the latest version of the [fair cli]() and a [modelling api]() installed the following is an example of a locally run workflow (without the need of a [remote registry]({{< relref "/docs/data_registry/remote_registry/" >}}))

```
fair init --local
fair pull --local config.yaml
fair run --local config.yaml
```

N.B. a remote registry can be added later by running `fair remote add`.

For example:
```
fair remote add https://data.fairdatapipleine.org/api/
```