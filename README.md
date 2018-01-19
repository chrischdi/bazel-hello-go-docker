# Introduction

This repository and its content shows a small example of creating a bazel-builded go project.

# Hint:
Due to a bug inside the bazel rules according to python3 the normal bazel commands may not work.
As workaround you can set `export BAZEL_PYTHON=/usr/bin/python2` (or to any other python2 binary).

# step 1: [61183875](https://github.com/chrischdi/bazel-hello-go-docker/commit/61183875a45f0d5b6aed580b0826a5fcea2db944)
This steps adds a small hello-world application written in go.
The app can be built and run using `go run main.go`.

# step 2: [7211b4df](https://github.com/chrischdi/bazel-hello-go-docker/commit/7211b4df77e7e9f57589cbcf1ca879b4bd546ad8)
This step initializes the `WORKSPACE`-file with some basic definitions.

# step 3: [7f9f9304](https://github.com/chrischdi/bazel-hello-go-docker/commit/7f9f9304289e4e65c800fb6ee2fff7f12d7ec4b9)
Here we add the initial `BUILD.bazel`.
Now we are able to build the `main.go` for linux windows and darwin using a simple `bazel build //...`.

# step 4: [60f3f2b5](https://github.com/chrischdi/bazel-hello-go-docker/commit/60f3f2b537fdde9e18d355befe89e7d4eec86318)
This step adds the `bazel_rules_docker` and uses `go_image` to build a go image for the application.

The following snippet creates the image, loads it into docker and runs the container:
```
bazel build //:main_image.tar
docker load -i bazel-bin/main_image.tar
docker run bazel:main_image
```

