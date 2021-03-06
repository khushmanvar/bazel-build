load("@rules_jvm_external//:defs.bzl", "artifact")
load("@rules_android//android:rules.bzl", "android_library")

package(default_visibility = ["//visibility:private"])

PACKAGE = "com.bazel.general"
MANIFEST = "AndroidManifest.xml"

android_library(
    name = "bazel_res",
    custom_package = PACKAGE,
    manifest = MANIFEST,
    resource_files = glob(["res/**"]),
    enable_data_binding = False,
    deps = [
        artifact("androidx.constraintlayout:constraintlayout"),
        artifact("com.google.android.material:material"),
    ],
)

android_library(
    name = "bazel_java",
    srcs = glob(["java/**/*.java"]),
    deps = [
        ":bazel_res",
        artifact("androidx.appcompat:appcompat"),
        artifact("androidx.fragment:fragment"),
        artifact("androidx.core:core"),
        artifact("androidx.lifecycle:lifecycle-runtime"),
        artifact("androidx.lifecycle:lifecycle-viewmodel"),
        artifact("androidx.lifecycle:lifecycle-common"),
        artifact("androidx.drawerlayout:drawerlayout")
    ]
)

android_binary(
    name = "general",
    manifest = MANIFEST,
    custom_package = PACKAGE,
    manifest_values = {
        "minSdkVersion": "21",
        "versionCode" : "2",
        "versionName" : "0.2",
        "targetSdkVersion": "29",
    },
    deps = [
        ":bazel_res",
        ":bazel_java",
        artifact("androidx.appcompat:appcompat"),
    ],
)