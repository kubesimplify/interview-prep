---
title: "PVC Stuck in Pending"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 20
description: "Debugging PersistentVolumeClaim binding issues."
---

### Scenario

A StatefulSet pod is stuck in `Pending`. `kubectl describe pod` says "0/3 nodes are available: pod has unbound immediate PersistentVolumeClaims". The PVC is stuck in `Pending` state.

### Question

What are the likely reasons the PVC is not binding?

### Expected Answer

1.  **StorageClass**: Does the StorageClass requested exist? Is the provisioner (e.g., EBS CSI driver) working?
2.  **Volume Binding Mode**: If `WaitForFirstConsumer` is set, the PV won't be created until the Pod is scheduled. If the Pod can't be scheduled (e.g., due to taints/CPU limits), the PVC waits forever. Deadlock.
3.  **Availability Zone**: If using AWS EBS/GCP PD, the PV might be created in `us-east-1a`, but the Pod is trying to run on a node in `us-east-1b`.
4.  **Capacity**: The underlying storage backend (e.g., AWS quota) might be full/exceeded.
