---
uid: Connector_help_Generic_KAFKA_Consumer_Technical
---

# Generic KAFKA Consumer - Technical Reference

## About

This connector uses a virtual connection that interfaces with Kafka using a Confluent .NET client. It polls one or more configured topics via one or more brokers defined on the element, buffers received messages, and offloads them to a compressed GZ file containing JSON data per topic. This file can then be ingested and used in other workflows by connectors, Automation scripts, etc.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation. All connectivity (broker addresses, ports, authentication) is configured after element creation, from the element's Brokers, Authentication, OAuth, and Schema Registry pages.

### Initialization

When you have created an element, you still need to configure several things based on your Kafka system.

#### Mandatory configuration

Add one or more **brokers** to the element:

1. Go to the **Brokers** page of the element.
1. Right-click the table and select **Add** in the context menu.
1. Enter the bootstrap server, port, and an alias for the broker.

Add one or more **topics** to the element:

1. Go to the **Topics** page of the element.
1. Right-click the table and select **Add** in the context menu.
1. Specify the **Topic name** and the following settings:
   - **Subscription Interval**: Determines how frequently the topic is polled. Default: 5 minutes.
   - **Poll Duration**: Used in the Kafka consume call to determine how long it polls before the call ends. Default: 1 minute.

#### Optional configuration

To configure authentication, go to the **Authentication** page of the element and fill out the parameters with the necessary information. The following authentication methods are supported:

- **SSL**
  - SSL Certificate
  - SSL CA with Public/Private Key
- **SASL SSL**
  - Supported mechanisms: Plain, SCRAM 256, SCRAM 512, OAuth Bearer, SASL Credentials
  - Same SSL Certificate authentication
- **None**

To configure OAuth Bearer authentication, go to the **OAuth** page of the element. See [OAuth Bearer configuration](#oauth-bearer-configuration) below for details.

To consume Avro messages, go to the **Schema Registry** page and configure the Confluent Schema Registry connection. See [Schema Registry](#schema-registry) below for details.

To configure the data format, go to the **Consumer** page of the element and update the **Data Format** parameter to the message format used on the Kafka broker. The following formats are supported:

- **String**
- **AVRO**

> [!NOTE]
> If AVRO messages are consumed, the exported messages need to be deserialized using the AVRO schema in an external method.

## How to use

After the initialization detailed above is performed, on a timer, the connector retrieves data for the specified topic(s) from the configured broker(s) via the Confluent Kafka client. This data is offloaded to the directory path specified in the **Export Directory** parameter, as a GZ file per topic. These GZ files can then be used in other workflows by connectors, Automation scripts, etc.

The following settings are often of use:

- **Brokers**: Via the right-click menu of the Brokers table, you can add, edit, or delete brokers. Multiple delete is possible by highlighting multiple rows and selecting the delete option in the context menu.
- **Topics**: Via the right-click menu of the Topics table, you can add, edit, or delete topics. Multiple delete is possible by highlighting multiple rows and selecting the delete option in the context menu.
- **Consumer & Authentication**: These pages allow you to configure the Kafka consumer settings.
  Note: Double-check your Kafka settings against the parameters on these pages, because these parameters directly affect the polling of data from Kafka.
- **Export Settings**: These settings allow you to toggle the export functionality of the connector and choose whether a local or remote directory should be used.
  Note: For the remote file handling feature to work, you must enter a local directory in the **Local Export Directory**. The connector writes to this location and then copies it over to the remote location. You must also provide the credentials for the system in the **System Credentials** section and enter the path to the remote directory in the **Export Directory** parameter. The path must be shared/accessible.
- **Housekeeping Settings**: Configure file retention on the **Configuration** page so exported GZ files are automatically cleaned up after the configured retention period.
- **Debug**: To reduce file-reading latency, enable the **Enable Interapp** parameter and specify the DMA ID/Element ID that will receive a notification as soon as a new Kafka export file is available for processing. Additional logging of the Kafka connection is also available when the **Kafka Logging** parameter is enabled; this logging is written to the element logging with the information level set to 1.

### Monitoring

- The **General** page shows the **Kafka Connection Status** parameter (Error / OK / No Data), which is monitored and alarmed.
- The **Polling Buffer** page shows a visual representation of the buffer-to-export pipeline: one row per in-flight or recently processed topic poll, with its status, received time, completed time, and topic partitions. Use this page to verify that topics are being consumed and exported as expected.

## Schema Registry

When consuming **AVRO** messages (Consumer page, **Data Format** = AVRO), configure the Confluent Schema Registry connection on the **Schema Registry** page:

- **Schema Registry URL**: URL of the Confluent Schema Registry used to decode AVRO messages.
- **Schema Registry Username** / **Schema Registry Password**: Credentials for Schema Registry basic authentication, if required.
- **Schema Registry Bearer Auth Issuer Endpoint URL**: OAuth/OIDC issuer token endpoint URL for Schema Registry bearer authentication (`bearer.auth.issuer.endpoint.url`).
- **Schema Registry Bearer Auth Client ID** / **Schema Registry Bearer Auth Client Secret**: Client credentials for Schema Registry bearer authentication (`bearer.auth.client.id` / `bearer.auth.client.secret`).

## OAuth Bearer configuration

When the **SASL Mechanism** on the **Authentication** page is set to **OAuth Bearer**, configure the parameters on the dedicated **OAuth** page. More information about these parameters can be found below.

### OAuth Bearer settings

These parameters control the general OAuth Bearer behavior:

- **SASL OAuth Bearer Method**: The token retrieval method. Select **Default** for a static token or **OIDC** for OpenID Connect token endpoint flow.
- **Enable SASL OAuth Bearer JWT**: Enables use of an unsigned JWT. Should only be used for testing purposes.
- **SASL OAuth Bearer Client ID**: The client ID used for OAuth Bearer authentication.
- **SASL OAuth Bearer Client Secret**: The client secret used for OAuth Bearer authentication.
- **SASL OAuth Bearer Scope**: The client-credentials scope requested for the token.
- **SASL OAuth Bearer Extensions**: Additional key=value pairs passed to the broker during authentication.
- **SASL OAuth Bearer Token Endpoint URL**: The OAuth/OIDC issuer token endpoint URL used when the method is set to **OIDC**.
- **SASL OAuth Bearer Grant Type**: The OAuth grant type. Choose **Client Credentials** for service-to-service authentication or **JWT Bearer** for assertion-based flows.
- **SASL OAuth Bearer Metadata Authentication Type**: The authentication type used when fetching OIDC metadata from the broker. Set to **Azure IMDS** when running on Azure infrastructure.

### JWT assertion

These parameters are used when the grant type is set to **JWT Bearer** and control how the JWT assertion is built and signed:

- **SASL OAuth Bearer Assertion Algorithm**: The algorithm used to sign the JWT assertion (e.g., RS256, ES512).
- **SASL OAuth Bearer Assertion Private Key File**: Path to the PEM file containing the private key used to sign the assertion.
- **SASL OAuth Bearer Assertion Private Key Passphrase**: Passphrase protecting the private key file, if applicable.
- **SASL OAuth Bearer Assertion Private Key PEM**: PEM-encoded private key provided inline as an alternative to specifying a file path.
- **SASL OAuth Bearer Assertion File**: Path to a file containing a pre-built JWT assertion, used instead of having the connector build one.
- **SASL OAuth Bearer Assertion Claim Aud**: The audience (`aud`) claim value embedded in the JWT assertion.
- **SASL OAuth Bearer Assertion Claim Exp Seconds**: Lifetime of the JWT assertion in seconds from the time it is created.
- **SASL OAuth Bearer Assertion Claim Iss**: The issuer (`iss`) claim value embedded in the JWT assertion.
- **SASL OAuth Bearer Assertion Claim JTI Include**: When enabled, a unique JWT ID (`jti`) claim is added to the assertion to prevent replay attacks.
- **SASL OAuth Bearer Assertion Claim Nbf Seconds**: The not-before (`nbf`) offset in seconds relative to the current time.
- **SASL OAuth Bearer Assertion Claim Sub**: The subject (`sub`) claim value embedded in the JWT assertion.
- **SASL OAuth Bearer Assertion JWT Template File**: Path to a JSON file containing additional claim templates merged into the assertion.
