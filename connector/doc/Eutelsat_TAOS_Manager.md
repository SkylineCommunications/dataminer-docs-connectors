---
uid: Connector_help_Eutelsat_TAOS_Manager
---

# Eutelsat TAOS Manager

## About

The **Eutelsat TAOS Manager** connector retrieves satellite transponder telemetry from Eutelsat's TAOS (Telemetry Acquisition and Operations System) MySQL databases. It polls redundant databases on a configurable schedule, merges results based on validity and recency, and presents consolidated per-transponder telemetry.

An **Association Table** maps each transponder to its TM_IDs, allowing flexible per-transponder configuration. Custom alarm thresholds with Major/Critical severity offsets provide fine-grained alarming control.

### Version Info

| Range   | Description                   | Based on | System Impact                                                                          |
|---------|-------------------------------|----------|----------------------------------------------------------------------------------------|
| 1.0.0.x | Standard Eutelsat satellites  | -        | -                                                                                      |
| 1.0.1.x | Quantum satellite support     | 1.0.0.27 | High — Association Table columns differ; telemetry pages reorganized by equipment type |

## Configuration

### Connections

This is a **virtual** connector. No connections are configured in the element wizard.

Database connections are configured on the **Setup** page after element creation.

### Initialization

1. Create an element using this connector.
2. On the **Setup** page, enter the **Satellite ID** matching the target satellite in the TAOS database.
3. Configure the database connection parameters (address, port, name, username, password) for each database source.
4. On the **Configuration** page, populate the **Association Table** to map transponders to TM_IDs.
5. The connector begins polling automatically on a 20-second cycle.

## How to use

This connector is available in two version ranges depending on the **satellite type**.

### **Range 1.0.0.x**

Use this range for **standard Eutelsat satellites**.

Telemetry is organized by **parameter type**, such as:

- TWTA / Mute / Mode
- Power
- Gain Step
- Voltage / Current
- Coverage

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Eutelsat_TAOS_Manager_1_0_0_x_Technical).

---

### **Range 1.0.1.x**

Use this range for **Eutelsat Quantum satellites**.

Telemetry is organized by **equipment type**, including:

- SCACE
- AIDA
- MPM
- RASE
- IRASE
- DRA
- BFN

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Eutelsat_TAOS_Manager_1_0_1_x_Technical).

---

> [!IMPORTANT]
> The two ranges are **not interchangeable**. The Association Table schema and telemetry page layout differ between ranges. Select the range that matches your satellite type when creating the element.

## Notes

- The connector uses the **MySql.Data** NuGet package (v9.0.0) for database connectivity.
- The polling timer has a random initial start offset (0–30 s) to prevent multiple elements from querying the database simultaneously.
