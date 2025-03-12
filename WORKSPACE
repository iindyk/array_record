workspace(name = "array_record")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
        name = "bazel_skylib",
        urls = [
            "https://storage.googleapis.com/mirror.tensorflow.org/github.com/bazelbuild/bazel-skylib/releases/download/1.3.0/bazel-skylib-1.3.0.tar.gz",
            "https://github.com/bazelbuild/bazel-skylib/releases/download/1.3.0/bazel-skylib-1.3.0.tar.gz",
        ],
    )

git_repository(
    name = "rules_python",
    remote = "https://github.com/bazelbuild/rules_python.git",
    tag = "0.5.0",
)

http_archive(
        name = "rules_license",
        urls = [
            "https://mirror.bazel.build/github.com/bazelbuild/rules_license/releases/download/0.0.7/rules_license-0.0.7.tar.gz",
            "https://github.com/bazelbuild/rules_license/releases/download/0.0.7/rules_license-0.0.7.tar.gz",
        ],
    )

http_archive(
        name = "rules_pkg",
        urls = [
            "https://mirror.bazel.build/github.com/bazelbuild/rules_pkg/releases/download/0.7.1/rules_pkg-0.7.1.tar.gz",
            "https://github.com/bazelbuild/rules_pkg/releases/download/0.7.1/rules_pkg-0.7.1.tar.gz",
        ],
    )

# Abseil LTS 20230125.0
http_archive(
    name = "com_google_absl",
    strip_prefix = "abseil-cpp-20230802.1",
    urls = [
        "https://github.com/abseil/abseil-cpp/archive/refs/tags/20230802.1.tar.gz",
    ],
)

# Version: pypi-v0.11.0, 2020/10/27
git_repository(
    name = "com_google_absl_py",
    commit = "127c98870edf5f03395ce9cf886266fa5f24455e",
    remote = "https://github.com/abseil/abseil-py",
    shallow_since = "1673401277 -0800",
)

# Needed by com_google_riegeli
http_archive(
    name = "org_brotli",
    strip_prefix = "brotli-3914999fcc1fda92e750ef9190aa6db9bf7bdb07",
    urls = ["https://github.com/google/brotli/archive/3914999fcc1fda92e750ef9190aa6db9bf7bdb07.zip"],  # 2022-11-17
)

# GoogleTest/GoogleMock framework. Used by most unit-tests.
http_archive(
    name = "com_google_googletest",
    strip_prefix = "googletest-main",
    urls = ["https://github.com/google/googletest/archive/main.zip"],
)

# V3.4.0, 20210818
http_archive(
    name = "eigen3",
    build_file_content =
        """
cc_library(
    name = 'eigen3',
    srcs = [],
    includes = ['.'],
    hdrs = glob(['Eigen/**', 'unsupported/Eigen/**']),
    visibility = ['//visibility:public'],
)
""",
    strip_prefix = "eigen-3.4.0",
    urls = [
        "https://gitlab.com/libeigen/eigen/-/archive/3.4.0/eigen-3.4.0.tar.bz2",
    ],
)

# `pybind11_bazel` (https://github.com/pybind/pybind11_bazel): 20230130
http_archive(
    name = "pybind11_bazel",
    strip_prefix = "pybind11_bazel-5f458fa53870223a0de7eeb60480dd278b442698",
    urls = ["https://github.com/pybind/pybind11_bazel/archive/5f458fa53870223a0de7eeb60480dd278b442698.tar.gz"],
)

# V2.10.3, 20230130
http_archive(
    name = "pybind11",
    build_file = "@pybind11_bazel//:pybind11.BUILD",
    strip_prefix = "pybind11-2.10.3",
    urls = ["https://github.com/pybind/pybind11/archive/refs/tags/v2.10.3.zip"],
)

load("@pybind11_bazel//:python_configure.bzl", "python_configure")

python_configure(name = "local_config_python")

# proto_library, cc_proto_library, and java_proto_library rules implicitly
# depend on @com_google_protobuf for protoc and proto runtimes.
# This statement defines the @com_google_protobuf repo.
http_archive(
    name = "com_google_protobuf",
    strip_prefix = "protobuf-3.21.9",
    urls = ["https://github.com/protocolbuffers/protobuf/archive/v3.21.9.zip"],
)

load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")

protobuf_deps()

http_archive(
    name = "com_google_riegeli",
    strip_prefix = "riegeli-254e6d74ee0d325676739fe5075e5a1a895624cf",
    urls = [
        "https://github.com/google/riegeli/archive/254e6d74ee0d325676739fe5075e5a1a895624cf.tar.gz",
    ],
)

# Riegeli's dependencies
http_archive(
    name = "net_zstd",
    build_file = "@com_google_riegeli//third_party:net_zstd.BUILD",
    strip_prefix = "zstd-1.4.5/lib",
    urls = ["https://github.com/facebook/zstd/archive/v1.4.5.zip"],  # 2020-05-22
)

http_archive(
    name = "lz4",
    build_file = "@com_google_riegeli//third_party:lz4.BUILD",
    strip_prefix = "lz4-1.9.3/lib",
    urls = ["https://github.com/lz4/lz4/archive/refs/tags/v1.9.3.zip"],  # 2020-11-16
)

http_archive(
    name = "snappy",
    build_file = "@com_google_riegeli//third_party:snappy.BUILD",
    strip_prefix = "snappy-1.2.0",
    urls = ["https://github.com/google/snappy/archive/1.2.0.zip"],  # 2024-04-04
)

http_archive(
    name = "crc32c",
    build_file = "@com_google_riegeli//third_party:crc32.BUILD",
    strip_prefix = "crc32c-1.1.0",
    urls = ["https://github.com/google/crc32c/archive/1.1.0.zip"],  # 2019-05-24
)

http_archive(
    name = "zlib",
    build_file = "@com_google_riegeli//third_party:zlib.BUILD",
    strip_prefix = "zlib-1.2.11",
    urls = ["http://zlib.net/fossils/zlib-1.2.11.tar.gz"],  # 2017-01-15
)

http_archive(
    name = "highwayhash",
    build_file = "@com_google_riegeli//third_party:highwayhash.BUILD",
    strip_prefix = "highwayhash-a7f68e2f95fac08b24327d74747521cf634d5aff",
    urls = ["https://github.com/google/highwayhash/archive/a7f68e2f95fac08b24327d74747521cf634d5aff.zip"],  # 2023-08-09
)

# Tensorflow, 20230705
http_archive(
    name = "org_tensorflow",
    strip_prefix = "tensorflow-2.12.1",
    urls = ["https://github.com/tensorflow/tensorflow/archive/v2.12.1.zip"],
)

load("@org_tensorflow//tensorflow/tools/toolchains:cpus/aarch64/aarch64_compiler_configure.bzl", "aarch64_compiler_configure")  # buildifier: disable=load-on-top

# This import (along with the org_tensorflow archive) is necessary to provide the devtoolset-9 toolchain
load("@org_tensorflow//tensorflow/tools/toolchains/remote_config:configs.bzl", "initialize_rbe_configs")  # buildifier: disable=load-on-top

initialize_rbe_configs()

aarch64_compiler_configure()
