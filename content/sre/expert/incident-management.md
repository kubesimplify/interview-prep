---
title: "Managing a Major Outage"
date: 2023-10-27T10:00:00+00:00
draft: false
weight: 10
description: "Leading the response to a cascading failure."
---

### Scenario

A bad configuration push caused a cascading failure across the entire checkout flow. You are the designated Incident Commander (IC). Multiple teams (Network, DB, App) are jumping on the call, panicking, and proposing fixes simultaneously.

### Question

How do you manage this situation effectively?

### Expected Answer

1.  **Establish Command**: calm everyone down. State clearly: "I am the IC. All actions must be approved by me."
2.  **Roles**: Assign a Scribe (record timeline), Ops Lead (execute commands), and Comms Lead (stakeholder updates).
3.  **Triage**: Focus on _mitigation_ (rollback, shed load, killswitch), not _root cause analysis_ (RCA).
4.  **Communication**: Keep the main channel clear. Spin off investigation threads if needed but mandate reporting back.
5.  **Aftermath**: Once stable, declare "Incident Closed" and schedule the Post-Mortem.
