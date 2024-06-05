---
title: Docker Images
layout: default
---
%% #-🪴weedy %%
[[Unsorted]]
# Docker images

## Alpine Linux

[Alpine Linux](https://hub.docker.com/_/alpine) is a Linux distribution built around musl libc and BusyBox. The image is only 5MB and has access to a package repository that is much more complete than other BusyBox based images.
The small footprint of the image makes it an ideal candidate for [init containers](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/). 


## Busybox

[Busybox](https://hub.docker.com/_/busybox) combines tiny versions of many common UNIX utilities into a single small executable. It provides replacements for most of the utilities you usually find in GNU fileutils, shellutils, etc. The utilities in BusyBox generally have fewer options than their full-featured GNU cousins; however, the options that are included provide the expected functionality and behave very much like their GNU counterparts. BusyBox provides a fairly complete environment for any small or embedded system.

### Use case

Init containers can contain scripts or other utilities outside the application image. Initializing these “regular” containers may depend on k8s spinning up these components first. But they always run synchronously and until their tasks finish.

But what can you use an initContainer for? According to the k8s documentation, you can:
- Wait for a Service to be created as Pods spin up
- Register a Pod with a remote server from an API
- Wait for an allotted period before finally starting an app container
- Clone a Git repo into a volume
- Generate configuration files automatically from value inputs
