# hegel-cpp overlay

The files in `overlay/` are the upstream repository's own Bazel build
(`MODULE.bazel`, `BUILD.bazel`, `libhegel/`, `third_party/`), copied
verbatim from https://github.com/hegeldev/hegel-cpp. They are shipped as
a registry overlay because the `v0.11.6` release tag predates the commits
that added the Bazel build to the repository.

Differences from a plain copy of the upstream tree:

- `MODULE.bazel` adds `bazel_compatibility = [">=7.2.1"]` (registry
  overlays require Bazel 7.2.1+).
- The test packages (`tests/`) and the build files for the test-only
  dependencies (`third_party/googletest.BUILD`,
  `third_party/approvaltests.BUILD`) are omitted: they are declared as
  dev dependencies in `MODULE.bazel` and are not resolvable when the
  module is consumed as a dependency.

Once a release containing the Bazel build is tagged upstream, future
versions of this module can drop the overlay.
