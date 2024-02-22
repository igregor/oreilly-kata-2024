# Use Access Control Gateway

## Status

ACCEPTED

## Context

There are some access restrictions to the system.
Some protect patient privacy, others prevent mistakes/malice.

### Requirements

- Medical staff should only see data for patients under their care.
- Medical staff should only be able to configure monitors for patients under their care.

### Business Assumptions

- While patient monitoring data must be secure, MonitorMe does not have to meet any government regulatory requirements

## Considered options

- User applications interact with the system via an access control gateway. The rest of the system components trust each other.
- All components handle access control

## Decision

User applications interact with the system via an access control gateway. The rest of the system components trust each other.

**Reasons:**

- Centralizing access control simplifies the system.
- Especially relevant since the user facing parts are CRUD-level simple. The actual complexity is in the backend.

### Consequences

- Components are in an isolated network. External access is only possible through the access control gateway (and monitoring device gateway for data input).
