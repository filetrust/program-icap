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

[filetrust/event-submission-service](https://github.com/filetrust/event-submission-service) This facilitates the upload of transaction event and analysis report to the Azure File Share.

[filetrust/icap-adaptation-service](https://github.com/filetrust/icap-adaptation-service) This provides the Orchestration that co-ordinates the processing of content received by the ICAP on a Kubernetes environment.

[filetrust/icap-management-ui](https://github.com/filetrust/icap-management-ui) This provides the service for a management UI used to configure the Adaptation policy and display metrics from the ICAP service, as well as a log/history of transactions. 

[filetrust/icap-request-processing](https://github.com/filetrust/icap-request-processing) This provides the rebuild functionality for the ICAP offering.

[filetrust/pod-janitor](https://github.com/filetrust/pod-janitor) This provides cleaning of Failed & Succeeded pods in the cluster.

[filetrust/transaction-event-api](https://github.com/filetrust/transaction-event-api) This is the API that handles transaction searches on the event store. The swagger deployment can be found [here](https://filetrust.github.io/transaction-event-api/#/)

[filetrust/transaction-event-api-static-data](https://github.com/filetrust/transaction-event-api-static-data) This is a tool that populates static data for the transaction-event-api

[filetrust/policy-management-api](https://github.com/filetrust/policy-management-api) This is the API that handles operations on the Adaption Policy.

[filetrust/policy-update-service](https://github.com/filetrust/policy-update-service) This handles the update to the Adaptation Policy Configmap.

[filetrust/ncfs-policy-update-service](https://github.com/filetrust/ncfs-policy-update-service) This handles the update to the NCFS Policy Configmap.

[filetrust/archive-adaptation-service](https://github.com/filetrust/archive-adaptation-service) This provides the orchestration that co-ordinates the processing of archive files.

[filetrust/archive-processing](https://github.com/filetrust/archive-processing) This process facilitates the unpacking, sending off adaptation requests and repacking of archive files.

[filetrust/reference-ncfs](https://github.com/filetrust/reference-ncfs) This process is a reference for the Non-Compliant file service. It decides the action to take when a file is considered non-compliant.

## Threat Model
The program's Threat Model is recorded as [ICAP Threat Model Cloud Deployment](https://glasswall.atlassian.net/browse/THREATMODL-3)
The model's diagram is [here](https://app.lucidchart.com/invitations/accept/43e0cb76-052f-486c-8bfd-166f4ad4ea4f)
