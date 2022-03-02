load("@npm//@bazel/typescript:index.bzl", "ts_project")
load("@build_bazel_rules_nodejs//:index.bzl", "js_library")
load("@npm//jest-cli:index.bzl", "jest_test")

ts_project(
    name = "a",
    srcs = ["a.js"],
    allow_js = True,
    declaration = True,
    extends = "//:tsconfig.json",
    tsconfig = {},
)

ts_project(
    name = "b",
    srcs = ["b.ts"],
    extends = "//:tsconfig.json",
        declaration=True,
    tsconfig = {},
    deps = [
        ":a",
        "@npm//@types",
    "@npm//tslib",
    ],
)

ts_project(
    name = "test_b",
    srcs = ["b.test.ts"],
    extends = "//:tsconfig.json",
        declaration=True,
    tsconfig = {},
    deps = [
        ":b",
        "@npm//@types",
    "@npm//tslib",
    ],
)

jest_test(
    name = "test",
    args = [
        "--no-cache",
        "--no-watchman",
        "--ci",
        "--colors",
        "--config",
        "jest.config.js",
    ],
    data = [
        ":test_b",
        "//:jest.config.js",
    ],
)
