---
title: "Service Discovery Failure"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 20
description: "Troubleshooting internal DNS resolution issues."
---

### Scenario

Frontend pod `frontend-app` cannot connect to Backend pod `backend-app` using the service name `http://backend-svc`. It returns "Name or service not known".

### Question

How do you debug this DNS/Network issue?

### Expected Answer

1.  **Verify Service**: Does `backend-svc` exist? Does it have valid **Endpoints**? (`kubectl get ep backend-svc`). If no endpoints, the selector doesn't match the pods.
2.  **Test DNS**: Exec into frontend pod and run `nslookup backend-svc` or `dig backend-svc.default.svc.cluster.local`.
3.  **Check CoreDNS**: Are CoreDNS pods running in `kube-system`? Check their logs for errors.
4.  **Network Policy**: Is there a NetworkPolicy blocking traffic between these namespaces/pods?
