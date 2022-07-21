# docker-cli-release
Repo for building and releasing the Docker CLI for different platforms.

## Creating a populated release:

1. Get the tag of the docker CLI release you want to build, e.g. "v20.10.10" (called `TAG`)

1. `git tag TAG` (from whatever `main` is).

1. `git push origin refs/tags/${TAG}`.

1. Let GitHub CI do its thing.  This will generate a draft release.

1. Then go build a release:

Go to https://github.com/rancher-sandbox/rancher-desktop-docker-cli/releases
and edit the draft release.

## Manually triggering builds

It's possible to manually trigger a build (via GitHub Actions, manually use the
_Run workflow_ button); builds triggered this way will not create a draft
release.