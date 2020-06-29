workspace(name = "scala_unused_deps")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("//tools/jdk:jdks.bzl", "jdk_repositories")

jdk_repositories()

# bazel-skylib 0.8.0 released 2019.03.20 (https://github.com/bazelbuild/bazel-skylib/releases/tag/0.8.0)
skylib_version = "0.8.0"

http_archive(
    name = "bazel_skylib",
    sha256 = "2ef429f5d7ce7111263289644d233707dba35e39696377ebab8b0bc701f7818e",
    type = "tar.gz",
    url = "https://github.com/bazelbuild/bazel-skylib/releases/download/{}/bazel-skylib.{}.tar.gz".format(skylib_version, skylib_version),
)

rules_scala_version = "fad57c6a321311cdd102459b1ecc081ec809aa9c"

http_archive(
    name = "io_bazel_rules_scala",
    sha256 = "47afe3694a146e980d55b905525c9fe5f3484606f34e30591bd1d022f545daf7",
    strip_prefix = "rules_scala-%s" % rules_scala_version,
    type = "zip",
    url = "https://github.com/liucijus/rules_scala/archive/%s.zip" % rules_scala_version,
)

load("@io_bazel_rules_scala//scala:toolchains.bzl", "scala_register_toolchains")

scala_register_toolchains()

load("@io_bazel_rules_scala//scala:scala.bzl", "scala_repositories")

scala_repositories()

protobuf_version = "3.11.3"

protobuf_version_sha256 = "cf754718b0aa945b00550ed7962ddc167167bd922b842199eeb6505e6f344852"

http_archive(
    name = "com_google_protobuf",
    sha256 = protobuf_version_sha256,
    strip_prefix = "protobuf-%s" % protobuf_version,
    url = "https://github.com/protocolbuffers/protobuf/archive/v%s.tar.gz" % protobuf_version,
)

load("@io_bazel_rules_scala//scala_proto:scala_proto.bzl", "scala_proto_repositories")

scala_proto_repositories()

load("@io_bazel_rules_scala//scala_proto:toolchains.bzl", "scala_proto_register_toolchains")

scala_proto_register_toolchains()

register_toolchains("//scala/proto:proto_deps_toolchain")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

RULES_JVM_EXTERNAL_TAG = "3.2"

RULES_JVM_EXTERNAL_SHA = "82262ff4223c5fda6fb7ff8bd63db8131b51b413d26eb49e3131037e79e324af"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")
load("@rules_jvm_external//:specs.bzl", "maven")

maven_install(
    artifacts = [
        "org.scala-lang:scala-library:jar:2.12.11",
        "org.scala-lang:scala-reflect:jar:2.12.11",
        "org.scala-lang:scala-compiler:jar:2.12.11",

        # proto
        "com.thesamet.scalapb:compilerplugin_2.12:0.9.7",
        "com.thesamet.scalapb:protoc-bridge_2.12:0.7.14",
        "com.thesamet.scalapb:scalapbc_2.12:0.9.7",
        "com.thesamet.scalapb:scalapb-runtime_2.12:0.9.7",
        "com.thesamet.scalapb:scalapb-runtime-grpc_2.12:0.9.7",
        "com.thesamet.scalapb:lenses_2.12:0.9.7",
        "com.lihaoyi:fastparse_2.12:2.1.3",
        "io.grpc:grpc-core:1.24.0",
        "io.grpc:grpc-api:1.24.0",
        "io.grpc:grpc-protobuf:1.24.0",
        "io.grpc:grpc-netty:1.24.0",
        "io.grpc:grpc-context:1.24.0",
        "io.perfmark:perfmark-api:0.17.0",
        "com.google.guava:guava:26.0-android",
        "com.google.instrumentation:instrumentation-api:0.3.0",
        "io.netty:netty-codec:4.1.32.Final",
        "io.netty:netty-codec-http:4.1.32.Final",
        "io.netty:netty-codec-socks:4.1.32.Final",
        "io.netty:netty-codec-http2:4.1.32.Final",
        "io.netty:netty-handler:4.1.32.Final",
        "io.netty:netty-buffer:4.1.32.Final",
        "io.netty:netty-transport:4.1.32.Final",
        "io.netty:netty-resolver:4.1.32.Final",
        "io.netty:netty-common:4.1.32.Final",
        "io.netty:netty-handler-proxy:4.1.32.Final",
        "io.opencensus:opencensus-api:0.22.1",
        "io.opencensus:opencensus-impl:0.22.1",
        "com.lmax:disruptor:3.4.2",
        "io.opencensus:opencensus-impl-core:0.22.1",
        "io.opencensus:opencensus-contrib-grpc-metrics:0.22.1",

        # additional
        #        "org.scalameta:common_2.12:jar:4.3.0",
        #        "org.scalameta:fastparse_2.12:jar:1.0.1",
        #        "org.scalameta:fastparse-utils_2.12:jar:1.0.1",
        #        "org.scala-lang.modules:scala-collection-compat_2.12:jar:2.1.2",
        #        "org.scalameta:parsers_2.12:jar:4.3.0",
        #        "org.scalameta:scalafmt-core_2.12:jar:2.3.2",
        #        "org.scalameta:scalameta_2.12:jar:4.3.0",
        #        "org.scalameta:trees_2.12:jar:4.3.0",
        #        "org.typelevel:paiges-core_2.12:jar:0.2.4",
        #        "com.typesafe:config:1.3.3",
        #        "org.scala-lang:scalap:jar:2.11.12",
        #        "com.thesamet.scalapb:lenses_2.12:jar:0.9.0",
        #        "com.thesamet.scalapb:scalapb-runtime_2.12:jar:0.9.0",
        #        "com.lihaoyi:fansi_2.12:jar:0.2.5",
        #        "com.lihaoyi:pprint_2.12:jar:0.5.3",
        #        "com.lihaoyi:sourcecode_2.12:jar:0.1.7",
        #        "com.google.protobuf:protobuf-java:3.10.0",
        #        "com.geirsson:metaconfig-core_2.12:jar:0.9.4",
        #        "com.geirsson:metaconfig-typesafe-config_2.12:jar:0.9.4",
    ],
    fetch_sources = True,
    generate_compat_repositories = True,
    maven_install_json = "@//:maven_install.json",
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

load("@maven//:defs.bzl", "pinned_maven_install")

pinned_maven_install()

load("@maven//:compat.bzl", "compat_repositories")

compat_repositories()
