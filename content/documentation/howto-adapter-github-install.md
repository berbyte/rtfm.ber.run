---
title: How to: Connect BER as a GitHub app
type: docs
diataxis: howto
prev: documentation/adapter
next: documentation/howto-adapter-github-label
---

# Overview
BER is a platform-agnostic framework. Any number of custom adapters can be built for extensive coverage of different systems, projects, organisations. In this guide we demonstrate how to create a GitHub app, so BER can be reached from your repository.

# Pre-requisites
 - Clone the `ber-os` repository
 - Create secret key
 - Deploy the BER project and serve it at <URL>

If you would like to know how to deploy and run the BER project please take a look at the Deployment documentation.

# Installation
In your developer settings you can create `GitHub Apps`. 

## Webhook
In order to connect with BER, do this:
 - Activate the webhook setting,
 - Set the value to `<URL>/api/v1/github/webhook`,
 - In order to use the webhook with SSL configure your secret key of your webhook. 

## Security
### Access token
You must add a private key that signs the access token requests 

## Display information and customisation
Optionally, you can add a logo, colors, description for the application. 
