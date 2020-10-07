# program-icap
Documentation repository for the Glasswall ICAP program

# ZenHub
In order to see kanban board please download this extension: https://www.zenhub.com/extension

# Associated Repos

## PoC
[filetrust/c-icap](https://github.com/filetrust/c-icap) : This repo contains the proof of concept implementation. The ICAP solution is deployed within a docker container, with the Glasswall SDK integrated.

## Cloud Deployment
The cloud deployment is implemented through the integration of the services provided by a number of repos.

[filetrust/mvp-icap-service](https://github.com/filetrust/mvp-icap-service) This provides the ICAP Server and Glasswall ICAP Resource. These components are responsible for providing the ICAP interface and submitting the content received in ICAP Requests for processing through the Glasswall products.

[filetrust/mvp-icap-cloud](https://github.com/filetrust/mvp-icap-cloud) This provides the Orchestrator that co-ordinates the processing of content received by the ICAP Server.

[filetrust/rebuild-k8s-filetypedetection](https://github.com/filetrust/rebuild-k8s-filetypedetection) This provides the source code for the File Type Detection API used during ICAP processing.

[filetrust/rebuild-k8s](https://github.com/filetrust/rebuild-k8s) This provides the deployment scripts for the ICAP services being deployed to a Kubernetes Cluster.

[filetrust/icap-argo](https://github.com/filetrust/icap-argo) This provides the Orchestration that co-ordinates the processing of content received by the ICAP on a Kubernetes environment.

[filetrust/transaction-event-api](https://github.com/filetrust/transaction-event-api) This is the API that handles transaction searches on the event store.

## Threat Model
The program's Threat Model is recorded as [ICAP Threat Model Cloud Deployment](https://glasswall.atlassian.net/browse/THREATMODL-3)
The model's diagram is [here](https://app.lucidchart.com/invitations/accept/43e0cb76-052f-486c-8bfd-166f4ad4ea4f)
