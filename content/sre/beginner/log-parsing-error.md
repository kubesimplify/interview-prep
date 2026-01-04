---
title: "Log Analysis & Parsing"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 20
description: "Debugging missing logs in a centralized logging system."
---

### Scenario

A developer complains that their application logs are not showing up in Kibana/Splunk. The application pod is running fine.

### Question

How do you trace where the logs are dropping?

### Expected Answer

1.  **Source**: `kubectl logs <pod>` - verify the app is actually printing to STDOUT/STDERR.
2.  **Node Level**: Check the log collector agent (e.g., Fluentd, Filebeat) on the node. Is the agent running? Is it tailing the correct path (`/var/log/pods/...`)?
3.  **Transport**: Check agent logs for buffer full errors or network timeouts connecting to the backend (Elasticsearch).
4.  **Ingestion**: Check index patterns or parsing errors (timestamp mismatch) in the backend.
