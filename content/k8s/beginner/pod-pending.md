---
title: "Pod Pending State Analysis"
date: 2026-01-10
author: "KubeSimplify"
draft: false
weight: 1
description: "A scheduled pod remains in Pending status endlessly. Diagnose the cause."
---

### Scenario

You deploying a new replica set, but the pods are stuck in `Pending` state and are not being scheduled on any node.

### Question

What are the possible reasons for this, and how would you investigate?

### Expected Answer

1.  **Check Events**:
    - `kubectl describe pod <pod-name>` to see scheduler events.
    - Common reasons: "Insufficient cpu", "Insufficient memory", "No node(s) available for zone", "Taint/Toleration mismatch".
2.  **Resource Quotas**:
    - Check if the namespace has hit its resource quota.
3.  **Node Status**:
    - `kubectl get nodes` to ensure nodes are `Ready`.
    - Check for taints on the nodes.
