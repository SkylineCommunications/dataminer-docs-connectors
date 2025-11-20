---
uid: Connector_help_Red_Hat_Enterprise_Openshift
---

# Red Hat Enterprise OpenShift

## About

Red Hat Enterprise OpenShift allows the full management of enterprise Kubernetes deployments. This connector monitors the entire north-south infrastructure, from containers to PODs and nodes. It also includes real-time statistics of the main elements.

This connector allows full monitoring and SRM support of OpenShift instances.

### Version Info

| Range   | Description                                    | DCF Integration | Cassandra Compliant |
|---------|------------------------------------------------|-----------------|---------------------|
| 1.0.0.x | Initial Version - Version 3.6                  | No              | Yes                 |
| 1.1.0.x | Initial Version - Version 3.7                  | No              | Yes                 |
| 1.2.0.x | API v1.11+                                     | No              | Yes                 |
| 1.2.1.x | API v1.11+, virtual connection changed to HTTP | No              | Yes                 |

## Configuration

### Connections - Ranges 1.0.0.X, 1.1.0.X & 1.2.0.X

This connector uses a virtual connection and does not require any input during element creation.

Note, however, that the connector uses HTTPS connectivity that must be configured after element creation. On the General page, you will need to configure parameters such as the authentication token.

### Connections - Range 1.2.1.X

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device.
- **Device address**: The device address (default: *ByPassProxy*).

To set up the connection, after element creation, enter a valid bearer token on the **General** page. If the token is valid, the Authorization State will change to "Authorized".

## How to Use

### General

The General page contains the main connection data. On this page, you will have to specify the **OpenShift URL/IP Address**, the **username** and the **password**. Openshift uses the OAuth authentication method, based on Bearer tokens. By default, the token is retrieved from the implemented login mechanism, but you can insert your own token. Each Bearer token is valid for 24 hours and renewed accordingly. You can also verify the authorization state here, which refers to the login success. With the refresh data button, you can manually trigger the immediate polling of all data.

By default, the login is done at startup and renewed every 12 hours.

From the General page, you can also access the main information in a table. To do so, click the page buttons to the **Nodes**, **PODs**, and **Containers** subpages.

### Namespaces

The namespaces list, which originates from Kubernetes, is listed on this page in a table. This includes the namespace name, labels, status, age, creation timestamp, resource version, and self link.

### Nodes

This page contains a list of nodes organized by namespace in a tree control fashion. From each node, you can navigate to the respective Conditions, Stats, and PODs.

### PODs

This page contains a list of PODs organized by namespace in a tree control fashion. For every POD, you can see the Containers, Conditions, and Volumes, among others.

### Services

This page displays all services, organized per namespace, also shown in a tree control fashion.

### Replica Controllers

On this page, replica controllers are listed and organized per namespace in a tree control structure.

> [!NOTE]
> The pages listed below are exported to SRM DVEs and not visible in the main element.

### Node Info

This page shows all information available regarding one specific node.

### POD Info

The POD Info page also shows all the information available regarding one specific POD.

### POD Container Info

The POD Container Info page display all data about the selected container.

### Node Stats Info

The Node Stats Info page is shown in the same element as the Node Info page. It shows all real-time statistics regarding the chosen node.

### POD Stats Info

The POD Stats Info page presents all real-time statistics for the referred node. It is shown for the same DVE as the POD Info page.

### POD Container Stats Info

The POD Container Stats Info page displays the real-time statistics for the selected container. This page is enclosed with the POD Container Info.
