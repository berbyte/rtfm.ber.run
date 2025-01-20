---
title: How to: Use labels on GitHub issues to invoke a BER agent
type: docs
diataxis: howto
prev: documentation/howto-adapter-github-install
---

# Overview
BER agents are fully conversational. There are situations when you, the user knows exactly the agent and skill that they want to employ. This guide shows how to achieve this through labels. All of your repository's events are tracked by the BER adapter  which allows you to use the issue labels as the control and command panel of your agents.


# Label naming schema
To understand and compose BER-compatible labels follow a few simple rules:
 - The label title must start with `BER`
 - Delimiter between sections must be a colon, eg. `:`
 - The agent name must come first and a skill can optionally follow

# How-to communicate with labels
Imagine you would like to get story point estimations on an issue. By adding the following label to the issue in question: `BER:product-owner:estimation` the event is going to be caught by the adapter due to seeing the beginning of label title. 

With title including values that can be mapped to the list of agents and skills, the selected agent will respond to the issue with the selected skill, the output will be delivered as a comment by the BER adapter bot.

# Modifying, removing labels
Asking for different type of responses from BER is as simple as changing your labels to another one that matches BER's labelling schema. 

Removing a label has no effect on the output already provided.

> ![Note]
> Multiple label handling is not supported at the moment. 

# Further reading
This article is part of a series on BER GitHub adapter.

For a full reference on the agent and skills available with BER please look at our BERAgent Overview document.

Would you like to call BER directly? Look at our BERAdapter Overview for multiple ways to communicate with BER.
