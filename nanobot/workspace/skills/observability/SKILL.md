---
name: observability
description: Investigate system health, logs, and traces when errors are suspected
always: true
---

# Observability Strategy

You have access to system logs and traces via the `obs` MCP server.

## Service Names

- LMS Backend: "Learning Management Service"
- Qwen Code API: "Qwen Code API"
- Nanobot: "nanobot"

## MANDATORY Investigation Flow

When the user asks **"What went wrong?"**, **"Check system health"**, or when a tool call fails, you MUST perform these steps IN ORDER within a single response:

1.  **logs_error_count(time_window="10m")**: Determine which services are failing.
2.  **logs_search(query="service.name:\"Learning Management Service\" severity:ERROR")**: Search for the actual error messages for the failing service.
3.  **traces_get(trace_id="...")**: YOU MUST CALL THIS TOOL. Pick the most recent `trace_id` from the logs and fetch the full trace. This is non-negotiable.
4.  **Summarize**: Explain the failure using BOTH log evidence (the error message) and trace evidence (the failing span and status code).

## Identifying the Planted Bug

The backend has a bug where it returns **HTTP 404 (Not Found)** but the logs and traces show a **Database Error (Connection closed)**. If you see this discrepancy, YOU MUST REPORT IT as a bug in the application's error handling path.

## Examples

- "What went wrong?" -> Follow the mandatory flow above.
- "Check system health" -> Follow the mandatory flow above.
