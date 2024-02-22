# Use Web Frontends

## Status

DRAFT

## Context

Currently, we identified three interfaces for end users:

- Nurse Station
- Mobile App
- History App

### Requirements

- Authentication for certain operations
- Display tabular and graphical data
- Receive push notifications
- Interact with system backend via HTTP

### Business Assumptions

- In the first iteration of the system we should make deployment as easy as possible.

## Considered options

- Use a web frontend for all interfaces
- Use native applications for some/all interfaces

## Decision

Use a web frontend for all interfaces.

**Reasons:**

- Web applications can handle all the required functions.
- Web applications can be accessed from any device with a browser.
- No need to install the software on medical professionals' phones and nurse stations.
- Updates can be performed only with replacing the frontend code stored on the server.
