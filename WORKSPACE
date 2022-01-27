workspace(name="example")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_JVM_EXTERNAL_TAG = "3.2"

RULES_JVM_EXTERNAL_SHA = "82262ff4223c5fda6fb7ff8bd63db8131b51b413d26eb49e3131037e79e324af"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    name = "maven",
    artifacts = [
        "org.apache.thrift:libthrift:0.12.0",
    ],
    fetch_sources = True,
    repositories = [
        "https://repo1.maven.org/maven2",
    ],
    maven_install_json = "//:maven_install.json",
)

load("@maven//:defs.bzl", "pinned_maven_install")
pinned_maven_install()

load("@rules_jvm_external//:specs.bzl", "maven")

maven_install(
name = "special",
    artifacts = [
        "junit:junit:4.12",
        "com.google.guava:guava:28.0-jre",
        "org.apache.commons:commons-compress:1.8.1",
        maven.artifact(group = "com.fasterxml.jackson.core", artifact = "jackson-databind", version = "2.7.9.4",
        ),
    ],
    fetch_sources = True,
    repositories = [
        "https://jcenter.bintray.com/",
    ],
    maven_install_json = "//:special_install.json",
)

load("@special//:defs.bzl", special_pin = "pinned_maven_install")
pinned_maven_install()


