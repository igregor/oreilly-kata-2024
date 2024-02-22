# Monitoring Device Gateway

## Status

ACCEPTED

## Context

Vital sign monitoring devices communicate with the rest of the system through a queue.
Yet having the equipment communicate directly with the queue might not be ideal.
Adding additional layer could enable us to enrich the data or evolve the message format.

### Requirements

- Transmission rates range from 0.5s to 3600s.
- Latency needs to be low.

### Business Assumptions

- Vital sign monitoring devices should not need a sophisticated sub-system to send data.
- Vital sign monitoring devices are difficult to change/update.

## Considered options

- Network gateway to receive data from the input sources and write it to the queue.
- Input sources write data directly to the queue.

## Decision

Network gateway to receive data from the input sources and write it to the queue.

**Reasons:**

- Monitoring devices are not aware of the patient's context. The network gateway can enrich the message with patient's context.
- Above will allow subscribing to messages for a specific patient only.
- The network gateway can be used to evolve the message format without affecting the input sources.
- The network gateway can be used to handle different input formats and protocols from monitoring devices.
- "Multiplexer" gateway (handling multiple queues) can be used to replace the remaining parts of the system in a "blue-green deployment" style.

### Consequences

- Gateway is a single point of failure, High Availability suggests a stateless service.
- Need to ensure that the gateway is not a bottleneck. Latency here will affect all the critical functions.
