# docker-cli-release
Repo for building and releasing the Docker CLI for different platforms.

To create a populated release:

1. Get the tag of the docker CLI release you want to build, e.g. "v20.10.10" (called `TAG`)

1. Set the value of `DOCKER_CLI_REF` to the new tag in `.github/workflows/package.yaml`

1. `git add` and `git commit` the change with description
`Bump to use Docker CLI [TAG]`

1. `git tag TAG`

1. `git push origin main --tags`

1. Let the github packager do its thing

1. Then go build a release:

Go to https://github.com/rancher-sandbox/rancher-desktop-docker-cli/releases
and create a new release, and tell it to create the tag `TAG`.

Set the title and description to `Docker CLI builds for docker TAG`

Publish the release. This has to be a final release, not a draft release,
so for a while it will be visible without the associated binaries
until the github actions build, upload, and attach them.
