---
title: "Zero-Downtime Database Migration"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 10
description: "Handling schema changes in a high-traffic environment."
---

### Scenario

You need to rename a core column `user_name` to `username` in a User table that receives 10,000 requests per second. You cannot afford any downtime or maintenance window.

### Question

How do you execute this migration safely ensuring both the old and new versions of the application code work during the transition?

### Expected Answer

1.  **Phase 1 - Add**: Add the new column `username` (nullable) to the DB.
2.  **Phase 2 - Dual Write**: Deploy app version v1.1 that writes to _both_ columns but reads from `user_name`.
3.  **Phase 3 - Backfill**: Run a script to copy existing data from `user_name` to `username`.
4.  **Phase 4 - Switch Read**: Deploy app v1.2 that reads from `username` (still writes to both for rollback safety).
5.  **Phase 5 - Cleanup**: Remove `user_name` column and stop writing to it.
6.  **Key Concept**: "Expand and Contract" pattern.
