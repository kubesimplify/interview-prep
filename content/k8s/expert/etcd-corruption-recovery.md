---
title: "Etcd Cluster Loss Recovery"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 10
description: "Disaster recovery for the Kubernetes control plane."
---

### Scenario

You have a 3-node HA Kubernetes cluster. Due to a critical failure (e.g., 2 nodes corrupted simultaneously), you have lost quorum in etcd. The API server is read-only or unresponsive. You have a snapshot backup `snapshot.db`.

### Question

How do you restore the cluster functionality?

### Expected Answer

1.  **Stop Instances**: Stop all `kube-apiserver` and `etcd` static pods on all masters to prevent further corruption.
2.  **Restore (etcdctl)**: On _one_ master node, run `etcdctl snapshot restore snapshot.db --data-dir /var/lib/etcd-new ...`. This creates a new single-member cluster from the data.
3.  **Update Config**: specific point: update `etcd.yaml` manifest to point to the new data directory and set `--initial-cluster-state=new`.
4.  **Start & Scaling**: Start this main member. Once healthy, join the other 2 nodes as new members one by one.
5.  **Restart Control Plane**: Restart API servers/Scheduler/Controller Manager.
