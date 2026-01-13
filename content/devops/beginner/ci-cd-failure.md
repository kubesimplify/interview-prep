---
title: "CI/CD Pipeline Failure Debugging"
date: 2026-01-11
author: "KubeSimplify"
draft: false
weight: 1
description: "A deployment pipeline is failing at the artifact upload stage. How do you troubleshoot?"
---

### Scenario

Your team's main application pipeline is failing intermittently during the Docker image push to ECR.

### Question

How do you approach debugging this CI/CD failure? What are the potential causes?

### Expected Answer

1.  **Check Logs**:
    - Examine the build logs for specific error messages (e.g., `401 Unauthorized`, `Connection Timed Out`).
2.  **Permissions**:
    - Verify the IAM role used by the build agent has `ecr:PutImage` and `ecr:GetAuthorizationToken` permissions.
3.  **Network**:
    - Check if the build agent has internet access or a VPC endpoint to ECR.
4.  **Disk Space**:
    - Check if the build agent is running out of disk space (common with Docker layers).
