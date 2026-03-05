---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_FRR_on_OpenShift_Technical
---

# Vodafone Kabel Deutschland GmbH FRR on OpenShift

## About

This is a dedicated connector to interface with a Red Hat OpenShift cluster and underlying PODs by utilizing the OpenShift CLI Tooling (OC Tool).
The Free Range Routing (*FRR*) is a dedicated network routing suite under the OpenShift cluster hosting all instances to manage and deploy the network routes within the cluster.

> [!IMPORTANT]
> To interface with OpenShift, a dedicated CLI tool is utilized which is required to be available and installed on each DataMiner Agent where an element using this protocol is hosted.
> Refer to the Official Red Hat [Documentation](https://docs.redhat.com/en/documentation/openshift_container_platform/4.21/html/cli_tools/openshift-cli-oc)

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

The endpoint details are configured under the **Connection Settings** page on the element together with providing the **Authentication Token** (Service Account). These will be used when performing the required commands with the OC Tool to fetch or configure the data.

## How to use

### General Page

The **General** page displays an overview of the available *PODs* and all *Active Routes*.

On the **Configuration** page, the table actions allow you to add, sync and remove routes on all PODs.
You can interface with each table by right-clicking it to access the context menu.

The **Poll Settings** page allows you to configure the polling interval per integrated command. It also shows a status if the command was succesful or what the error response was.
