---
uid: Connector_help_DAZN_MediaOps_VSC_Sync
---

# DAZN MediaOps VSC Sync

This connector will send HTTP POST messages to the AVOS system to keep it up to date with changes in DataMiner.

## About

### Version Info

| Range              | Features                                       | Based on | System Impact |
|--------------------|------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Handling of job updates.<br>AVOS force update. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | TBD                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

On the **Setup** page, fill in the API token.

## How to use

When a job is created, an InterApp call is performed on the connector. The connector will add this call to an internal buffer and send this request over to AVOS. When the POST fails, it will be added into the Failed Post Requests table. Every 10 seconds, this will be retried. Records in this table also have a maximum age. If they exceed this age, they are removed.

### Notes

This connector is designed to work with the DZN-UDAPI-AVOS automation script.

In the background, there are two buffers: pending and live requests. When a pending request changes to a live request, the connector first checks if it is a patch request. If it is, the data of the patch request will be used to send a get request first, because the API expects the "LastModified" tag to be the same. For this reason, this "LastModified" value is retrieved first and then used to complete the patch request and transmit it.

# Incoming requests

## Register Livestream

### POST

For example: `https://<Hostname>/api/custom/livestreams/registrations?livestreamId=6gr51t8jdhl7119l9w23ljtnc`

### Body

```json
{
"contentMediaId": "a98711a1-ab43-4e76-8491-5ff413ffFFF0"
}
```

This will register the livestream in DOM ((slc)event_management / LiveStream ContentMedia Link Registrations), depending on whether the MediaContent and Livestream ID match, and on whether a link can be found in the DOM events between the ContentMedia, livestream, and event:

- If the MediaContent and Livestream ID match, the record will be updated.
- If these do not match, the following error will be returned: 400 "Content Media Already Registered”.
- If no event with the livestream ID is found, the following error will be returned: 404 "Livestream not found".
- If an event with the livestream ID is found, but it does not have a job, the following error will be returned: 404 "Event has no Job attached".

## Unregister

### DELETE

For example: `https://<HOSTNAME>/api/custom/livestreams/registrations?livestreamId=6gr51t8jdhl7119l9w23ljtnc&contentMediaId=a98711a1-ab43-4e76-8491-5ff413ffFFF0`

This will soft-delete the registration in DOM ((slc)event_management / LiveStream ContentMedia Link Registrations)

## List Active Livestreams

### GET

For example: `https://<HOSTNAME>/api/custom/livestreams/registrations/active`

This will filter out all the non-soft-deleted registers in DOM ((slc)event_management / LiveStream ContentMedia Link Registrations) and include them in the response.

Response body:

```json
{
"activeLivestreams": 
 [
   { "livestreamId": "6gr51t8jdhl7", "contentMediaId": "a98711a1-ab43-4e76-8491-5ff413ff63f0" },
   { "livestreamId": "87r51t8jdjt12", "contentMediaId": "abc711a1-ab43-4e76-8491-5ff413ff6xyz" }
 ]
}
```

## Update ContentMedia

### GET

For example: `https://<HOSTNAME>/api/custom/livestreams/update?contentMediaId=a98711a1-ab43-4e76-8491-5ff413ff63f0`

This request asks DataMiner to send an update to AVOS with 2 PATCH messages (`Patch ContentMedia/live/{id}` and a `Patch ContentMedia/live/{id}/technicalMedia/sourceMedia/`)

The DZN-UDAPI-AVOS script will pick this up and forward this request to the DAZN MediaOps VSC Sync connector.

## Outgoing

Via connector DAZN MediaOps VSC Sync.

UDAPI-AVOS detects the request.

## Get ContentMedia/live/{id}

### GET

For example: `https://<HOSTNAME>/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472`

## Patch ContentMedia/live/{id}

### PATCH

For example: `https://<HOSTNAME>/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472`

### Body

```json
{
  "**bookingPreKOStartTime**": "0001-01-01T00:00:00",
  "**bookingStartTime**": "0001-01-01T00:00:00",
  "**eventEndTime**": "0001-01-01T00:00:00",
  "**lastModified**": "0001-01-01T00:00:00"
}
```

Before the patch can be sent, a `GET ContentMedia/live/{id}` must be sent to receive the field "LastModified". This field bust be copied to the PATCH request body so the AVOS API accepts the patch.

### AVOS API fields / DataMiner DOM mapping

- **BookingPreKOStartTime**: eventsInstance.LiveStream.First().PreKoUTC
- **BookingStartTime**: jobInstance.JobInfo.JobStart
- **EventEndTIme**: eventsInstance.EventInfo.EventEnd
- **lastModified**: From GET request ID, this Content Media ID

## Patch ContentMedia/live/{id}/technicalMedia/sourceMedia/

### PATCH

For example: `https://<HOSTNAME>/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472/technicalMedia/sourceMedia/`

### Body

```json
{
  "lastModified": "2025-01-23T12:34:56Z",
  "txEventType": "Update",
  "heSourceChannelId": "channel123",
  "heSourceAddresses": [
    {
      "destination": "http://example.com/destination1",
      "resources": [
        {
          "resource": "ResourceA",
          "order": 1,
          "sourceUri": "http://example.com/resourceA"
        },
        {
          "resource": "ResourceB",
          "order": 2,
          "sourceUri": "http://example.com/resourceB"
        }
      ]
    },
    {
      "destination": "http://example.com/destination2",
      "resources": [
        {
          "resource": "ResourceC",
          "order": 1,
          "sourceUri": "http://example.com/resourceC"
        }
      ]
    }
  ]
}
```

Before the patch can be sent, a `GET ContentMedia/live/{id}` must be sent to receive the field "LastModified". This field bust be copied to the PATCH request body so the AVOS API accepts the patch.

### AVOS API fields / DataMiner DOM mapping

- **heSourceAddresses**: In the job instance, there are nodes, which can be of the "resources" node type. These resources can have the DMHE property. If they do, they will be added with the correct sorting.
- **txEventType**: livestream.Txeventtype
- **lastModified**: From GET request ID, this Content Media ID.
