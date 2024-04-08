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
bazel run //cmd
```

# TODO
Use bazelisk, A user-friendly launcher for Bazel.