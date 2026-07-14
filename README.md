# alpine-rsync

A minimal Docker image based on Alpine Linux with `rsync` installed.

## Overview

This repository provides a small container image for running `rsync` in lightweight Alpine-based environments. It is useful for file synchronization tasks in CI/CD pipelines, containers (e.g. sidecars), or simple deployment workflows.

## Image Contents

- Base image: `alpine:3.20.1` (configurable through build arguments)
- Installed package: `rsync`

## Build

To build the container image locally:

```bash
docker build -t alpine-rsync ./image
```

To build with a custom Alpine version or tag:

```bash
docker build --build-arg IMAGE=alpine --build-arg TAG=3.20.1 -t alpine-rsync ./image
```

## Image registry

The published image is available from GitHub Container Registry at:

```text
ghcr.io/dominik-ba/alpine-rsync:latest
```

Pull the image directly from GHCR:

```bash
docker pull ghcr.io/dominik-ba/alpine-rsync:latest
```

## Run

Run the container and verify `rsync` is available:

```bash
docker run --rm ghcr.io/dominik-ba/alpine-rsync:latest rsync --version
```

## Example usage

Use `rsync` from the image for local or remote synchronization:

```bash
docker run --rm -v "$PWD":/src alpine-rsync rsync -av /src/ /dst/
```

Replace `/dst/` with your target directory or mount a remote destination from the host.

## License

This project is licensed under the terms of the `LICENSE` file.
