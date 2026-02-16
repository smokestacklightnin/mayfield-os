# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

**Mayfiled OS** — a custom Linux desktop image based on Universal Blue Aurora (Fedora Atomic KDE), built using [BlueBuild](https://blue-build.org/). The image is published as an OCI container to GitHub Container Registry (GHCR) via GitHub Actions, and endpoints receive atomic updates by pulling new image versions.

## Goals

- BlueBuild recipe (`recipe.yml`) defining the base image, packages, and customizations
- GitHub Actions workflow to build and push the image on every push to `main`
- ISO generation via [Universal Blue isogenerator](https://github.com/ublue-os/isogenerator) for initial laptop installation
- User account creation during installation via Anaconda installer

## Build Commands

```bash
# Build locally (requires podman or docker)
bluebuild build recipe.yml

# Validate recipe
bluebuild validate recipe.yml
```

## Key Conventions

- Base image: Universal Blue Aurora (Fedora Atomic / KDE)
- Image name: `mayfiled-os`
- Recipe format: [BlueBuild module spec](https://blue-build.org/reference/module/)
- Registry: GitHub Container Registry (`ghcr.io`)
- Installer: Anaconda (Fedora default) — handles user account creation
- CI: GitHub Actions using `blue-build/github-action` with `GITHUB_TOKEN` for GHCR auth
