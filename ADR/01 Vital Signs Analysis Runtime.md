# Vital Signs Analysis Runtime

## Status

ACCEPTED

## Context

MonitorMe software must analyze each patient’s vital signs and alert a medical professional if it detects an issue.

### Requirements

- If any of vital sign monitoring devices fails, analysis must still function for the available signals.
- Robust support for different analysis algorithms - from simple threshold checks to complex machine learning models.
- System needs to handle maximum 500 patients.
- Updates have to performed with zero downtime.

### Business Assumptions

- Failure of the system to alert a medical professional of a patient’s vital sign issue is a critical failure.
- Complex analysis tools might be sourced from third-parties with relevant expertise.

## Considered options

- Each monitor is an isolated, containerized process.
- Use a monolithic analysis engine.

## Decision

Each monitor is an isolated, containerized process.

**Reasons:**

- Allows for easier management of different analysis tools.
- Malfunction of single monitor does not affect other monitors.
- Update by starting a new container and replacing the old one when it is ready.
- Popular orchestration tools like Kubernetes and Docker Swarm can do most of the heavy lifting for us.
- Horizontal scaling if the resource requirements increase.

### Consequences

- Monitors should have modest resource requirements, because we need to run up to 500 of them (or 500 of each type).
