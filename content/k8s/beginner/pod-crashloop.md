---
title: "Debug a CrashLoopBackOff"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 10
description: "Resolving common pod startup failures."
---

### Scenario

You deploy a new pod, and it enters a `CrashLoopBackOff` state.

### Question

Walk me through your debugging process to find the root cause.

### Expected Answer

1.  **Inspect State**: `kubectl get pod` (confirm restart count) and `kubectl describe pod` (check for Events: OOMKilled? Liveness Probe failure?).
2.  **Check Logs**: `kubectl logs <pod>` and `kubectl logs <pod> --previous` (crucial to see _why_ it died last time).
3.  **Common Causes**:
    - **Application Error**: Missing env var, panic on startup.
    - **Probes**: Liveness probe configured incorrectly (e.g., checking port 8080 when app listens on 80).
    - **Resources**: OOMKilled (Memory limit too low).
