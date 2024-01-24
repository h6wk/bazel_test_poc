# Run bazel test with their own database

This is a project that will set up google tests that were executed using the bazel sandboxing concept. The tests or (suites) will have their own databases. The databases will run in a container that is pulled in dynamically into the sandbox (on demand).

## Bazel sandboxing

Bazel sandboxes provide isolation, reproducibility, and security for the build process by creating controlled environments for each build target. This helps in maintaining consistency across different development environments and improves the efficiency of the build and test processes.

Here's a brief overview of how Bazel sandboxing works:
* Isolation: Bazel sandboxes are isolated environments that contain all the dependencies and tools necessary to build a specific target or rule. This isolation is achieved by creating a separate directory for each sandbox.

* Filesystem: Each sandbox has its own filesystem that includes the necessary input files, source code, and dependencies. This filesystem is isolated from the host system's filesystem to prevent any accidental contamination or interference.

* Environment: Bazel sets up a controlled environment inside the sandbox, including environment variables, to ensure that the build process has a predictable and consistent execution environment. This helps in reproducibility across different machines and ensures that builds are not affected by differences in the host environment.

* Caching: Bazel leverages caching to improve build performance. It can reuse previously built artifacts from the cache, which reduces the need to rebuild dependencies if they haven't changed. Sandboxing plays a crucial role in this caching mechanism because it ensures that the build is hermetically sealed and independent of the host system.

* Security: Sandboxing enhances the security of the build process. By isolating the build within a sandbox, Bazel can control which files and resources the build process can access. This minimizes the risk of malicious code or unintended access to sensitive files during the build.

* Reproducibility: Bazel aims to provide reproducibility by ensuring that builds are not affected by differences in the local development environment. Sandboxing contributes to this by encapsulating the build process and its dependencies.

# Bazelisk

Getting started with C++: https://bazel.build/start/cpp


# Set up a WORKSPACE for Google Tests

https://google.github.io/googletest/quickstart-bazel.html


# Use rules_docker

https://github.com/bazelbuild/rules_docker/releases

## Examples

### The rules_docker example folder

Folder: rules_docker/testing/examples

### Create container images with bazel

https://dev.to/schoren/create-container-images-with-bazel-47am

Issue:
```console
ERROR: /home/vscode/.cache/bazel/_bazel_vscode/6d7f2dfd87d2c738b7d62f9bf776efb1/external/io_bazel_rules_docker/platforms/BUILD:78:9: in constraint_values attribute of platform rule @@io_bazel_rules_docker//platforms:image_transition: '@@io_bazel_rules_docker//platforms:image_transition_cpu' does not have mandatory providers: 'ConstraintValueInfo'
```

# Bazel targets and main commands

## Targets

```console
$ bazel query //...
//:app
//:hello_test
```

## Clean

```console
$ bazel clean
```

## Build

```console
$ bazel build //...
INFO: Analyzed 2 targets (69 packages loaded, 388 targets configured).
INFO: Found 2 targets...
INFO: Elapsed time: 10.488s, Critical Path: 9.68s
INFO: 34 processes: 13 internal, 21 linux-sandbox.
INFO: Build completed successfully, 34 total actions
```

## Run

```console
$ bazel run //...
INFO: Analyzed target //:app (66 packages loaded, 302 targets configured).
INFO: Found 1 target...
Target //:app up-to-date:
  bazel-bin/app
INFO: Elapsed time: 0.649s, Critical Path: 0.00s
INFO: 1 process: 1 internal.
INFO: Build completed successfully, 1 total action
INFO: Running command line: bazel-bin/app
Hello Bazel!
```

## Test

```console
$ bazel test //...
INFO: Analyzed 2 targets (0 packages loaded, 0 targets configured).
INFO: Found 1 target and 1 test target...
INFO: Elapsed time: 0.232s, Critical Path: 0.07s
INFO: 2 processes: 1 internal, 1 linux-sandbox.
INFO: Build completed successfully, 2 total actions
//:hello_test                                                            PASSED in 0.0s

Executed 1 out of 1 test: 1 test passes.
```
