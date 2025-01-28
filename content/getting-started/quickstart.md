---
title: Quickstart Guide
next: concepts
prev: getting-started
sidebar:
  include: true
---

1. Clone the repository:

```
git clone git@github.com:berbyte/ber-os.git
cd ber-os
```

2. Install the dependencies:

```
go mod tidy
```

Choose how to run BER:

### Running BER as a GitHub Application

1. Create a GitHub App by following our [documentation guide](https://rtfm.ber.run/guides/howto-adapter-github-install/). This will provide you with the required credentials for the next steps.

2. Set the environment variables
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
go run . webhook --debug
```

For detailed GitHub adapter usage instructions, please visit our [GitHub Adapter Tutorial](https://rtfm.ber.run/tutorials/github/).


### Running BER as a Terminal User Interface

> [!WARNING]
> The TUI adapter is currently in an experimental state

1. Set the environment variable

```
export OPENAI_API_KEY=""
```

2. Run the TUI:

```
go run . tui
```





## Next Steps

1. Configure the BERAdapter for GitHub to start communicating immediately with `BERAgents`.
{{< cards >}}
  {{< card link="/tutorials/github" title="Accessing BER from a repository" icon="sparkles" >}}
{{< /cards >}}

2. Solve your problems with `BER`.
{{< cards >}}
  {{< card link="/tutorials/agent" title="Creating custom agents with BER" icon="sun" >}}
{{< /cards >}}
