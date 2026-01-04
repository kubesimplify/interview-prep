---
title: "Defining SLOs for a New Service"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 10
description: "Translating business requirements into Service Level Objectives."
---

### Scenario

The Product team wants to launch a new "Search" microservice. They ask for "100% availability" because it's critical.

### Question

How do you explain why 100% is unrealistic, and how do you help them define a meaningful SLO (Service Level Objective)?

### Expected Answer

1.  **Education**: Explain the cost of "nines". 100% limits innovation (no deployments allowed). Error budgets allow for safe failure.
2.  **Definition**:
    - **SLI (Indicator)**: Latency < 200ms and Success Rate (HTTP 200s).
    - **SLO (Objective)**: 99.9% of requests meet the SLI over 30 days.
3.  **Consequences**: Define what happens if the Error Budget is depleted (freeze features, focus on stability).
