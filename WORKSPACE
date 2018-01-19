http_archive(
    name = "io_bazel_rules_go",
    url = "https://github.com/bazelbuild/rules_go/releases/download/0.9.0/rules_go-0.9.0.tar.gz",
    sha256 = "4d8d6244320dd751590f9100cf39fd7a4b75cd901e1f3ffdfd6f048328883695",
)

load("@io_bazel_rules_go//go:def.bzl", "go_rules_dependencies", "go_register_toolchains", "go_toolchain")
go_rules_dependencies()
go_register_toolchains()

local_repository(
    name = "io_bazel_rules_docker",
		path = "/home/christi/git/rules_docker",
)

load("@io_bazel_rules_docker//go:image.bzl", container_repositories = "repositories")
container_repositories()
