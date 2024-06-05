---
title: DNS
layout: default
---
%% #-🪴weedy %%
[[Unsorted]]
# DNS setup

## Terminology

### Apex domain

An apex domain is a custom domain that does not contain a subdomain, such as example.com.
Apex domains are also known as base, bare, naked, root apex, or zone apex domains.
An apex domain is configured with an A , ALIAS , or ANAME record through your DNS provider.

## Record types

### A record

An A record (Address Record) points a domain or subdomain to an IP address. For example,
you can use it for store.website.com or blog.website.com and point it to where you have your store.

For example, an A Record is used to point a logical domain name, such as "google.com," to the IP address of Google's hosting server, "74.125.224.147".

#### Example

The following example shows the A records for the domain example.com:

- The domain itself (@) is pointed to the IP address 66.147.224.236.
- The subdomain ftp.example.com is also pointed to the IP address
- The subdomain localhost.example.com is a loopback address pointing to the local machine. This is useful for testing and development.

| Type | Name      | Value          | TTL  |
| ---- | --------- | -------------- | ---- |
| A    | @         | 66.147.224.236 | 3600 |
| A    | ftp       | 66.147.224.236 | 3600 |
| A    | localhost | 127.0.0.1      | 3600 |

### AAAA record

An AAAA record maps a domain to the IP address (IPv6) of the computer hosting the domain.

### CNAME record

A CNAME record maps a domain or subdomain to another domain, which is usually the domain
that is hosting the domain or subdomain.

## Debugging DNS

### Nslookup CLI

[nslookup](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup) is a command-line tool to discover the IP address or DNS record of a specific domain name. 
It also allows for reverse DNS lookup, letting you find the domain attached to an IP address.
The primary purpose of nslookup is to retrieve detailed information about the specified domain. 
This information is essential for troubleshooting DNS-related problems.

Example - To find the all DNS record types for `google.com`, run the following command in the terminal: 
```sh
nslookup -type=any google.com
```
