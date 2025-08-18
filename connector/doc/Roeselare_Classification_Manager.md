---
uid: Connector_help_Roeselare_Classification_Manager
---

# Roeselare Classification Manager

## About

Vehicles on which cameras are mounted are used to take captures/pictures of the traffic signs in the city. These are called Rides. The connector collects the rides data and the captured detections. It collects detection which are not classified. By classification, it means interpreting the meaning and category of the traffic sign. The connector then forwards the unclassified detections to the Classifier module/API endpoint.

## Key Features
- **Classification**: Collects rides and detections which are not classified and sends the detections to the classifier for classification.

## Use Cases

### Use Case 1

**Challenge**: Keeping track of what traffic signs are installed in the city and where.

**Solution**: This connector facilitates with the collection and identification of which traffic signs are interpreted and forwarding the unclassified detections to the classifier.

**Benefit**: Clear overview of classified detections or interpreted signs.

## Technical Reference

### Prerequisites

- **Minimum DMA Version 10.4.1** is needed for the connector to properly function.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref: Connector_help_Roeselare_Classification_Manager_Technical).
