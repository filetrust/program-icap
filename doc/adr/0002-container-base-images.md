# 2. Container Base Images

Date: 2020-10-05

## Status

Accepted

## Context

One of the requirements for the ICAP Proxy project as outlined in the SoW is for the software deliverables
to _be compatible with CentOS v7.x and RHEL v7.x to the nearest patch schedule._

Since the application will consist of a number of containers, orchestrated by and running on Kubernetes clusters,
it is necessary to decide how this requirement should be interpreted for the container images used to spawn these containers.

It is already established that these container images will be prepared by us and handed over to customers both for initial
release as well as future updates.


## Decision

For container images built by Glasswall, which form part of the final deliverables, we will exclusively use **CentOS 7** or **RHEL 7**
at the discretion of the development teams owning these containers.

In addition to these, we will include verbatim copies of officially released container images for any open-source or commercial
third-party software we deploy to these clusters. These images will be taken from their respective official release channels,
their versions documented and then included in the final deliverables.


## Consequences

The requirement to use CentOS or RHEL will increase the image sizes beyond what would strictly be necessary.
On the other hand it will unambiguously fulfill the requirement given in the SoW and also reduce softwaretesting burden.

By including third-party images as-is, we accept that we are introducing some base image diversity in exchange for not
having to build and maintain our own versions of these software components.
We believe that their use is inconsequential and will not violate the SoW requirement as written.
