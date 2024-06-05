---
title: NGrok
layout: default
---
%% #-🪴weedy %%
[[Unsorted]]
# Ngrok
![Ngrok logo](../../assets/images/ngrok-logo.png)

[NGrok](https://ngrok.com/docs/what-is-ngrok/) is a globally distributes reverse proxy service for exposing local endpoints to the public internet.
It acts like a front door / proxy that receives traffic and delivers it forward to configured upstream services. This is achieved by running a
lightweight agent on your local machine, which connects to the NGrok endpoint via TLS. All traffic to this endpoint is delivered to the agent,
and finally to the upstream service.

## Setup

Follow the [instructions](https://dashboard.ngrok.com/get-started/setup/windows) to setup NGrok on your local machine,
and establish a connection to the NGrok endpoint.

## Running NGrok

1. Start the target application's web server on your local machine.
2. Run ngrok with one of the following commands:

### HTTP / HTTPS (unauthenticated)

```sh
> ngrok http https://localhost:3001
```

### HTTP / HTTPS (Basic auth)

```sh
> ngrok http https://localhost:3001 --basic-auth="testuser:-T3stUserr1234#"
```


### HTTP / HTTPS (OAuth2)

```sh
> ngrok http https://localhost:3001 --oauth=google --oauth-allow-email=<allowed-email-address>
```

### HTTP with custom domain

Custom domain support requires a paid plan. Use the ngrok-dashboard to configure a custom domain
name, and then add the `CNAME` settings to the DNS records.

```sh
> ngrok http --domain=<domain-name> <local-server-url>
```