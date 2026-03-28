---
name: lms
description: Use LMS MCP tools for live course data
always: true
---

# LMS Backend Tools

You have access to the following LMS backend tools via MCP:

## Available Tools

- **lms_health**: Check if the LMS backend is healthy and report the item count.
- **lms_labs**: List all labs available in the LMS. Returns lab IDs and titles.
- **lms_learners**: List all learners registered in the LMS.
- **lms_pass_rates**: Get pass rates (avg score and attempt count per task) for a specific lab. Requires `lab` parameter.
- **lms_timeline**: Get submission timeline (date + submission count) for a specific lab. Requires `lab` parameter.
- **lms_groups**: Get group performance (avg score + student count per group) for a specific lab. Requires `lab` parameter.
- **lms_top_learners**: Get top learners by average score for a specific lab. Requires `lab` parameter. Optional `limit` parameter (default 5).
- **lms_completion_rate**: Get completion rate (passed / total) for a specific lab. Requires `lab` parameter.
- **lms_sync_pipeline**: Trigger the LMS sync pipeline. May take a moment.

## Strategy

### When a lab parameter is needed

If the user asks about scores, pass rates, completion, groups, timeline, or top learners **without specifying a lab**:

1. First call `lms_labs` to get the list of available labs
2. If multiple labs are available, ask the user to choose one
3. Use each lab title as the user-facing label
4. Let the shared `structured-ui` skill handle how to present the choice on supported channels

### Formatting responses

- Format percentages nicely (e.g., "85.5%" not "0.855")
- Format counts clearly (e.g., "42 items" not just "42")
- Keep responses concise and well-structured
- Use bullet points or numbered lists for clarity

### When the user asks "what can you do?"

Explain that you can:
- Check LMS backend health and data freshness
- List available labs, learners, and groups
- Analyze lab performance: pass rates, completion rates, top learners
- View submission timelines and group statistics
- Trigger data sync from the autochecker API

Be clear about your limitations:
- You need a specific lab ID to get detailed analytics
- You cannot modify data, only read it
- Analytics are based on data from the autochecker API

### Tool selection examples

- "Show me the scores" → Ask which lab first
- "What's the pass rate for lab-04?" → Use `lms_pass_rates` with `lab="lab-04"`
- "Who are the top students in lab-06?" → Use `lms_top_learners` with `lab="lab-06"`
- "Is the backend working?" → Use `lms_health`
- "What labs do we have?" → Use `lms_labs`
- "How is group B-21-SE-01 doing in lab-05?" → Use `lms_groups` with `lab="lab-05"`

### Data freshness

If the user asks about very recent data and the results seem outdated, suggest calling `lms_sync_pipeline` to refresh the data, then retry the query.
