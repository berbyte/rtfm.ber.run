---
title: BERAdapter
diataxis: explanation
prev: BERAgent
next: tutorials
weight: 3
---

## Summary
The `BERAdapter` is client-facing interface that is implemented for any system that has a method to communicate real-world input with a `BERAgent`. An adapter is defined for a specific interface which may be a platform e.g. Github; or Jira.

For input, the `BERAdapter` relies on webhooks and for output it integrates with the service's REST API endpoint. This makes adapters pluggable, flexible and extendable.

[![BER's Pluggable Adapter System](/diagrams/ber-003-adapter.svg)](/diagrams/ber-003-adapter.svg)


Find practical, detailed examples in our tutorial about Adapter topics!
{{< cards >}}
  {{< card link="/tutorials/github" title="BERAdapter" icon="sparkles" >}}
{{< /cards >}}
