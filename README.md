# AgentRQ Claude Marketplace

This repository hosts the AgentRQ plugin for Claude Code.

## Usage

To add this marketplace to your Claude Code instance:

```bash
/plugin marketplace add https://github.com/agentrq/agentrq-claude-extension
```

### Supervisor MCP
If you don't want to UI to manage the tasks but want to use MCP server directly, then install the AgentRQ plugin:

```bash
/plugin install agentrq@agentrq
```

### Workspace(Agent) MCP

```bash
/plugin install agentrq@agentrq-workspace
```

## Included Plugins

### AgentRQ
Human-in-the-loop task manager for agents. Connects to the AgentRQ supervisor MCP server (account-level — manage workspaces and tasks across all of them).

**Tools:**

| Tool | Description |
| --- | --- |
| `listWorkspaces` | List all workspaces for the authenticated user |
| `createWorkspace` | Create a new workspace |
| `getWorkspace` | Get a workspace by ID |
| `updateWorkspace` | Update a workspace |
| `getWorkspaceStats` | Get statistics for a workspace |
| `listTasks` | List tasks in a specific workspace |
| `listAllTasks` | List all tasks across all workspaces |
| `createTask` | Create a new task in a workspace |
| `getTask` | Get a specific task by ID |
| `respondToTask` | Submit an allow/deny response to a task |
| `replyToTask` | Post a message to a task thread |
| `updateTaskStatus` | Update a task's status |
| `updateTaskOrder` | Update a task's sort order |
| `updateTaskAssignee` | Update a task's assignee |
| `updateTaskAllowAll` | Toggle allow_all_commands for a task |
| `updateScheduledTask` | Update a scheduled/cron task |
| `getAttachment` | Get attachment data as base64 and metadata |

### AgentRQ Workspace
Workspace agent that executes tasks assigned by humans or supervisors, communicates progress via reply, and manages the task lifecycle within a specific AgentRQ workspace.

**Tools:**

| Tool | Description |
| --- | --- |
| `createTask` | Create a task for the human user. Returns the task ID. |
| `updateTaskStatus` | Update the status of a task. Useful for moving tasks to ongoing or completed. |
| `reply` | Send a message to the current ongoing task. You can optionally include attachments. |
| `downloadAttachment` | Download the content of an attachment by its ID |
| `getWorkspace` | Returns the workspace title and mission description. |
| `getTask` | Fetch a task. With no taskId, returns the next available "not started" task assigned to the agent (dequeues the work queue). With a taskId, returns that specific task. Set `includeConversation=true` to also include the task's chat history. |
| `publishEvent` | Publish a named event so that subscriber workspaces are notified and their trigger tasks are created automatically. |

## License
Apache-2.0
