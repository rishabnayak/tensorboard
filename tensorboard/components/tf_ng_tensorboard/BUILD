package(default_visibility = ["//tensorboard:internal"])

load("@npm_angular_bazel//:index.bzl", "ng_module")
load("//tensorboard/defs:defs.bzl", "tf_js_binary")
load("//tensorboard/defs:web.bzl", "tf_web_library")

licenses(["notice"])  # Apache 2.0

tf_web_library(
    name = "tf_ng_tensorboard",
    srcs = [
        ":tf_ng_tensorboard_binary.js",
        "@npm//:node_modules/zone.js/dist/zone.js",
    ],
    path = "/tf-ng-tensorboard",
    deps = [
        ":tf_ng_tensorboard_binary",
    ],
)

# TODO(stephanwlee): move this to root level
tf_web_library(
    name = "material_theme",
    srcs = [
        "@npm//:node_modules/@angular/material/prebuilt-themes/indigo-pink.css",
    ],
    path = "/@angular",
    strip_prefix = "node_modules/@angular/material/prebuilt-themes",
)

tf_js_binary(
    name = "tf_ng_tensorboard_binary",
    compile = 1,
    entry_point = ":main.ts",
    deps = [
        ":ng_main",
        "@npm//@angular/common",
        "@npm//@angular/core",
        "@npm//@angular/material",
        "@npm//@angular/platform-browser",
        "@npm//@ngrx/store",
        "@npm//rxjs",
        "@npm//zone.js",
    ],
)

ng_module(
    name = "ng_main",
    srcs = [
        "main.ts",
    ],
    deps = [
        ":app",
        "@npm//@angular/core",
        "@npm//@angular/platform-browser",
        "@npm//@angular/router",
        "@npm//zone.js",
    ],
)

ng_module(
    name = "app",
    srcs = [
        "app.component.ts",
        "app.module.ts",
        "reducers.ts",
    ],
    assets = [
        "app.component.css",
        "app.component.html",
    ],
    deps = [
        "//tensorboard/components/tf_ng_tensorboard/core",
        "//tensorboard/components/tf_ng_tensorboard/header",
        "@npm//@angular/core",
        "@npm//@angular/platform-browser",
        "@npm//@ngrx/store",
    ],
)
