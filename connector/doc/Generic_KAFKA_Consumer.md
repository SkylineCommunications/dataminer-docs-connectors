---
uid: Connector_help_Generic_KAFKA_Consumer
---

# Generic KAFKA Consumer

## About

This connector uses a virtual connection that interfaces with KAFKA using a Confluent DLL that polls information for one or more topics via one or more brokers that can be defined in the DataMiner element.

The data retrieved from the API will be offloaded to a compressed GZ file with JSON data per topic. This file can then be ingested and used in other workflows by connectors, automation scripts, etc.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

When you have created an element, you still need to configure several things based on your KAFKA system.

#### Mandatory configuration

Add one or more **brokers** to the element:

1. Go to the **Broker** page of the element.

1. Right-click the table and select **Add** in the context menu.

1. Enter the information for the broker(s).

Add one or more **topics** to the element:

1. Go to the **Topics** page of the element.

1. Right-click the table and select **Add** in the context menu.

1. Specify the **Topic name** and the following settings:

   - **Subscription Interval**: Determines how frequently the topic will be polled. Default: 5 minutes.

   - **Poll Duration**: Will be used in the API call to determine how long it will poll before the call ends. Default: 1 minute.

#### Optional Configuration

To configure authentication, go to the **Authentication page** of the element and fill out the parameters with the necessary information.

To configure OAuth Bearer authentication, go to the **OAuth page** of the element. See [OAuth Bearer authentication](#oauth-bearer-authentication) for details.

## How to use

After the initialization detailed above is performed, based on a timer, the connector will retrieve data from the **API** for the specified **topic(s)**. This data will be offloaded to the directory path specified in the **Export Directory parameter** in a **GZ** file per topic. These GZ files can then be used in other workflows by connectors, automation scripts, etc.

The following settings are often of use:

- **Brokers**: Via the right-click menu of the Brokers table, you can add, edit, or delete brokers. Multiple delete is possible by highlighting multiple rows and selecting the delete option in the right-click menu.
- **Topics**: Via the right-click menu of the Topics table, you can add, edit, or delete topics. Multiple delete is possible by highlighting multiple rows and selecting the delete option in the context menu.
- **Consumer & Authentication**: These pages allow you to configure different settings for the Consumer element within the KAFKA API.
  Note: Double-check your KAFKA settings with the parameters on these pages, because these parameters can directly affect the polling of data from KAFKA.
- **Export Settings**: These settings allow you to toggle the export functionality of the connector and choose whether a local or remote directory should be used.
  Note: For the remote file handling feature to work, you must enter a local directory in the **Local Export Directory**. The connector will write to this location and then copy over to the remote location. You must also provide the credentials for the system in the **System Credentials** section and enter the path to the remote directory in the **Export Directory** parameter. The **path** **must be shared/accessible**.
- **Debug**: To reduce the file reading latency, enable the **Enable Interapp** parameter and specify the DMA ID/Element ID that will receive the message to immediately know a new Kafka file is available for processing. Additional Logging of the Kafka connection is also available when the **Kafka Logging** parameter is enabled. This additional logging will be written to the element logging with the information level set to 1.

## OAuth Bearer authentication

When the **SASL Mechanism** on the **Authentication** page is set to **OAuth Bearer**, configure the parameters on the dedicated **OAuth** page. You can find more information about these parameters below.

### OAuth Configuration

These parameters control the general OAuth Bearer behavior:

- **SASL OAuth Bearer Method**: The token retrieval method. Select **Default** for a static token or **OIDC** for OpenID Connect token endpoint flow.
- **Enable SASL OAuth Bearer Unsecure JWT**: Enables use of an unsigned JWT. Should only be used for testing purposes.
- **SASL OAuth Bearer Client ID**: The client ID used for OAuth Bearer authentication.
- **SASL OAuth Bearer Client Secret**: The client secret used for OAuth Bearer authentication.
- **SASL OAuth Bearer Scope**: The OAuth scope requested for the token.
- **SASL OAuth Bearer Extensions**: Additional key=value pairs passed to the broker during authentication.
- **SASL OAuth Bearer Token Endpoint URL**: The OAuth/OIDC token endpoint URL used when the method is set to **OIDC**.
- **SASL OAuth Bearer Grant Type**: The OAuth grant type. Choose **Client Credentials** for service-to-service authentication or **JWT Bearer** for assertion-based flows.
- **SASL OAuth Bearer Metadata Authentication Type**: The authentication type used when fetching OIDC metadata from the broker. Set to **Azure IMDS** when running on Azure infrastructure.

### JWT Assertion

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
