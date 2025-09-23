---
uid: Connector_help_SES_S.A._O3b_mPOWER_Technical
---

# SES S.A. O3b mPOWER

## About

The SES O3b mPOWER connector integrates live terminal data from the SES O3b mPOWER API into DataMiner. It retrieves terminal configuration, status, and key performance metrics by polling secure REST API endpoints, enabling operators to monitor and analyze their MEO services in real time.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTPS connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: `https://ses-n-brace.com`
- **IP port**: `443` (default)

### Initialization

When the element has been created, configure the credentials to connect to the SES O3b mPOWER API:

1. Set the following parameters on the **Configuration** page:
   - **Client ID**
   - **Username**
   - **Password**

2. Use the **Authenticate** button to manually initiate authentication.

When login is successful, an **Access Token** and **Refresh Token** are generated. The **Token Expiration** parameters will be updated automatically, and tokens are refreshed by the connector when needed.

## How to Use

The connector manages subscriptions to the SES API and automatically retrieves performance reports.

### Subscription Workflow

- Upon startup, the connector creates or reuses a subscription via the `nbrace/backend/nbrace-performance/api/mefApi/legato/streamingManagement/v1/subscription` endpoint.  
- It retrieves metrics using the `nbrace/backend/nbrace-performance/api/pm-reports/{subscriptionId}` endpoint, linked to the subscription ID.  
- Subscriptions are renewed automatically when expired.

### Pages Overview

#### General Page

This page displays overall counts of discovered terminals:

- **Total Terminals**
- **Active Terminals**
- **Inactive Terminals**

#### Terminals Metrics Page

This table is the core of the connector and is populated via the **pm-reports** endpoint.

Each row represents a terminal and includes:

- **Identifiers**:  
  - VNO ID  
  - Site Name  
  - Platform Type  
  - Customer ID  
  - Service ID  
  - Beam ID  
  - Contract ID  
  - Object Name (used as Terminal ID)

- **Performance Metrics**:  
  - Latency  
  - Forward/Return Packet Loss  
  - Forward/Return Throughput (Delivered, Utilization)  
  - Forward MIR, CIR, EIR  
  - Return CIR, EIR  
  - Forward/Return Signal Es/No  
  - Max Tx Power  
  - Forward/Return Volume (in MB, as provided by the API)

- **Geographic Location**:  
  - Latitude  
  - Longitude  
  - Altitude  
  - Heading  

- **Status**:  
  - Service Status  
  - Terminal Status  

All performance values are timestamped and stored in history sets for trending and analysis.

#### Configuration Page

The configuration page provides controls and settings:

- **Authentication Settings**: Client ID, Username, Password, Access Token Expiration, Refresh Token Expiration, Authentication Status.  
- **Subscription Information**: Subscription ID, Subscription Status.  
- **Pull Metrics Settings**:  
  - Pull Live Metrics Timer  
  - Maximum History Set Range – Maximum history applied per pull (default 7 days; prevents overloading DataMiner when catching up after downtime)  
  - Pull Live Metrics Status. 
- **Terminal Removal Settings**: Automatic Terminal Removal, Terminal Removal Period. 