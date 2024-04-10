# What and why

Bazel is a modern build system with better performance characteristics 
and correctness guarantees than make/go build.

## Regenerating BUILDfiles

```shell
bazel run //:gazelle
```

## Updating and adding new dependencies

Add a Go dependency to your code, then:

```shell
go mod tidy
bazel run //:gazelle-update-repos
```

All generated sources (eg. protobuf stubs) that are usually built by Bazel
are invisible to go(mod)-based tooling.

To get around this, we place `gomod-generated-placeholder.go` files in package 
directories that would otherwise contain generated files.
These are ignored by Gazelle (and thus by Bazel builds) but not by go(mod)-based tooling.


