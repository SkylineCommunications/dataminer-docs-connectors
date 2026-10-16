---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_FRR_on_OpenShift_Technical
description: Configure and use the FRR on OpenShift connector in DataMiner, with connection settings and operational guidance.
---

# Vodafone Kabel Deutschland GmbH FRR on OpenShift

## About

The Vodafone Kabel Deutschland GmbH FRR on OpenShift connector monitors pods and manages FRRouting (FRR) routes in a Red Hat OpenShift cluster using the OpenShift CLI (`oc`).

FRRouting is a network routing suite used to manage and deploy routes within the cluster.

> [!IMPORTANT]
> To interface with OpenShift, a dedicated CLI tool is utilized, which must be available and installed on each DataMiner Agent where an element using this protocol is hosted. Refer to the official [Red Hat documentation](https://docs.redhat.com/en/documentation/openshift_container_platform/4.21/html/cli_tools/openshift-cli-oc).

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the **Connection Settings** page, configure the endpoint details and provide the service account's **Authentication Token**. The connector uses these settings when running OpenShift CLI commands to retrieve data or configure routes.

## How to Use

### General Page

The **General** page displays an overview of the available **PODs** and all **Active Routes**.

On the **Configuration** page, the table actions allow you to add, sync, and remove routes on all pods. Right-click a table to access its context menu.

On the **Poll Settings** page, you can configure the polling interval for each integrated command. The page also shows whether each command succeeded or displays its error response.
