# docker-cli-release
Repo for building and releasing the Docker CLI for different platforms.

To create a populated release:

Get the tag of the docker CLI release you want to build on the CLI, e.g. "v20.10.10"

```bash
git tag v20.10.10
git push origin v20.10.10
```
Then go to https://github.com/rancher-sandbox/rancher-desktop-docker-cli/releases
and create a new release, with the following info:

Choose the tag (TAG) you just pushed.

Set the title and description to `Docker CLI builds for docker TAG`

Publish the release.

The github actions CI will build the binaries and populate the release.
