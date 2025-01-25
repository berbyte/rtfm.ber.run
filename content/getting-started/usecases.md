---
title: Usecases
prev: getting-started
next: quickstart
type: docs
weight: 1
---

BER's flexible framework enables powerful automation and integration across different domains.

> [!NOTE]
>
> Here are some key use cases, which you can already try out:



## Domain Management

Streamline DNS and certificate management through natural language interactions. BER connects your project management tools directly to cloud services, enabling teams to handle domain operations through simple requests. This includes automated domain registration, DNS configuration - all through your existing workflow tools.

### Example Chat

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

> [!NOTE]
>
> Interested? Try it out!
{{< cards >}}
  {{< card link="/concepts/agent" title="Setting up BER" icon="beaker" >}}
{{< /cards >}}

## Code Visualization

Transform code into clear, visual diagrams automatically. BER helps development teams understand and document code behavior by generating flow diagrams, sequence diagrams, and architecture visualizations. This ensures documentation stays current with the codebase and helps teams communicate technical concepts effectively.

### Example Chat

```{filename=USER}
hey @ber, generate a sequence diagram for the user authentication flow
in auth.js
```

```{filename=BER}
Generated Sequence Diagram:


graph TD;
    A["Start"] --> B["User Attempts Login"];
    B --> C{Is User Valid?};
    C -->|Yes| D["Generate JWT Token"];
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

> [!NOTE]
>
> BER's flexible workflows enable you to build powerful agents for various use cases:
{{< cards >}}
  {{< card link="/tutorials/agent" title="Building your first BERAgent" icon="sun" >}}
{{< /cards >}}


## User Access Management

Simplify employee onboarding and offboarding across multiple SaaS services. While SSO solutions help, many organizations still struggle with managing user access across various platforms that don't support single sign-on. BER automates the tedious process of user provisioning, permission management, and access revocation across disparate systems.

### Example Chat

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

Simplify data access and analysis across your organization. BER can dynamically construct database queries, generate formatted reports, and deliver insights through your preferred channels. This eliminates manual data extraction and formatting work while ensuring consistent reporting across teams.

### Example Chat

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

Accelerate incident response through intelligent automation. BER connects your monitoring systems, chat platforms, and ITSM tools to streamline the entire incident lifecycle. From initial detection through resolution and post-mortems, BER reduces manual coordination work and helps teams resolve issues faster.

### Example Chat

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

