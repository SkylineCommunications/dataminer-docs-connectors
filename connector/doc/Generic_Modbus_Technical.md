---
uid: Connector_help_Generic_Modbus_Technical
---

# Generic Modbus

## About

The Generic Modbus connector provides standardized communication with Modbus-compliant devices using the Modbus TCP/IP protocol. This connector supports Function Code 3 (Read Holding Registers) for reading data and Function Codes 6 and 16 for writing single or multiple registers. The connector is configuration-driven, allowing operators to define which registers to poll.

Important limitations:

- Only Holding Registers are supported for reading and writing operations.
- Coils, Discrete Inputs, and Input Registers are not supported by this connector.

> [!NOTE]
> Consult your device's Modbus register map documentation to identify the correct register addresses and data types.

## Configuration

### Connections

#### TCP/IP Main Connection

This connector uses a TCP/IP connection and requires the following input during element creation:

- **IP address/host**: The polling IP address of the Modbus device.
- **IP port**: The IP port of the destination (default: 502).

### Initialization

After creating the element, navigate to the Configuration page to set up the registers you want to monitor.

### Register Configuration

The Register Configuration table on the Configuration page is the heart of this connector. Each row defines a register or group of registers to poll from your Modbus device. To add a new register to monitor, right-click anywhere in the table and select "Add new row" in the context menu. Then, fill in the required parameters:

- Description
- Type (unsigned integer, signed integer, bits, text)
- Register Number

> [!NOTE]
> **This connector uses 0-based register addressing**.
> However, device manufacturers often use different addressing conventions in their documentation:
>
> - **0-based addressing**: If your manual shows register 0-65535, use the address **as-is**.
> - **1-based addressing**: If your manual shows register 1-65536, **subtract 1**.
> - **40001-based addressing**: If your manual shows 40001-49999 (Holding Register notation), **subtract 40001**.

### Configuration Parameters

Each row in the Register Configuration table has the following parameters:

- **Description**: A user-friendly name for this register. This will appear in the Register Values table.
- **Type**: The data type of the register. Possible values: unsigned integer, signed integer, bits, text.
- **Register Number**: The 0-based Modbus register address (0-65535). Apply offset conversion if your documentation uses 1-based or 40001-based addressing.
- **Command**: Hidden parameter representing the hexadecimal Modbus command to read this register. The string is generated based on the configuration parameters.
- **Transaction Identifier**: Unique generated identifier, also used to link to the Register Values table.
- **Function Code**: Currently only Read Holding Registers [FC3] is supported for reading operations.
- **Number of Registers**: How many consecutive registers to read. 1 register = 16 bits (2 bytes). For integers, each register is one number. For text data, specify enough registers to hold the text (1 register = 2 bytes).
- **Slave Identifier**: The Modbus slave ID of the target device (1-255). Default is 1. If you have multiple devices on the same bus, each must have a unique slave ID.
- **Unit**: The unit of measurement for numeric values (optional). Used for display purposes only.
- **Factor**: Multiplication factor for numeric values. Default is 1.0.

## How to use

### General Page

The Register Values table displays data for all configured registers:

- **Description**: The user-defined register name from the configuration.
- **Transaction Identifier**: Unique identifier linking to the configuration table.
- **Register Number**: The Modbus register address.
- **Value (Numeric)**: Numerical value (for Integer types), with factor applied. **Editable**: Click to write a new value to the device.
- **Value (Text/Numerics)**: Text representation or semicolon-separated values for multi-register integer reads. **Editable**: Click to write values back to the device.
- **Value (Bits)**: Binary representation for bit-type registers (semicolon-separated). **Editable**: Click to modify individual bits and write back.
- **Unit**: Unit of measurement.
- **Timestamp**: Date and time of the last successful read or write operation.
- **Exception**: Displays any Modbus error codes or communication failures.

#### Writing Values to Device

To modify a register value on the Modbus device:

1. Locate the register in the Register Values table.
2. Click in the appropriate value column (Numeric, Text, or Bits).
3. Enter the new value in the same format as displayed.
4. Press Enter to send the write command to the device.
5. The connector will automatically use:
   - Function Code 6 for single register writes
   - Function Code 16 for multiple register writes (text or multi-register numerics)
6. Upon successful write, the Timestamp column updates to reflect the write operation.

### Configuration Page

The Register Configuration table allows you to:

- **Use the context menu**: Right-click anywhere in the table to add a new row, delete selected rows, or clear the entire table.
- **Modify existing configuration**: Click cells to edit parameters. Changes are applied immediately and trigger a new poll.

> [!IMPORTANT]
> Changes to the configuration table trigger an immediate poll of the affected register. The timer continues to poll all configured registers at the specified interval (default: 30 seconds).

> [!NOTE]
> **Polling Behavior**
>
> - The connector iterates through all rows in the Register Configuration table.
> - Each register is polled sequentially.
> - Default polling interval: 30 seconds