---
uid: Connector_help_Skyline_Job_Manager_Technical
---

# Skyline Job Manager

## About

This connector exposes a REST API that can be used to manage jobs and distribute them to operational domains (DataMiner SRM applications).

### 1.0.3 Range (SLC Main)

This range builds on the 1.0.x ranges, inheriting all their functionalities while improving authentication security. For a better understanding of all functionalities, refer to the sections below.

### 3.0.0.x Range (EOL)

*This range is currently end-of-life (EOL) and **should not be used for new developments**.*

This range was designed to act as an intermediary between the DataMiner Jobs app and the SRM Booking module. Developed on top of range 2.0.0.x, it allows for fully customizable data presentation. Users can configure which job fields are displayed in the table, and information templates can be used to name columns according to the job fields they contain. This range also enables operators to modify job fields directly from the connector interface. It supports immediate job processing as well as bulk operations triggered by subscription events. The script can be configured on the Script Config subpage of the Configurations page. Note that custom solutions are required for the creation of bookings.

### Other Ranges (Deprecated)

- **1.0.0.x range**: This range exposes a web service for third-party applications to access and request jobs information. Third-party apps can create new jobs on this element, which, based on the user's configuration, creates bookings.
- **1.0.1.x range**: Developed on top of 1.0.0.x, this range adds support for unicode characters.
- **1.0.2.x range**: Developed on top of 1.0.0.x, this range adds support for the ISO8601 DateTime format.
- **2.0.0.x range**: This range, along with the *SRM_ConvertToBooking* script, serves as an intermediary between the DataMiner Jobs app and the SRM Booking module. The main objective is to have a generic workflow that parses and converts the information provided, either through manual user input or by interfacing the DataMiner Jobs app API with an internal customer platform, into an SRM Booking.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

### 1.0.3.x Range

A DataMiner job is a domain-specific description to set up SRM services. DataMiner Domain Orchestrators will be able to convert a DataMiner job into one or multiple DataMiner bookings. Whereas a job is an administrative description of a service that needs to be set up, a DataMiner booking is a detailed definition of the service, the configuration profiles and parameters, the exact resources to be used, the detailed schedule, etc.

The purpose of this connector is to manage and store a collection of jobs. Jobs can be ingested via a REST API that is hosted by a Job Manager element. When possible, jobs are distributed to one or multiple network domains (virtual platforms), which then convert the jobs into full service bookings. Typically, Automation scripts are used to perform the complex operation of converting a job into a booking.

The following methods are currently supported by the API:

- /login

  - GET or POST: Authenticates the user and retrieves an access token that can be used with the other API methods. The user must have write access to the Job Manager element.

- /logout

  - POST: Logs out the authenticated user and invalidates the current access token.

- /job

  - GET: Retrieves a list of all jobs (only the summary of each job is returned).
  - POST: Creates a new job. A booking will automatically be created for each virtual platform in the new job.
  - PUT: Updates an existing job. Related bookings will be replaced by new instances.

- /job/{requesterID}/{jobID}

  - GET: Retrieves all details of the specified job.
  - DELETE: Deletes the specified job. Related bookings will also be deleted.

Access tokens are used to authenticate a user on the service. In order to obtain such an access token, the /login API method must be used, with a valid DataMiner username and password as arguments. The specified user needs to have write access to the Job Manager element.

When the login is successful, an access token is returned, which should be used in all other API calls. The access token expires after 5 minutes.

A Swagger ([https://swagger.io](https://swagger.io/)) YAML file is available with a more detailed description of the API (i.e. the exact JSON-XML messages that are expected). This file can also be used to automatically create a client that can communicate with the API.

> [!IMPORTANT]
>
> - The token is valid for 5 minutes from the time it is requested. Using the token (e.g., to request job details) does not extend its lifespan.
> - The Swagger documentation can be accessed through the `/help` endpoint of the API, but this endpoint is currently only accessible via the DMA server.
> - You can use the Accept and Content-Type headers to define the response data format as JSON or XML

Below you can find more information about the different data pages available in the element.

### General Page

This page displays the current status of the API service, together with the current endpoint URI on which the service can be reached.

### Jobs Page

This page contains tables that are used to store the data of each job, along with the detailed information and properties for each service that belongs to the job.

### Jobs Details Page

This page provides detailed information about each service associated with the job.

You can also execute the Automation scripts selected on the Configuration page. For more details about configuring these scripts, refer to the Configuration page section below.

Use the page button to open a pop-up page with the service details and profiles.

### Configuration Page

On this page, the **Virtual Platforms Table** provides a mapping between the virtual platform (defined in the job) and Automation scripts. Three scripts must be configured: a script to create a booking, a script to update bookings, and a script to remove bookings. The Booking Manager element on which the booking should be registered must also be specified here for each virtual platform.

The **Create Booking Script** will be executed for each virtual platform in a job that is added through the API. When a job is updated via the API, the **Update Booking Script** will be executed. After a job is deleted via the API, the **Delete Booking Script** will be executed.

Additionally, the address and port of the web service endpoint can be configured here. After the address or port has been changed, the web service will restart. Make sure that incoming traffic is allowed in the (Windows) firewall for the configured port.

#### Configuration of the virtual platforms

Virtual platforms must be configured on the Configuration page before you start using a newly created element, as otherwise the jobs will not be automatically translated into bookings.

Use the context menu to add a new row to the table, representing a virtual platform. You will need to fill in the name of the virtual platform in a pop-up window.

After you have added the row, use the dropdown controls to specify the Booking Manager element and the create/delete booking scripts. Only valid elements (with protocol name "Skyline Booking Manager") and valid scripts (with correct input parameters - see [Notes](#notes) section below) are available.

### Login History Page

This page displays a table with historical user login information, including the username, login status, and last attempt. The historical user login data is automatically deleted when the last attempt exceeds the auto-delete time defined on the Configuration page.

### API Help Page

This page displays the default WCF help page that describes the available methods and expected input/output of the REST web service.

### 3.0.0.x Range

The Skyline Job Manager connector is used to parse **generic booking info** provided by a job.

The connector can be configured to display certain job fields. A job field can be displayed in three ways: as a read-only string, a modifiable string, or a drop-down box. The **Jobs table** contains 20 generic columns for each display option. The field displayed in each column can be configured in the **Configuration table**. **Information templates** can be used to replace the generic column names of the Jobs table and to hide unused columns.

Via the right-click menu of the Jobs table, you can **convert a job into a booking**. This action will launch the **Automation script** defined on the **Script Config** subpage of the **Configurations** page.

Note that if the **Default Behavior** is set to *Enabled*, the script needs to be able to accept the following input parameters:

- JobGuid (string): GUID of the selected job.
- JobManager (string): Element name of the Job Manager (if the **Skyline Job Manager Element Name** is set to *Included*).

Otherwise, the Automation script input parameters will be defined according to the data configured in the Input Script Parameters table.

Note also that the Automation script with the name defined in the Booking Script parameter will be triggered according to the configuration defined on the Script Config subpage. If **Run Booking Script on New Job** is set to *Enabled*, the script will be launched whenever there is a change to a job in the Jobs application.

### 2.0.0.x Range

The Skyline Job Manager connector is used to parse **generic booking info**, provided by a job.

Since the job parameters available in the Jobs app are customizable, first the **Configuration Table** must be configured. This table indicates from which Jobs app section and field names the connector should retrieve the values.

When the **Administrative State** of a job is changed to *Approved*, the connector will try to launch the **SRM_ConvertJobToBooking** script. This script parses custom booking info and launches the execution of a "silent booking" via a custom script. Given that the custom info required to perform the booking depends on the type of booking, the script needs to be changed according to what is indicated in the Note section at the top of the script. This includes the definition of the parameters to be parsed and the mapping of the silent booking to be launched, depending on the type of booking.

Note that while by default the connector will try to launch the **SRM_ConvertJobToBooking** script, at the top of the **Configurations** page, you can configure it to launch a **different custom script**.

As a final step, the custom silent booking script that has been launched will try to create bookings according to the requirements. This script **must report back the "Booking Status"** information to the Job Manager connector, as the creation of new bookings is conditionally triggered by the state of the "Administrative State" and "Booking Status" values.

## Notes

### Automation scripts

The Automation scripts that create and delete bookings for a specific domain must have the following input parameters:

Create booking:

- **jobManager**: DMA/element ID or element name of the Job Manager element that initiated the execution of the script.
- **bookingManager**: DMA/element ID or element name of the Booking Manager element on which the new booking should be registered.
- **newBookingRequestData**: XML document with all the data needed to create the new booking.

Delete booking:

- **jobManager**: DMA/element ID or element name of the Job Manager element that initiated the execution of the script.
- **bookingManager**: DMA/element ID or element name of the Booking Manager element that contains the booking that must be deleted.
- **deleteBookingRequestData**: XML document with the data needed to remove the booking (i.e. booking ID).

### Differences Between API V1 and API V2

#### API V1

- **Date Fields**: In API V1, the job start and end dates and times are stored in separate fields.
  - **StartDate**: Contains only the start date.
  - **StartTime**: Contains only the start time.
  - **EndDate**: Contains only the end date.

#### API V2

- **Date Fields**: In API V2, the date and time are combined into single fields.
  - **StartDateTime**: Contains both the start date and time in the ISO8601 DateTime format.
  - **EndDateTime**: Contains both the end date and time in the ISO8601 DateTime format.

#### Example

- **API V1**:
  - `StartDate`: `2024-12-20`
  - `StartTime`: `09:13:19`
  - `EndDate`: `2024-12-20`

- **API V2**:
  - `StartDateTime`: `2024-12-20T09:13:19Z`
  - `EndDateTime`: `2024-12-20T17:00:00Z`
