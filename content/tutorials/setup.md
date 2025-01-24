---
title: Setting up BER
weight: 1
prev: /tutorials
next: /tutorials/agent
sidebar:
  open: true
---

> [!caution]
>
> ⚠️ **Under Active Development** ⚠️
>
> - This project is in active development and not production ready
> - Breaking changes may occur without prior notice
> - APIs and features are subject to change
> - Use at your own risk
>
> We encourage you to experiment and provide feedback, but please do not use in production environments yet.

1. Clone the repository:

```
git clone git@github.com:berbyte/ber-os.git
cd ber-os
```

2. Install the dependencies:

```
go mod tidy
```

## Usage

### TUI

1. Set the environment variable

```
export OPENAI_API_KEY=""
```

2. Run the TUI:

```
go run . tui
```

### GitHub Application

1. Set the environment variables
```
export GH_APP_ID=""
export GH_PRIVATE_KEY="" # base64 decoded pem
export GH_WEBHOOK_SECRET=""

export OPENAI_API_KEY=""
```

2. Start ngrok:

```
ngrok http http://localhost:8080
```

3. Run the application:
```
go run . webhook
```
