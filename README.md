# What and why

Bazel is a modern build system with better performance characteristics 
and correctness guarantees than make/go build.

## generate BUILD files for src codes.
```shell
gazelle -go_prefix github.com/crrow/bazel-go
```

## Define external dependencies by gazelle update-repo
```shell
gazelle update-repos -from_file=go.mod -to_macro=DEPS.bzl%go_dependencies -prune
```

## Build src Files and Run the Application
```shell
bazel build //...
```

## Run application with bazel
```shell
bazel run //cmd/hello
```

# TODO
1. Migrating your external dependencies from WORKSPACE to MODULE.bazel.
2. Use [bazelisk](https://github.com/bazelbuild/bazelisk), A user-friendly launcher for Bazel.

# Some bazel usage
1. [Cockroach](https://github.com/cockroachdb/cockroach), they use bazel to build their project,
they also wrote a [blog](https://cockroachlabs.atlassian.net/wiki/spaces/CRDB/pages/2221703221/Developing+with+Bazel) about how they use bazel.
