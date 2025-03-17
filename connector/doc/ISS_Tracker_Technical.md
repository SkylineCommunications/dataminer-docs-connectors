---
uid: Connector_help_ISS_Tracker_Technical
keywords: ISS, International Space Station, Tracker
---
# ISS Tracker

## About
The ISS Tracker connector provides real-time tracking and monitoring of the International Space Station (ISS). This connector integrates live positional data, crew information, and data retrieval status, enabling users to access critical information efficiently.

The ISS Tracker module offers seamless integration with DataMiner, allowing for intuitive visualization of ISS metrics, including latitude, longitude, and current crew details. This real-time feed is essential for monitoring ISS movements and operational insights.

## Configuration

### Connections

#### HTTP Connection – ISS Tracker API
This connector uses an HTTP connection and requires the following input during element creation:

**HTTP CONNECTION:**
- **IP address/host:** `api.open-notify.org` (Public API for real-time ISS position)
- **IP port:** `80` (Default HTTP port)
- **Bus address:** Not required

### Stream Viewer 
DataMiner's Stream Viewer tool can be used to monitor HTTP traffic between the ISS Tracker connector and the external data source. The connector establishes two HTTP sessions to retrieve ISS tracking and crew information. If both sessions return a status OK with the expected response body, the connection is considered operational. Otherwise, further troubleshooting may be required to resolve connectivity or API response issues. 

Additionally, there is a parameter that displays the connectivity status. It can display status messages that include:
- **OK**
- **Error**
- **API Not Responding**

If any message other than OK appears, the Stream Viewer should be checked.

## Initialization
No additional configuration is required after element creation. The connector automatically retrieves data from the ISS API at regular intervals.

## General Functionality
The ISS Tracker connector retrieves real-time data from the API and displays it into DataMiner. The following key metrics are available:
- **Latitude & Longitude:** The exact position of the ISS at any given time.
- **Crew Information:** The current astronauts aboard the ISS and other craft.

Users can visualize ISS movement and view historical data for analysis.

## Data Retrieval Process
1. The connector sends an HTTP GET request to `api.open-notify.org`.
2. The API responds with a JSON object containing latitude, longitude, and timestamp.
3. Data is parsed and displayed in a DataMiner Element.

## Notes
- The connector is dependent on the availability of the Open Notify API.
- Future updates may include additional space station tracking.
