%% #-🪴weedy %%
[[Unsorted]]
# Docker

## CLI commands

### Build Docker Image

To build the docker image with the `Dockerfile` in the current path, run the following command:

```sh
docker build -t <image-name> .
```

### Build Docker Image with Dockerfile in different path

To build the docker image with the `Dockerfile` in a specific path, run the following command:

```sh
docker build -t <image-name> -f <dockerfile-path> .
```

### Build Docker Image with Build Arguments

To build the docker image, while overriding the build arguments, run the following command:

```sh
docker build -t <image-name> --build-arg "<key>=<value>" .
```
