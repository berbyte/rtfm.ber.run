---
title: Usecases
prev: getting-started
next: quickstart
type: docs
weight: 1
---

BER's flexible framework enables powerful automation and integration across different domains.

Here are some key use cases, which you can already try out.

## Domain Management

> [!TIP]
> In this example, a user manages DNS records through natural language commands:
> 1. Initially requests an A record for demo.ber.run
> 2. Changes their mind to create a CNAME record instead
> 3. Approves the change, which is then implemented

```{filename=USER}
hey @ber, create a DNS record for demo.ber.run pointing to 127.0.0.1
with a TTL of 600 seconds.
```

```{filename=BER}
New DNS Record

============================
| Hostname: | demo.ber.run |
| Target:   | 127.0.0.1    |
| Type:     | A            |
| TTL:      | 3600         |
============================

👉 To create the record, comment: @ber approve 5bb9384d
```

```{filename=USER}
@ber Changed my mind, point the record to rtfm.ber.run and use a lower ttl.
```

```{filename=BER}
New DNS Record

============================
| Hostname: | demo.ber.run |
| Target:   | rtfm.ber.run |
| Type:     | CNAME        |
| TTL:      | 600          |
============================

👉 To create the record, comment: @ber approve 734b095b
```

```{filename=USER}
@ber approve 734b095b
```

```{filename=BER}
✅ demo.ber.run sucessfully created.

Details:
============================
| Hostname: | demo.ber.run |
| Target:   | rtfm.ber.run |
| Type:     | CNAME        |
| TTL:      | 600          |
============================

❗️ To revert, comment: @ber revert 0d219c57
```

{{< cards cols=1 >}}
  {{< card title="DNS Management Through Natural Language" subtitle="Watch BER handle DNS record creation, updates and validation through natural language commands, demonstrating the power of combining Cloudflare's API with GitHub's collaborative interface" image="https://rtfm.ber.run/demo.gif" >}}
{{< /cards >}}



> [!NOTE]
>
> Interested? Try it out!
{{< cards >}}
  {{< card link="/getting-started/quickstart" title="Quickstart Guide" icon="beaker" >}}
{{< /cards >}}

## Code Visualization

> [!TIP]
> This example shows how BER can automatically generate diagrams from code:
> 1. User requests a sequence diagram for authentication flow
> 2. BER analyzes the code and generates a Mermaid diagram
> 3. User approves and the diagram is saved as SVG

```{filename=USER}
hey @ber, generate a sequence diagram for the user authentication flow
in auth.js
```

```{filename=BER}
Generated Sequence Diagram:


graph TD;
    A["Start"] --> B["User Attempts Login"];
    C -->|Yes| D["Generate JWT Token"];
    B --> C{Is User Valid?};
    C -->|No| E["Return Error Message"];
    D --> F["Send Token to Client"];
    F --> G["User Logged In Successfully"];
    E --> H["Log Failed Attempt"];
    H --> A;
    G --> I["End"];

============================
| Format:  | Mermaid      |
| Source:  | auth.js      |
| Scope:   | Auth Flow    |
============================

👉 To save diagram, comment: @ber approve 9c4f182e
```

```{filename=USER}
@ber approve 9c4f182e
```

```{filename=BER}
✅ Diagram saved to docs/diagrams/auth-flow.svg

Details:
===========================================
| Location: | docs/diagrams/auth-flow.svg |
| Format:   | SVG                         |
| Size:     | 24KB                        |
===========================================

❗️ To revert, comment: @ber revert 2b7d945a
```

---

{{< cards >}}
  {{< card link="/tutorials/agent" title="Building your first BERAgent" icon="sun" >}}
{{< /cards >}}


> [!NOTE]
>
> BER's flexible workflows enable you to build powerful agents for various use cases:

## User Access Management

> [!TIP]
> This interaction demonstrates automated user provisioning:
> 1. Request to create accounts across multiple services
> 2. BER prepares the changes for approval
> 3. Upon approval, accounts are created with appropriate permissions

```{filename=USER}
hey @ber, create accounts for jane.doe@company.com in our standard
tools stack (Slack, Jira, GitLab) with developer permissions
```

```{filename=BER}
Account Creation Summary

=====================
| Service | Status  |
| ------- | ------- |
| Slack   | Pending |
| Jira    | Pending |
| GitLab  | Pending |
=====================

👉 To create accounts, comment: @ber approve 7d2e891f
```

```{filename=USER}
@ber approve 7d2e891f
```

```{filename=BER}
✅ Accounts created successfully

Details:
================================
| Service | Status  | Username |
| ------- | ------- | -------- |
| Slack   | Created | jane.doe |
| Jira    | Created | jane.doe |
| GitLab  | Created | jane.doe |
================================

❗️ To revert, comment: @ber revert 3f8a620d
```

```
hey @ber, show me all active service accounts for
john.smith@company.com who is leaving next week
```

```
hey @ber, revoke all access for departed employee
mark.wilson@company.com and generate an audit report
```




## Custom Reports

> [!TIP]
> This example shows BER's reporting capabilities:
> 1. User requests a signup report with specific parameters
> 2. BER generates a preview of the data
> 3. Upon approval, full report is generated in multiple formats

```{filename=USER}
hey @ber, generate a report of all users who signed up
in the last 30 days, grouped by country
```

```{filename=BER}
Report Preview:

=====================
| Country | Signups |
| ------- | ------- |
| USA     | 1,245   |
| UK      | 892     |
| Germany | 567     |
| Others  | 1,890   |
=====================

👉 To generate full report, comment: @ber approve 1a2b3c4d
```

```{filename=USER}
@ber approve 1a2b3c4d
```

```{filename=BER}
✅ Report generated and shared

Details:
================================
| Format:    | CSV, PDF        |
| Location:  | reports/        |
| Period:    | Last 30 days    |
| Records:   | 4,594           |
================================

❗️ To revert, comment: @ber revert 5e6f7g8h
```

## Incident Management

> [!TIP]
> This example demonstrates automated monitoring setup:
> 1. User requests log monitoring for specific errors
> 2. BER configures the monitoring rules
> 3. Upon approval, monitoring is enabled with ServiceNow integration

```{filename=USER}
hey @ber, monitor the logs for ConnectionTimeout errors
and create a ticket in ServiceNow if it appears
```

```{filename=BER}
Monitor Configuration:

=================================
| Type:     | Error Pattern     |
| Pattern:  | ConnectionTimeout |
| Action:   | Create Ticket     |
| System:   | ServiceNow        |
=================================

👉 To enable monitoring, comment: @ber approve 4d5e6f7g
```

```{filename=USER}
@ber approve 4d5e6f7g
```

```{filename=BER}
✅ Monitor enabled

Details:
===============================
| Status:    | Active         |
| Monitor ID:| MON-2024-123   |
| Logs:      | /var/log/app/* |
| Notify:    | #incidents     |
===============================

❗️ To disable, comment: @ber revert 8h9i0j1k
```


---

These use cases demonstrate BER's ability to bridge gaps between tools and teams, enabling natural language automation of complex workflows. The framework's flexibility allows you to adapt these patterns to your organization's specific needs and processes.

