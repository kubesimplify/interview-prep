---
title: "Database Connection Exhaustion"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 20
description: "Debugging a sudden spike in 500 errors related to DB connectivity."
---

### Scenario

Your API service starts throwing 500 errors. The logs say `FATAL: remaining connection slots are reserved for non-replication superuser connections`.

### Question

What is happening, and how do you fix it (short term and long term)?

### Expected Answer

1.  **Root Cause**: The application has exhausted the Postgres `max_connections` limit.
2.  **Short Term Fix**:
    - Restart app pods (clears leaked connections).
    - Temporarily increase `max_connections` if RAM allows.
3.  **Long Term Fix**:
    - Implement client-side pooling (e.g., HikariCP) properly.
    - Use a server-side pooler like **PgBouncer** to multiplex connections.
    - Check for connection leaks (code not closing rows/sessions).
