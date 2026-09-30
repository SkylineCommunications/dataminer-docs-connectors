---
uid: Connector_help_Generic_Sun_Outage_Technical
description: "Configure the Generic Sun Outage connector, import earth stations and satellites, and review calculated outage predictions and their status."
---

# Generic Sun Outage

## About

The **Generic Sun Outage** connector predicts when the sun will interfere with the link between a satellite earth station and a geostationary satellite. For each earth station, it calculates:

- The **outage angle**: The angle between the sun and the satellite, seen from the dish, below which interference can occur. It is derived from the frequency band and the dish size: 11 / (frequency in GHz × dish size in m) + 0.25 degrees.
- The **current status**: *Active* while an outage window is in progress, *Inactive* otherwise.
- The **future outages**: Every window in which the sun is inside the outage angle, for the configured number of equinox cycles.

All times are in **UTC**. The results are best-effort estimates based on astronomical calculations, not measurements.

This page explains how to set up an element step by step, how to keep the earth stations and satellites up to date, and how to read the results.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

A new element starts empty. Follow these steps to get the first predictions:

1. Add the satellites that your fixed earth stations point at.

   See [Adding satellites](#adding-satellites).

1. If you have steerable antennas, register the protocol of their controller element.

   See [Registering a controller protocol for steerable antennas](#registering-a-controller-protocol-for-steerable-antennas).

1. Add the earth stations, either manually or by importing a provisioning file.

   See [Adding earth stations manually](#adding-earth-stations-manually) and [Importing earth stations and satellites from files](#importing-earth-stations-and-satellites-from-files).

1. Check the results on the **Earth Stations** and **Outages** pages.

   See [Reading the results](#reading-the-results).

> [!TIP]
> Always add the satellites before the fixed earth stations. A fixed earth station that refers to an unknown satellite is skipped until that satellite exists.

## How to Use

### Adding Satellites

Fixed earth stations need the orbital longitude of their satellite.

1. Go to the **Satellites** page.

1. Click **New Satellite**.

1. Enter the **Satellite Name**, the **Satellite Longitude**, and the **Satellite Longitude Units** (*deg E* or *deg W*).

   The satellite name must match the **Satellite** value of the earth stations exactly.

1. Click the button at the bottom of the page to add the satellite.

   The satellite will be added to the **Satellites Table**.

To remove a satellite, click the **Delete** button in its row.

### Registering a Controller Protocol for Steerable Antennas

A steerable antenna changes its orientation, so the connector reads the azimuth, elevation, and satellite from the element that controls the antenna (e.g., an antenna control unit or a modem). The controller element must be part of the same DataMiner System.

1. Go to the **ES Subscribers** page.

1. Click **New ES Subscriber**.

1. Enter the **Earth Station Subscriber Name** and **Earth Station Subscriber Version**, i.e., the protocol name and version of the controller element, exactly as used by that element.

1. Enter the **Earth Station Subscriber Azimuth PID**, **Earth Station Subscriber Elevation PID**, and **Earth Station Subscriber Satellite PID**, i.e., the parameter IDs in the controller protocol.

   These can be standalone parameters or columns of a table. If they are table columns, each steerable earth station must also specify the row key of the controller table (see **Earth Station Element Key** below).

1. Click the button at the bottom of the page to add the subscriber.

   The protocol will be listed in the **Earth Station Subscribers** table and will become available when you add steerable earth stations.

The connector monitors the controller element and its parameters. When the controller reports a new orientation, the outage values of the earth station are recalculated. When the controller element is stopped, is deleted, or cannot be reached, the orientation of the earth station is shown as *N/A*, and the connector retries automatically.

### Adding Earth Stations Manually

1. Go to the **Earth Stations** page.

1. Click **New Earth Station**.

1. Fill in the following fields:

   - **Earth Station Name**: A unique name. Other systems use this name to find the earth station.
   - **Earth Station Location**: A free-text location.
   - **Earth Station Latitude** and **Earth Station Latitude Units**: A positive value with *deg N* or *deg S*.
   - **Earth Station Longitude** and **Earth Station Longitude Units**: A positive value with *deg E* or *deg W*.
   - **Earth Station Frequency Band**: *C*, *X*, *Ku*, or *Ka*.
   - **Earth Station Dish Size**: The diameter of the dish in meters.
   - **Earth Station Type**: *Fixed* or *Steerable*.
   - **Earth Station Outage Overview**: *Enabled* to show the earth station in the tree view on the **Outage Overview** page.

1. Fill in the fields for the type of earth station:

   - For a **Fixed** earth station, select the **Earth Station Satellite**.
   - For a **Steerable** earth station, select the **Earth Station Protocol**, and enter the **Earth Station Element ID** of the controller element in the format *DataMinerID/ElementID* (e.g., *346/1203*). If the orientation parameters are table columns, also enter the **Earth Station Element Key**, i.e., the primary key of the row for this antenna in the controller table.

1. Click the button at the bottom of the page to add the earth station.

   The earth station will be added to the **Earth Station** table with **Origin** *Manual*, and its outages will be calculated.

To delete earth stations, select them in the **Earth Station** table, right-click, and select **Delete selected item(s)**. Deleting an earth station also deletes its predicted outages.

### Importing Earth Stations and Satellites from Files

For large networks, the connector can import earth stations and satellites from provisioning files. These files are typically generated by an inventory system or by another connector, such as **Skyline EPM Platform VSAT DSM SO**.

#### Step 1: Ensure the Import Settings Are Shown

The import settings are on pages that are hidden by default.

1. Go to the **Configuration** page.

1. In the **General Settings** section, set **Earth Stations Config Page** and **Satellites Config Page** to *Enabled*.

   The **ES Config** and **Sat Config** page buttons will open the import settings.

#### Step 2: Prepare the Files

Place the files in a folder on the DataMiner Agent that hosts the element. The default folder is `C:\Skyline DataMiner\Documents\Generic Sun Outage\PD`. When the folder is inside `C:\Skyline DataMiner\Documents`, file changes made by the connector are synchronized in the DataMiner System.

The file names must start with the ID of the DataMiner Agent that hosts the element:

- Earth stations: `<DataMinerID>_<any text>_ESO.csv`, e.g., `346_Stations_ESO.csv`.
- Satellites: `<DataMinerID>_<any text>_SO.csv`, e.g., `346_Satellites_SO.csv`.

If more than one file matches, only the first one is used. Keep only one earth stations file and one satellites file per folder.

The **satellites file** has a header line, followed by one satellite per line with the name and the longitude in degrees. Use a negative longitude for west and a point as the decimal separator:

```text
Name;Longitude
SES-4;-22
Intelsat 901;-18
Eutelsat 7B;7
```

The **earth stations file** is separated by semicolons and starts with this header line:

```text
Name;Location;Latitude;Longitude;Frequency_Band;Dish_Size;Type;Outage_Overview;Satellite;Subscriber;Version;Element_ID;Element_Key
```

The columns are read by position, so keep them in this order:

- **Name**: A unique earth station name. Required.
- **Location**: Free text. Required.
- **Latitude** and **Longitude**: Decimal degrees, negative for south and west.
- **Frequency_Band**: *C*, *X*, *Ku*, or *Ka*, or the center frequency in GHz (*3.95*, *7.5*, *11.825*, or *19*).
- **Dish_Size**: The dish diameter in meters. When this is empty or 0, the **Default Dish Size** is used (default: *1.20 m*).
- **Type**: *Fixed* or *Steerable*.
- **Outage_Overview**: *Enabled* or *Disabled*.
- **Satellite**: For fixed earth stations, the satellite name as listed in the **Satellites Table**.
- **Subscriber** and **Version**: For steerable earth stations, the protocol name and version registered on the **ES Subscribers** page. Use *NA* for fixed earth stations.
- **Element_ID**: For steerable earth stations, the controller element in the format *DataMinerID/ElementID*. Use *NA* for fixed earth stations.
- **Element_Key**: For steerable earth stations whose orientation parameters are table columns, the row key in the controller table. Otherwise, use *NA*.

For example:

```text
Name;Location;Latitude;Longitude;Frequency_Band;Dish_Size;Type;Outage_Overview;Satellite;Subscriber;Version;Element_ID;Element_Key
Site 001;Denver;39.74;-104.99;Ku;1.2;Fixed;Enabled;SES-4;NA;NA;NA;NA
Site 002;Madrid;40.42;-3.70;Ka;;Fixed;Disabled;Eutelsat 7B;NA;NA;NA;NA
Vessel 101;Norfolk;36.85;-76.29;Ku;2.4;Steerable;Enabled;;ACU Controller;1.0.0.1;346/1203;NA
```

The following rows are skipped:

- Rows without a **Name** or **Location**.
- Fixed earth stations whose satellite is not in the **Satellites Table**.
- Steerable earth stations without an **Element_ID**, or whose **Subscriber** and **Version** combination is not registered on the **ES Subscribers** page.

If the file does not contain a single valid earth station, the import stops and the table is left unchanged.

#### Step 3: Configure and Run the Import

Import the satellites first, and then the earth stations.

1. On the **Configuration** page, click **Sat Config**.

1. Set **Sat Import Path** to the folder that contains the files.

1. Select the **Sat Reflection Mode**.

   See [Choosing a reflection mode](#choosing-a-reflection-mode).

1. Click the **Apply** button below **Sat Processing Status** to import the file once.

   The satellites will be added to the **Satellites Table**.

1. To keep importing automatically, set **Sat Update Timer** to the import interval (default: *3600 s*).

1. Set **Sat Update Status** to *Enabled*.

1. Repeat these steps for the earth stations on the **ES Config** page, using **ES Import Path**, **ES Reflection Mode**, **Default Dish Size**, the **Apply** button, **ES Update Timer**, and **ES Update Status**.

The import runs in the background. The outages of a large import are calculated in batches, so it can take a moment before the **Outages** page is complete.

#### Choosing a Reflection Mode

The reflection mode determines how a table follows its file. The earth stations and the satellites each have their own mode.

- **Manual** (default): The import adds new rows and updates existing ones. Nothing is deleted automatically, and the file is never changed.
- **Auto Sync**: The table and the file mirror each other. When the update status is *Enabled*, rows that you add, edit, or delete in the table are written back to the file, and the file is imported again. A row is deleted once it is no longer in the file.
- **Auto Delete**: The import adds and updates rows, and deletes rows that are no longer in the file. With **ES Auto Delete Delay** or **Sat Auto Delete Delay**, you can keep a missing row for a number of seconds before it is deleted. This prevents deletions when the file is briefly incomplete. The default, *Real-time*, deletes the row immediately.

The following buttons perform a one-time action, in any mode:

- **ES Delete All Removed** and **Sat Delete All Removed**: Delete every row that is not in the file.
- **ES Sync All Data** and **Sat Sync All Data**: Make the table and the file mirror each other once.

#### Imported and Manual Earth Stations

The **Origin** column of the **Earth Station** table shows who owns each earth station:

- **Imported** earth stations come from the file. The import creates, updates, and deletes them.
- **Manual** earth stations were added with **New Earth Station**. The import never deletes them, in any reflection mode.

Earth stations created with a connector version older than 1.3.0.1 are treated as imported.

If the file contains an earth station with the same name as a manual earth station, the file wins:

- In the **Manual** and **Auto Delete** modes, the manual earth station is renamed to *\<name\> [manual-conflict]*. Its **Original Name** column keeps the previous name, and its **Conflict** column shows *Name Collision*. As soon as the file no longer uses the name, the manual earth station automatically gets its original name back.
- In the **Auto Sync** mode, the manual earth station becomes an imported earth station, because the table and the file form one list in that mode.

To keep an earth station out of the import, give it a name that does not appear in the file.

### Configuring the Outage Calculation

On the **Configuration** page, click **Outage Config** to open the prediction settings:

- **Visibility Threshold**: The minimum elevation angle at which an earth station can see its satellite (default: *0 deg*). When you import the earth stations with the **Apply** button and a fixed earth station is below this angle, a message will warn you that the earth station may not have line of sight to its satellite. The earth station is then listed in the element log.
- **Number of Cycles**: The number of equinox cycles for which future outages are calculated, from 1 to 5 (default: *2*).
- **Execution Timer**: How often the future outages are recalculated (default: *43200 s*, i.e., 12 hours).
- **Calculate Outages**: Recalculates all future outages immediately.
- **Future Outages Update Time** and **Outage Last Import Time**: When the outages were last calculated.

The status of each earth station is re-evaluated every 10 seconds, regardless of the **Execution Timer**.

### Reading the Results

#### General Page

This page shows the number of **Monitored Stations**, the number of **Active Outages**, and the number of **Satellites**.

#### Earth Stations Page

The **Earth Station** table contains one row per earth station. The most important columns are:

- **Status**: *Active* while an outage is in progress, otherwise *Inactive*.
- **Time to Next Outage**: The number of days until the next outage. *0* means the next outage is today.
- **Start** and **End**: The next outage window, in UTC.
- **Peak**, **Duration**, and **Season**: Details of the next outage.
- **Azimuth** and **Elevation**: The orientation of the dish. For fixed earth stations, this is calculated from the satellite position. For steerable earth stations, this is the value reported by the controller.
- **Outage Angle**: The angle below which interference can occur, based on the frequency band and the dish size.
- **Current Angle** and **Angular Difference**: The angle between the sun and the satellite at the last calculation, and its difference with the outage angle. These values are not updated in real time.
- **Origin**, **Original Name**, and **Conflict**: The ownership of the earth station.

  See [Imported and manual earth stations](#imported-and-manual-earth-stations).

To be alerted when an outage starts, configure an alarm template on the **Status** column, e.g., with a minor alarm when the value is *Active*.

#### Outages Page

The **Outages Table** lists every predicted outage window of every earth station, with the **Start**, **Peak**, **End**, **Duration**, **Season**, and **Time to Outage** in days. The rows are recalculated based on the **Execution Timer**, when you click **Calculate Outages**, and when an earth station changes.

#### Outage Overview Page

This page shows a tree view with one entry per earth station, including its future outages. Only earth stations with the **Outage Overview** column set to *Enabled* are included.

On the **Configuration** page, you can configure the tree view in the **Tree Control Config** section:

- **Tree Overview**: Enables or disables the tree view.
- **Enable All** and **Disable All**: Set the **Outage Overview** column of all earth stations at once.
- **Overview Limit**: The maximum number of earth stations in the tree view (default: *100*, maximum: *500*).

To see the data behind the tree view, set **Tree Overview Info** to *Enabled* in the **General Settings** section.

### Troubleshooting

- **An earth station from the file is missing**: Check the element log. The earth station may refer to a satellite that is not in the **Satellites Table**, or a steerable earth station may refer to a protocol that is not registered on the **ES Subscribers** page. Import the satellites first, and then import the earth stations again.
- **Nothing is imported**: Check that the file name starts with the ID of the DataMiner Agent that hosts the element and ends with `_ESO.csv` or `_SO.csv`, and that the import path points to an existing folder on that Agent. Paths that contain `..` are rejected.
- **The Azimuth and Elevation of a steerable earth station are N/A**: Check that the controller element is active, that its ID is entered as *DataMinerID/ElementID*, that the protocol name and version match the **ES Subscribers** entry, and that the **Earth Station Element Key** is filled in when the orientation parameters are table columns.
- **A manual earth station was renamed with [manual-conflict]**: An imported earth station now uses the same name. Rename the manual earth station, or remove the name from the file.
- **The satellite longitude is wrong after an import**: Use a period as the decimal separator in the satellites file, and do not use thousands separators.

## Notes

- All dates and times of the outage calculations are in UTC.
- The predictions assume a geostationary satellite and are best-effort estimates. Verify critical maintenance windows with the information from your satellite operator.
