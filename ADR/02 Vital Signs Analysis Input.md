# Vital Signs Analysis Input

## Status

ACCEPTED

## Context

Vital signs are sourced from different patient monitoring devices.
MonitorMe gathers this data for two main purposes:

- viewing by medical staff,
- analysis for alerting medical staff of issues.

### Requirements

- If any of vital sign monitoring devices fails, analysis must still function for the available signals.
- There are currently 8 different types of vital sign monitoring devices, but system should be able to handle more.
- Transmission rates range from 0.5s to 3600s.
- Latency needs to be low.

### Business Assumptions

- Vital sign data analyzed and recorded must be as accurate as possible.
- Monitoring devices should not need a sophisticated sub-system to send data.

## Considered options

- Vital sign monitoring devices write data to a persistent message queue.
- Vital sign monitoring devices write data directly to a database.

## Decision

Vital sign monitoring devices write data to a persistent message queue.

**Reasons:**

- Posting to a queue is a non-blocking operation mostly. Monitoring devices don't need to worry about locks etc.
- Data is not lost even if receiver is down.
- We can have separate consumers to handle different use cases.
- It's natural to represent each reading as an event, should make the analysis code simpler.

### Consequences

- Queue is a single point of failure.
- Need to ensure that the queue is not a bottleneck. Latency here will affect all the critical functions.
- Need to ensure queue does not fill up. Monitor if consumers are keeping up.
