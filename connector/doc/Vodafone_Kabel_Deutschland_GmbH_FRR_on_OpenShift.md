---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_FRR_on_OpenShift
---

# Vodafone Kabel Deutschland GmbH FRR on OpenShift

## About

This is a dedicated connector to interface with a Red Hat OpenShift cluster and underlying PODs by utilizing the OpenShift CLI Tooling (OC Tool).
The Free Range Routing (*FRR*) is a dedicated network routing suite under the OpenShift cluster hosting all instances to manage and deploy the network routes within the cluster.

> [!IMPORTANT]
> To interface with OpenShift, a dedicated CLI tool is utilized which is required to be available and installed on each DataMiner Agent where an element using this protocol is hosted.
> Refer to the Official Red Hat [Documentation](https://docs.redhat.com/en/documentation/openshift_container_platform/4.21/html/cli_tools/openshift-cli-oc)

## Key Features

- **Status overview**: Aggregated and individual status data per POD and all available FR Routes.
- **24/7 monitoring**: Constant monitoring to support continuous status updates.
- **Real-time configuration**: The connector comes with an interface to add, manage and remove FR Routes.

## Use Case

**Challenge**: Specific control and monitoring is required to manage the FRR instance within an OpenShift cluster.

**Solution**: The aggregated status indicates which PODs are up-to-date with the FRRouting, and the table actions provided in the connector allow users to activate or remove certain routes.

**Benefit**: Improves uptime and reliability next to the routing management which is now available from within DataMiner.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_FRR_on_OpenShift_Technical).
