---
uid: Connector_help_Microsoft_Azure_DevOps
---

# Microsoft Azure DevOps

This connector facilitates seamless integration with **Azure DevOps** via the REST API, enabling efficient management of work items.
This connector can be leveraged to manage a system where Azure DevOps is used alongside other task systems (e.g. JIRA, GitHub, ...).

## About

### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -                |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | Azure DevOps Services REST API 7.1 |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                    | -                      |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the General > Configuration page, you need to specify the **organization**, **project** and a **PAT** (personal access token).
For the organization and project, both the name or guid can be used.

#### InterApp API

On the General > API Configuration page, you can specify the mapping of the types & states between Azure work items and the InterApp tasks.
The **Link ID Field Name** parameter is used for setting a work item field with the Link ID of the InterApp task.

## How to use

### InterApp

The below code can be copied when using this InterApp API in other connectors or Automation scripts:

```csharp
namespace QAction_1.InterApp.Messages
{
	using System;
	using System.Collections.Generic;

	using QAction_1.InterApp.MessagesContent;

	using Skyline.DataMiner.Core.InterAppCalls.Common.CallSingle;

	/// <summary>
	/// Basic response.
	/// </summary>
	[Serializable]
	public class BaseResponse : Message
	{
		/// <summary>
		/// Gets or sets if the request was successful.
		/// </summary>
		public bool Success { get; set; }

		/// <summary>
		/// Gets or sets the error message.
		/// </summary>
		public string ErrorMessage { get; set; }
	}

	/// <summary>
	/// Represents the request to create one or more tasks.
	/// </summary>
	[Serializable]
	public class CreateTasksRequest : Message
	{
		/// <summary>
		/// Gets or sets a list of task configurations.
		/// </summary>
		public List<TaskConfiguration> TaskConfigurations { get; set; } = new List<TaskConfiguration>();
	}

	/// <summary>
	/// Represents the response of the <see cref="CreateTasksRequest"/>.
	/// </summary>
	[Serializable]
	public class CreateTasksResponse : BaseResponse
	{
		/// <summary>
		/// Gets or sets the failed configurations and the error message.
		/// </summary>
		public List<(TaskConfiguration, string errorMessage)> FailedConfigurations { get; set; } = new List<(TaskConfiguration, string errorMessage)>();

		/// <summary>
		/// Gets or sets the created tasks.
		/// </summary>
		public List<InterAppTask> CreatedTasks { get; set; } = new List<InterAppTask>();
	}

	/// <summary>
	/// Represents the request to retrieve all relevant tasks.
	/// </summary>
	[Serializable]
	public class GetAllTasksRequest : Message
	{
	}

	/// <summary>
	/// Represents the response to the <see cref="GetAllTasksRequest"/>.
	/// </summary>
	[Serializable]
	public class GetAllTasksResponse : BaseResponse
	{
		/// <summary>
		/// Gets or sets the tasks.
		/// </summary>
		public List<InterAppTask> Tasks { get; set; } = new List<InterAppTask>();
	}

	/// <summary>
	/// Represents the request to update a task.
	/// </summary>
	[Serializable]
	public class UpdateTaskRequest : Message
	{
		/// <summary>
		/// Gets or sets the id.
		/// </summary>
		public string Id { get; set; }

		/// <summary>
		/// Gets or sets the global identifier used when using multiple task systems.
		/// </summary>
		public string LinkId { get; set; }

		/// <summary>
		/// Gets or sets the name.
		/// </summary>
		public string Name { get; set; }

		/// <summary>
		/// Gets or sets the description.
		/// </summary>
		public string Description { get; set; }

		/// <summary>
		/// Gets or sets the task type.
		/// </summary>
		public TaskType? Type { get; set; }

		/// <summary>
		/// Gets or sets the task state.
		/// </summary>
		public TaskState? State { get; set; }
	}

	/// <summary>
	/// Represents the response for the <see cref="UpdateTaskRequest"/>.
	/// </summary>
	[Serializable]
	public class UpdateTaskResponse : BaseResponse
	{
	}
}

namespace QAction_1.InterApp.MessagesContent
{
	using System;

	/// <summary>
	/// Represents a task used in the inter app communication
	/// </summary>
	[Serializable]
	public class InterAppTask
	{
		/// <summary>
		/// Gets or sets the link id. This represents an overarching identifier when working with multiple task systems.
		/// </summary>
		public string LinkId { get; set; }

		/// <summary>
		/// Gets or sets the task url. This can be used to cross-referencing when working with multiple task systems.
		/// </summary>
		public string TaskUrl { get; set; }

		/// <summary>
		/// Gets or sets the task type.
		/// </summary>
		public TaskType Type { get; set; }

		/// <summary>
		/// Gets or sets the task state.
		/// </summary>
		public TaskState State { get; set; }

		/// <summary>
		/// Gets or sets the id.
		/// </summary>
		public string Id { get; set; }

		/// <summary>
		/// Gets or sets the name.
		/// </summary>
		public string Name { get; set; }

		/// <summary>
		/// Gets or sets the description.
		/// </summary>
		public string Description { get; set; }

		/// <summary>
		/// Gets or sets the creation date.
		/// </summary>
		public DateTime CreatedAt { get; set; }

		/// <summary>
		/// Gets or sets the creator.
		/// </summary>
		public string CreatedBy { get; set; }
	}

	/// <summary>
	/// Represents a task configuration.
	/// </summary>
	[Serializable]
	public class TaskConfiguration
	{
		/// <summary>
		/// Gets or sets the link identifier used when using multiple task systems.
		/// </summary>
		public string LinkId { get; set; }

		/// <summary>
		/// Gets or sets the name.
		/// </summary>
		public string Name { get; set; }

		/// <summary>
		/// Gets or sets the description.
		/// </summary>
		public string Description { get; set; }

		/// <summary>
		/// Gets or sets the task type.
		/// </summary>
		public TaskType Type { get; set; }

		/// <summary>
		/// Gets or sets the task state. Optional.
		/// </summary>
		public TaskState? State { get; set; }

		/// <summary>
		/// Gets or sets the creation date. Optional.
		/// </summary>
		public DateTime? CreatedAt { get; set; }

		/// <summary>
		/// Gets or sets the task creator. Only mail addresses allowed. Optional.
		/// </summary>
		public string CreatedBy { get; set; }
	}

	/// <summary>
	/// Represents the task state.
	/// </summary>
	public enum TaskState
	{
		/// <summary>
		/// Unknown.
		/// </summary>
		Unknown = -1,

		/// <summary>
		/// Not Started.
		/// </summary>
		NotStarted,

		/// <summary>
		/// Started.
		/// </summary>
		Started,

		/// <summary>
		/// Finished.
		/// </summary>
		Finished,
	}

	/// <summary>
	/// Represents the task type.
	/// </summary>
	public enum TaskType
	{
		/// <summary>
		/// Unknown.
		/// </summary>
		Unknown = -1,

		/// <summary>
		/// Generic.
		/// </summary>
		Generic,

		/// <summary>
		/// Feature.
		/// </summary>
		Feature,

		/// <summary>
		/// Issue.
		/// </summary>
		Issue,
	}
}

namespace QAction_1.InterApp
{
	using System;
	using System.Collections.Generic;
	using QAction_1.InterApp.Messages;
	using QAction_1.InterApp.MessagesContent;

	/// <summary>
	/// Represents the known types.
	/// </summary>
	public static class KnownTypes
	{
		/// <summary>
		/// Represents the known types.
		/// </summary>
		public static readonly IReadOnlyList<Type> Types = new List<Type>
		{
			// Messages
			typeof(BaseResponse),

			typeof(CreateTasksRequest),
			typeof(CreateTasksResponse),

			typeof(UpdateTaskRequest),
			typeof(UpdateTaskResponse),

			typeof(GetAllTasksRequest),
			typeof(GetAllTasksResponse),

			// Message content
			typeof(TaskConfiguration),
			typeof(List<TaskConfiguration>),
			typeof(List<(TaskConfiguration, string)>),

			typeof(InterAppTask),
			typeof(List<InterAppTask>),

			// Enums
			typeof(TaskType),
			typeof(TaskState),
		};
	}
}
```
