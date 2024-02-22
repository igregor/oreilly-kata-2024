# Authorizations

## Status

ACCEPTED

## Context

There should be some access restrictions to the system. We should document those assumptions.
They will be an important influence on other decisions.
On the other hand they were made without consulting the end users, so we should expect change down the line.

### Business Assumptions

- While patient monitoring data must be secure, MonitorMe does not have to meet any government regulatory requirements.

## Decision

- Doctor can be assigned one or more patients.
- Nurse station can be assigned one or more patients.
- Nurse station can be assigned one or more nurses.
- Patient can be assigned one or more monitoring devices.

### Who is caring for a patient?

- All patients assigned to a doctor are considered under the care of that doctor.
- All patients assigned to a nurse station are considered under the care of all the nurses in that station.

### Authorizations

- Medical staff should only see data for patients under their care.
  - Exception: anyone with physical access to Nurse Station can view the dashboard data, we assume requiring a login to see the dashboard would be too inconvenient.
- Only nurses can assign monitoring devices to patients, and only to patients under their care.
- Only nurses can configure analyzers, and only for patients under their care.
