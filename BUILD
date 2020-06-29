load("@io_bazel_rules_scala//scala:scala.bzl", "scala_binary", "scala_library", "scala_test")
load("@io_bazel_rules_scala//scala:scala_toolchain.bzl", "scala_toolchain")
load("@io_bazel_rules_scala//scala:providers.bzl", "declare_scalac_provider")

scala_toolchain(
    name = "warn_unused_scala_toolchain",
    dependency_mode = "plus-one",
    dependency_tracking_method = "ast",
    strict_deps_mode = "warn",
    unused_dependency_checker_mode = "warn",
    visibility = ["//visibility:public"],
    scalac_provider_attr = ":scalac_provider",

)

toolchain(
    name = "unused_deps_toolchain",
    toolchain = "warn_unused_scala_toolchain",
    toolchain_type = "@io_bazel_rules_scala//scala:toolchain_type",
    visibility = ["//visibility:public"],
)

declare_scalac_provider(
    name = "scalac_provider",
    default_classpath = [
        "@org_scala_lang_scala_library",
        "@org_scala_lang_scala_reflect",
    ],
    default_macro_classpath = [
        "@org_scala_lang_scala_library",
        "@org_scala_lang_scala_reflect",
    ],
    default_repl_classpath = [
        "@org_scala_lang_scala_library",
        "@org_scala_lang_scala_reflect",
        "@org_scala_lang_scala_compiler",
    ],
)
