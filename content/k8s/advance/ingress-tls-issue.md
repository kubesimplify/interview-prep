---
title: "Ingress TLS/SSL Verification"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 10
description: "Configuring HTTPS and debugging certificate errors."
---

### Scenario

You created a Kubernetes Ingress for `myapp.example.com` with a TLS secret. However, when users visit the site, they get a "Kubernetes Ingress Controller Fake Certificate" warning instead of your valid cert.

### Question

Why is the Ingress Controller invalidating or ignoring your certificate?

### Expected Answer

1.  **Secret Typo**: The Ingress definition refers to a `secretName` that doesn't exist or is misspelled.
2.  **Namespace Mismatch**: The TLS secret must exist in the _same namespace_ as the Ingress resource. It cannot be in another namespace.
3.  **Certificate Data**: The secret must contain keys `tls.crt` and `tls.key`. If they are swapped or invalid base64, the controller usually rejects it.
