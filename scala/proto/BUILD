load("@io_bazel_rules_scala//scala_proto:scala_proto.bzl", "scala_proto_library")
load("@rules_proto//proto:defs.bzl", "proto_library")

proto_library(
    name = "proto_lib",
    srcs = ["some.proto"],
    deps = [],
)

scala_proto_library(
    name = "proto",
    deps = [":proto_lib"],
)

# toolchain deps

load("@io_bazel_rules_scala//scala/private/toolchains:toolchains.bzl", "declare_deps_provider", "declare_deps_toolchain")

declare_deps_provider(
    name = "scalapb_compile_deps_provider",
    visibility = ["//visibility:public"],
    deps = [
        "@com_lihaoyi_fastparse_2_12",
        "@com_thesamet_scalapb_lenses_2_12",
        "@com_thesamet_scalapb_scalapb_runtime_2_12",
        "@io_grpc_grpc_protobuf",
        "@org_scala_lang_scala_library",
    ],
)

declare_deps_provider(
    name = "scalapb_grpc_deps_provider",
    visibility = ["//visibility:public"],
    deps = [
        "@com_google_guava_guava",
        "@com_google_instrumentation_instrumentation_api",
        "@com_lmax_disruptor",
        "@com_thesamet_scalapb_scalapb_runtime_grpc_2_12",
        "@io_grpc_grpc_api",
        "@io_grpc_grpc_context",
        "@io_grpc_grpc_core",
        "@io_grpc_grpc_netty",
        "@io_grpc_grpc_protobuf",
        "@io_grpc_grpc_stub",
        "@io_netty_netty_buffer",
        "@io_netty_netty_codec",
        "@io_netty_netty_codec_http",
        "@io_netty_netty_codec_http2",
        "@io_netty_netty_codec_socks",
        "@io_netty_netty_common",
        "@io_netty_netty_handler",
        "@io_netty_netty_handler_proxy",
        "@io_netty_netty_resolver",
        "@io_netty_netty_transport",
        "@io_opencensus_opencensus_api",
        "@io_opencensus_opencensus_contrib_grpc_metrics",
        "@io_opencensus_opencensus_impl",
        "@io_opencensus_opencensus_impl_core",
        "@io_perfmark_perfmark_api",
    ],
)

declare_deps_toolchain(
    name = "proto_deps_toolchain_impl",
    dep_providers = {
        ":scalapb_compile_deps_provider": "compile_deps",
        ":scalapb_grpc_deps_provider": "grpc_deps",
    },
    visibility = ["//visibility:public"],
)

toolchain(
    name = "proto_deps_toolchain",
    toolchain = ":proto_deps_toolchain_impl",
    toolchain_type = "@io_bazel_rules_scala//scala_proto/toolchain:proto_toolchain_type",
    visibility = ["//visibility:public"],
)
