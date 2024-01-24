load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

#### For GTEST:

http_archive(
  name = "com_google_googletest",
  urls = ["https://github.com/google/googletest/archive/5ab508a01f9eb089207ee87fd547d290da39d015.zip"],
  strip_prefix = "googletest-5ab508a01f9eb089207ee87fd547d290da39d015",
)

#### For DOCKER:

# Pull rules_docker into bazel
# The last release: https://github.com/bazelbuild/rules_docker/releases
http_archive(
  name = "io_bazel_rules_docker",
  sha256 = "27d53c1d646fc9537a70427ad7b034734d08a9c38924cc6357cc973fed300820",
  strip_prefix = "rules_docker-0.24.0",
  urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.24.0/rules_docker-v0.24.0.tar.gz"],
)


#### Docker rules:


load("@io_bazel_rules_docker//repositories:repositories.bzl", container_repositories = "repositories")
container_repositories()


load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")
container_deps()


load("@io_bazel_rules_docker//container:pull.bzl", "container_pull")
container_pull(
  name = "alpine_linux_amd64",
  registry = "index.docker.io",
  repository = "library/alpine",
  # digest = "sha256:954b378c375d852eb3c63ab88978f640b4348b01c1b3456a024a81536dafbbf4",
  # tag field is ignored if digest was set
  tag = "3.8",
)


#load("@io_bazel_rules_docker//contrib:dockerfile_build.bzl", "dockerfile_image")
#
#dockerfile_image(
#  name = "basic_alpine_dockerfile",
#  dockerfile = "//docker:Dockerfile",
#)

