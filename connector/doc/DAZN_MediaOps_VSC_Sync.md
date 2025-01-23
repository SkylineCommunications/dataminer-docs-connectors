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

This connector is designed to work with the DZN-UDAPI-AVOS Automation script.

In the background, there are two buffers: pending and live requests. When a pending request changes to a live request, the connector first checks if it is a patch request. If it is, the data of the patch request will be used to send a get request first, because the API expects the "LastModified" tag to be the same. For this reason, this "LastModified" value is retrieved first and then used to complete the patch request and transmit it.

# Incoming requests

## Register Livestream

**POST**  
e.g.:[https://&lt;Hostname&gt;/api/custom/livestreams/registrations?livestreamId=6gr51t8jdhl7119l9w23ljtnc](https://&lt;Hostname&gt;/api/custom/livestreams/registrations?livestreamId=6gr51t8jdhl7119l9w23ljtnc)

**Body**
```json
{
"contentMediaId": "a98711a1-ab43-4e76-8491-5ff413ffFFF0"
}
```

This will register the livestream in DOM ((slc)event_management/ LiveStream ContentMedia Link Registrations)

When the MediaContent and Livestream ID match we will update the record.

Note: MediaContent and Livestream ID don’t match we will return an error: 400 "Content Media Already Registered”.

Note: there must be an event with the livestream must exist and it mist have a job otherwise we will return the error 404 "Event has no Job attached".

Note: if we can’t find an event with the livestream id we will return 404 Livestream not found".

Note that the livestream will be looked up in DOM, looking into the Events, searching for an event with that livestream attached. Because we need a link between the ContentMedia, livestream and Event.

## Unregister

**DELETE**
e.g.:[https://&lt;HOSTNAME&gt;/api/custom/livestreams/registrations?livestreamId=6gr51t8jdhl7119l9w23ljtnc&contentMediaId=a98711a1-ab43-4e76-8491-5ff413ffFFF0](https://&lt;HOSTNAME&gt;/api/custom/livestreams/registrations?livestreamId=6gr51t8jdhl7119l9w23ljtnc&contentMediaId=a98711a1-ab43-4e76-8491-5ff413ffFFF0)

This will soft delete the registration in DOM ((slc)event_management/ LiveStream ContentMedia Link Registrations)

## List Active Livestreams

**GET**

e.g.: [https://&lt;HOSTNAME&gt;/api/custom/livestreams/registrations/active](https://&lt;HOSTNAME&gt;/api/custom/livestreams/registrations/active)

This will filter all the non soft deleted registers in DOM ((slc)event_management/ LiveStream ContentMedia Link Registrations) and respond them back.

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

**GET**  

e.g.: [https://&lt;HOSTNAME&gt;/api/custom/livestreams/update?contentMediaId=a98711a1-ab43-4e76-8491-5ff413ff63f0](https://&lt;HOSTNAME&gt;/api/custom/livestreams/update?contentMediaId=a98711a1-ab43-4e76-8491-5ff413ff63f0)

This request request dataminer to send an update to AVOS with 2 PATCH messages (Patch ContentMedia/live/{id} and a Patch ContentMedia/live/{id}/technicalMedia/sourceMedia/

The DZN-UDAPI-AVOS script will pick this up and forward this request to the DAZN MediaOps VSC Sync connector

# Outgoing

Via connector DAZN MediaOps VSC Sync.

UDAPI-AVOS detects the recuest

## Get ContentMedia/live/{id}

**GET**

e.g.:[https:// &lt;HOSTNAME&gt;/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472](https://avos.metadata.dazn-stage.com/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472)

## Patch ContentMedia/live/{id}

**PATCH**
e.g.: [https:// &lt;HOSTNAME&gt;/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472](https://avos.metadata.dazn-stage.com/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472)

**Body**  
```json
{
  "**bookingPreKOStartTime**": "0001-01-01T00:00:00",
  "**bookingStartTime**": "0001-01-01T00:00:00",
  "**eventEndTime**": "0001-01-01T00:00:00",
  "**lastModified**": "0001-01-01T00:00:00"
}
```

Before the patch can be sent a GET ContentMedia/live/{id} must be sent to receive the field “LastModified”, this field bust be copied to the PATCH request Body to the AVOS API accepts the patch.

**AVOS API fields / Dataminer DOM mapping**

**BookingPreKOStartTime** = eventsInstance.LiveStream.First().PreKoUTC  
<br/>**BookingStartTime** = jobInstance.JobInfo.JobStart  
<br/>**EventEndTIme** = eventsInstance.EventInfo.EventEnd;  
<br/>**lastModified** : From GET request id this Content Media ID

## Patch ContentMedia/live/{id}/technicalMedia/sourceMedia/

**PATCH**
e.g.: [https://&lt;HOSTNAME&gt;/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472/technicalMedia/sourceMedia/](https://&lt;HOSTNAME&gt;/external/contentMedia/live/0b26a1d5-b490-4167-b370-c39fa5224472/technicalMedia/sourceMedia/)

**Body**  
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


Before the patch can be sent a GET ContentMedia/live/{id} must be sent to receive the field “LastModified”, this field bust be copied to the PATCH request Body to the AVOS API accepts the patch.

**AVOS API fields / Dataminer DOM mapping**

**heSourceAddresses:** in the JobInstance we have Nodes, these nodes can be of the NodeTypeResouces, these resources can have the DMHE property if they are then they will be added in the correct sorting.

**txEventType: livestream.Txeventtype**

**lastModified** : From GET request id this Content Media ID
