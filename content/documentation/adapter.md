---
title: BERAdapter
type: explanation
prev: ./agent
next: ./glossary
---

## Inputs

### GitHub Events

The BER system primarily processes GitHub events as input signals:

- **Issue Comments**: Natural language requests prefixed with "@ber"
- **Issue Creation**: Initial problem statements and documentation requests
- **Issue Events**: Added or removed `labels` call the attached `BERAgent`
- **Installation Events**: System setup and initialization triggers


### Messages

Messages flow through a validation pipeline:

1. Author verification (skip bot messages)
2. Intent detection ("@ber" mentions)
3. Content extraction (body parsing)
