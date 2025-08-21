---
uid: Connector_help_Roeselare_Classification_Manager_Technical
---

# Roeselare Classification Manager

## About

Vehicles on which cameras are mounted are used to take captures/pictures of the traffic signs in the city. These are called "Rides". The connector collects the rides data and the captured detections. It collects detections that are not classified, i.e. instances where the meaning and category of the traffic sign cannot be interpreted. The connector then forwards the unclassified detections to the Classifier module/API endpoint.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The URL of the classifier API endpoint to which the unclassified detections have to be sent.
- **IP port**: The IP port of the API endpoint (default: *443*).

### Initialization

After a new element is created, provide the API **Bearer Token** on the **General** page, which is used to authenticate the HTTP POST action when sending the request jobs to the classifier.

## How to use

On the **General** page, configure the parameters that are used to construct the request jobs that will be sent to the classifier.

- **Base URL**: The location of the frames from which the detections are extracted.

- **Maximum Requests**: The maximum number of detections that should be included in one job. The specified number of detections will be bundled together and forwarded to the classifier once. Detections from the same ride are bundled together. If the number of detections in one ride is greater than the configured maximum requests, the detections will be bundled in subsets and forwarded to the classifier.

- **Classification Wait Time**: Determines how long the connector will wait to start sending the requests to the classifier after polling the unclassified detections.

- **Maximum Job Retries**: If sending classification requests to the classifier fails, this setting determines how many times the connector will try to send the requests.
