---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_FRR_on_OpenShift
description: "Explore key features and use cases of the Vodafone Kabel Deutschland GmbH FRR on OpenShift connector for managing cluster routing in DataMiner."
---

# Vodafone Kabel Deutschland GmbH FRR on OpenShift

## About

The Vodafone Kabel Deutschland GmbH FRR on OpenShift connector monitors pods and manages FRRouting (FRR) routes in a Red Hat OpenShift cluster using the OpenShift CLI (`oc`).

FRRouting is a network routing suite used to manage and deploy routes within the cluster.

## Key Features

- **Status overview**: Displays aggregated and individual status data per pod and all available FRR routes.
- **24/7 monitoring**: Monitors continuously to provide constant status updates.
- **Real-time configuration**: Allows you to add, manage, and remove FRR routes from DataMiner.

## Use Cases

### Managing FRR Routes in OpenShift

**Challenge**: Managing FRR within an OpenShift cluster requires visibility into route configuration and deployment status across pods.

**Solution**: The aggregated status shows which pods are up to date with the FRR route configuration. Table actions allow you to activate or remove routes.

**Benefit**: You can manage routes and review their deployment status directly in DataMiner.

## Technical Reference

### Prerequisites

To interface with OpenShift, a dedicated CLI tool is utilized, which must be available and installed on each DataMiner Agent where an element using this protocol is hosted.

For more information, refer to the official [Red Hat documentation](https://docs.redhat.com/en/documentation/openshift_container_platform/4.21/html/cli_tools/openshift-cli-oc).

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_FRR_on_OpenShift_Technical).
