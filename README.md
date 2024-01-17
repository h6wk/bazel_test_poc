# Bazel test databases running isolated

Find out how can test instances user their own database connection.

## Bazel sandboxing

Bazel sandboxes provide isolation, reproducibility, and security for the build process by creating controlled environments for each build target. This helps in maintaining consistency across different development environments and improves the efficiency of the build and test processes.

Here's a brief overview of how Bazel sandboxing works:
* Isolation: Bazel sandboxes are isolated environments that contain all the dependencies and tools necessary to build a specific target or rule. This isolation is achieved by creating a separate directory for each sandbox.

* Filesystem: Each sandbox has its own filesystem that includes the necessary input files, source code, and dependencies. This filesystem is isolated from the host system's filesystem to prevent any accidental contamination or interference.

* Environment: Bazel sets up a controlled environment inside the sandbox, including environment variables, to ensure that the build process has a predictable and consistent execution environment. This helps in reproducibility across different machines and ensures that builds are not affected by differences in the host environment.

* Caching: Bazel leverages caching to improve build performance. It can reuse previously built artifacts from the cache, which reduces the need to rebuild dependencies if they haven't changed. Sandboxing plays a crucial role in this caching mechanism because it ensures that the build is hermetically sealed and independent of the host system.

* Security: Sandboxing enhances the security of the build process. By isolating the build within a sandbox, Bazel can control which files and resources the build process can access. This minimizes the risk of malicious code or unintended access to sensitive files during the build.

* Reproducibility: Bazel aims to provide reproducibility by ensuring that builds are not affected by differences in the local development environment. Sandboxing contributes to this by encapsulating the build process and its dependencies.
