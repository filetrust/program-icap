# 4. ICAP Original and Rebuilt Store Storage Solution

Date: 2020/10/12

## Status
Proposed

## Context

The design of the ICAP Adaptation cluster includes the use of two stores. The `Original` Store is used to persist the content of the incoming ICAP Request. The`Rebuilt` store is used to persist the version of the original content that has been rebuilt by the GlasswallSDK.

The content being processed through the ICAP Adaptation cluster is customer data and therefore should be treated as being highly sensitive in nature.

Some of the components that require access to the stores are in high risk zones. These zones are where content is being processed by the Glasswall SDK and are at risk of being compromised by malware that is activited during the processing of the document within the Glasswall SDK.

Storing the data within the cluster keeps the data local to where it is being processed.

Storing the data within a Persistant Volume makes it available to all pods within the cluster.

## Decision

### Option 1: Stored in open file
Simple to implement. No additional processing overhead encrypt\decrypt cycles). Content at risk of compromise in the event of targetted malware.

### Option 2: Use MinIO Security Token Service (STS) 
This would enable local storage of the content.
Question over concurrency performance.
Provides secure access through time-limited keys.

### Option 3: Use BLOB Storage with Shared Access Signature Strings
Requires the use of additional Platform Service.
Requires the transfer of the content from local file in ICAP Server to cloud storage.

### Option 4: Pass Public Key to Consumer Component
This would enable local storage of the content.
Content is encrypted at rest.
Access limited to key receipient only.

## Consequences

Storing the content in a Persistent Volume would keep the data local to where it is being used.

Storing the content unencrypted puts the data at risk of being compromised.

Using BLOB storage provides encrypted data at rest and restricted access.

Using BLOB storage places an additional platform service dependency on the solution.

Early prototyping with MinIO experienced issues unload heavy concurrently load.

