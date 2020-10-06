# 3. Use Helm3

Date: 2020-10-05

## Status

Accepted

## Context

The ICAP Proxy application will be deployed across a number of Kubernetes clusters, each serving a share of the
traffic.
All these clusters together form one "instance" of the ICAP Proxy solution.

To deploy any software to these clusters, Kubernetes manifests need to be created and managed which specify the
cluster-level dependencies, resources requirements and other aspects of running it.

In addition to the software developed in-house for the proxy, there will be a number of third-party components
also deployed to these clusters.


## Decision

We will write Helm charts for Helm version 3 for all software to be deployed as part of the ICAP Proxy
solution. We will not use any existing Helm 2 charts and not deploy Tiller on any of the clusters.


## Consequences

Using Helm 3 will give us greater flexibility to manage the software lifecycle. It does not introduce dependency on any
in-cluster software (e.g. `tiller`).
We accept with this decision that for some third-party software, where only Helm 2 charts are published, we may have to
adapt these for out use.
