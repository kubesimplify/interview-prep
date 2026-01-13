---
title: "Triage: Sustained CPU Spike"
date: 2026-01-05
author: "KubeSimplify"
draft: false
weight: 10
description: "Initial response and analysis of a high CPU alert."
---

### Scenario

You receive a P2 alert: "High CPU usage (>90%) on Payment Service". The service is running on Kubernetes.

### Question

What are your first steps to triage this alert? How do you distinguish between a valid surge and a bug?

### Expected Answer

1.  **Immediate Check**: Health endpoints (is the service actually down/slow?), Error rates, and Latency graphs.
2.  **Correlations**: Check throughput/RPS. If RPS increased proportionally with CPU, it's likely scaling lag.
3.  **Logs**: Check for errors or repetitive log lines (infinite loop).
4.  **Action**: Horizontal Pod Autoscaler (HPA) should handle it. If max replicas reached, check upstream changes (deployments) or downstream dependencies (slow database causing churn).
