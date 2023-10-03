---
tags:
  - high_availability
  - networking
references:
  - https://www.wikiwand.com/en/High_availability
---

# What does high availability (HA) look like?

To most, HA consists of 3 priniciples:
1. Redundancy: No single points of failure (SPOFs)
2. Reliable crossover: moving from 1 redundant instance to another may also become a SPOF, which we need to account for.
3. Failure detection: a user may never see a failure, but the maintainers must.

Here are some common HA architectural patterns:

![HA LB drawing](HA%20LB%20drawing.md)

This is considered highly available because, as is demonstrated, an LB failure does not cause our users to see a failure. 