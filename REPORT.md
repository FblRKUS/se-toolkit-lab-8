# Lab 8 — Report

Paste your checkpoint evidence below. Add screenshots as image files in the repo and reference them with `![description](path)`.

## Task 1A — Bare agent

**Question: "What is the agentic loop?"**

Response:
```
The agentic loop is a concept in psychology and behavioral science that describes a cyclical process through which individuals or agents (like humans or AI) engage in self-regulation and self-directed learning. It typically involves the following stages:

1. Goal Setting: The agent identifies a goal or desired outcome they want to achieve.
2. Action: The agent takes actions or makes decisions aimed at achieving the goal.
3. Feedback: The agent receives feedback from the environment or their own performance regarding the effectiveness of their actions.
4. Reflection: The agent reflects on the feedback, assessing what worked, what didn't, and why.
5. Adjustment: Based on the reflection, the agent adjusts their strategies or actions to improve future performance.

This loop can repeat multiple times, allowing the agent to refine their approach and enhance their learning and effectiveness over time. The agentic loop emphasizes the importance of agency, self-efficacy, and adaptability in achieving goals.
```

**Question: "What labs are available in our LMS?"**

Response:
```
It seems that the command to list labs in the LMS is not recognized. This could be due to the LMS tool not being installed or configured in the current environment.

Could you provide more details about the LMS you are using, or any specific commands you might have for accessing it?
```

✅ As expected, the agent doesn't have access to real LMS data without MCP tools.

## Task 1B — Agent with LMS tools

**Question: "What labs are available?"**

Response:
```
The available labs are:

1. Lab 01 – Products, Architecture & Roles
2. Lab 02 — Run, Fix, and Deploy a Backend Service
3. Lab 03 — Backend API: Explore, Debug, Implement, Deploy
4. Lab 04 — Testing, Front-end, and AI Agents
5. Lab 05 — Data Pipeline and Analytics Dashboard
6. Lab 06 — Build Your Own Agent
7. Lab 07 — Build a Client with an AI Coding Agent
8. Lab 08
```

✅ Tool called: `mcp_lms_lms_labs({})`

**Question: "Is the LMS backend healthy?"**

Response:
```
The LMS backend is healthy, with a total of 56 items.
```

✅ Tool called: `mcp_lms_lms_health({})`

## Task 1C — Skill prompt

**Question: "Show me the scores" (without specifying a lab)**

Response:
```
Please choose a lab from the following list to see the scores:

1. Lab 01 – Products, Architecture & Roles
2. Lab 02 — Run, Fix, and Deploy a Backend Service
3. Lab 03 — Backend API: Explore, Debug, Implement, Deploy
4. Lab 04 — Testing, Front-end, and AI Agents
5. Lab 05 — Data Pipeline and Analytics Dashboard
6. Lab 06 — Build Your Own Agent
7. Lab 07 — Build a Client with an AI Coding Agent
8. lab-08

Let me know which lab you'd like to check!
```

✅ Tool called: `mcp_lms_lms_labs({})` first to get available labs
✅ The skill prompt successfully guides the agent to ask which lab when the lab parameter is missing.

## Task 2A — Deployed agent

<!-- Paste a short nanobot startup log excerpt showing the gateway started inside Docker -->

## Task 2B — Web client

<!-- Screenshot of a conversation with the agent in the Flutter web app -->

## Task 3A — Structured logging

<!-- Paste happy-path and error-path log excerpts, VictoriaLogs query screenshot -->

## Task 3B — Traces

<!-- Screenshots: healthy trace span hierarchy, error trace -->

## Task 3C — Observability MCP tools

<!-- Paste agent responses to "any errors in the last hour?" under normal and failure conditions -->

## Task 4A — Multi-step investigation

<!-- Paste the agent's response to "What went wrong?" showing chained log + trace investigation -->

## Task 4B — Proactive health check

<!-- Screenshot or transcript of the proactive health report that appears in the Flutter chat -->

## Task 4C — Bug fix and recovery

<!-- 1. Root cause identified
     2. Code fix (diff or description)
     3. Post-fix response to "What went wrong?" showing the real underlying failure
     4. Healthy follow-up report or transcript after recovery -->
