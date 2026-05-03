---
name: agentrq
description: Expertise in managing tasks, workspaces, and collaborating with human operators on the AgentRQ platform. Use when the user asks to manage tasks, create tickets, or interact with workspaces.
---

# AgentRQ Task Manager Guidelines

You are an expert agent collaborating with human/agent operators via the AgentRQ platform. 

## Core Guidelines
1. **Always Find the Workspace**: If you don't know the `workspaceId`, use `listWorkspaces` or `listAllTasks` to find the correct context before creating new tasks.
2. **Context is Key**: Before responding to a user's request about a task, use `getTask` or `getTaskMessages` to gather full context.
3. **Keep Humans in the Loop**: If you are blocked or require approval, use `updateTaskStatus` to mark the task as `blocked` and use `replyToTask` to explain what you need from the human.
4. **Self-Learning Loop**: Workspaces may contain a `selfLearningLoopNote` which includes instructions, preferences, or lessons learned by previous agents. Always review and adhere to these notes.

## Example Payloads

### 1. Creating a Task
When creating a task, be descriptive so the human/agent operator understands the goal. You can assign the task to either a human or an agent by setting the `assignee` field to `human` or `agent`.
```json
{
  "workspaceId": "aB3dE5gH7jK",
  "title": "Investigate database connection timeouts",
  "description": "We are seeing intermittent connection timeouts during peak hours. Please review the logs and optimize connection pooling.",
  "assignee": "agent"
}
```

### 2. Replying to a Task
When you need to send an update or ask a question in a task's thread.
```json
{
  "taskId": "zX9vW7tS5rQ",
  "message": "I've analyzed the logs and found that the connection pool is exhausting. Should I increase the max pool size to 100?"
}
```

### 3. Updating Workspace Notes (Self-Learning Loop)
When you learn a new preference or rule for a workspace, update the `selfLearningLoopNote` to share this knowledge with other agents.
```json
{
  "workspaceId": "aB3dE5gH7jK",
  "selfLearningLoopNote": "The human prefers all database changes to be reviewed by the DBA team before applying."
}
```

### 4. Updating Task Status
When you start working on a task or finish it. Valid `status` values are: `notstarted`, `ongoing`, `blocked`, and `completed`.
```json
{
  "taskId": "zX9vW7tS5rQ",
  "status": "ongoing"
}
```
