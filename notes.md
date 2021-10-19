# Notes on how this repository was populated

```
cd THISDIR
VERSION=v20.10.9
pushd ../..
git clone https://github.com/docker/cli.git
cd cli
CLI=$PWD
git checkout $VERSION
docker buildx bake --set binary.platform=darwin/amd64
docker buildx bake --set binary.platform=linux/amd64
docker buildx bake --set binary.platform=linux/arm64
# This fails on this branch:
if ! docker buildx bake --set binary.platform=windows/amd64 ; then
    # Apply this patch
    curl https://raw.githubusercontent.com/tiborvass/cli/83e9eeb8a08abd04a357c32f5fbf94129f569c71/scripts/build/binary >
      scripts/build/binary
    # This succeeds
    docker buildx bake --set binary.platform=windows/amd64
    git checkout scripts/build/binary
fi
sha256sum build/docker-* > build/sha256sum.txt
popd
mkdir -p releases/$VERSION

for file in $CLI/build/docker-* ; do
  cp $file releases/$VERSION/
done
git tag $VERSION
git push origin $VERSION
```
