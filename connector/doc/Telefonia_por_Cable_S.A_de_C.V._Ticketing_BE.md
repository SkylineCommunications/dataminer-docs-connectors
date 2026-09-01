---
uid: Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_BE
---

# Telefonia por Cable S.A de C.V. Ticketing BE

## About

The Telefonia por Cable S.A de C.V. Ticketing BE connector automates the trouble-ticket workflow
between DataMiner and Telefonia por Cable S.A de C.V.'s (Sky Cable) **Cherwell** ticketing platform
and **SFyC** work-order (OT) system. It receives ticket entities from other DataMiner elements over
InterApp, checks Cherwell for an existing ticket before creating a duplicate, creates a new ticket or
adds a note to an existing one, creates the corresponding work order (OT), and links the OT number
back to the Cherwell ticket — all without manual operator intervention.

## Key Features

- **Automatic ticket deduplication**: searches Cherwell (by FDL and SNR) for an existing ticket
  before creating a new one, avoiding duplicate tickets for the same entity.

- **End-to-end ticket lifecycle automation**: drives a ticket entity all the way from "received"
  through ticket creation/note-adding, OT creation, and OT linkage to "completed", exposed as a
  clear per-row status in the `Tickets` overview table.

- **Configurable retries**: automatically retries a failed processing step up to a configurable
  maximum before marking the ticket as an error, with details available for troubleshooting.

- **Batch processing controls**: configurable maximum tickets per request and automatic/manual
  cleanup of completed or expired rows via a configurable retention time.

- **InterApp-driven intake**: integrates with upstream DataMiner elements/scripts that raise ticket
  entities via InterApp, requiring no manual data entry.

## Use Cases

### Avoiding duplicate trouble tickets

**Challenge**: Multiple alarms for the same underlying issue can result in duplicate tickets being
raised on the Cherwell platform, creating noise and confusion for operations teams.

**Solution**: The connector searches Cherwell for an existing open ticket matching the entity before
creating a new one, adding a note to the existing ticket instead when found.

**Benefit**: Operations teams see a single, up-to-date ticket per issue instead of a growing pile of
duplicates.

### Linking work orders to tickets automatically

**Challenge**: Once a customer issue requires field work, someone has to manually create a work
order (OT) in SFyC and remember to link it back to the originating Cherwell ticket.

**Solution**: The connector automatically creates the OT on SFyC once a ticket is created, and
updates the Cherwell ticket with the resulting OT number.

**Benefit**: Field teams and support agents always have an up-to-date, correctly linked record
between the ticket and the work order, without manual follow-up.

### Hands-off ticket processing at scale

**Challenge**: Manually processing every alarm into a ticket does not scale as alarm volume grows.

**Solution**: Ticket entities are queued and processed automatically, with configurable batch size,
retry count, and retention time so the pipeline can be tuned to the customer's volume.

**Benefit**: NOC operators only need to intervene on tickets that reach an error state, instead of
manually creating every ticket.

## Technical Reference

### Prerequisites

- **Cherwell platform access** (`skylineApi` HTTP endpoint) is required to search, create, and
  update tickets.

- **SFyC OT (work order) platform access** (via the same `skylineApi` HTTP endpoint) is required to
  create work orders linked to tickets.

- **An upstream DataMiner element or script** capable of sending ticket entities to this connector
  via InterApp is required to feed the pipeline.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_BE_Technical).

