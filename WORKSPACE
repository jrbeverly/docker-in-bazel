workspace(name = "cardboardci")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")
load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
load(
    "@io_bazel_rules_docker//repositories:go_repositories.bzl",
    container_go_deps = "go_deps",
)
load("@io_bazel_rules_docker//container:pull.bzl", "container_pull")

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "14ac30773fdb393ddec90e158c9ec7ebb3f8a4fd533ec2abbfd8789ad81a284b",
    strip_prefix = "rules_docker-0.12.1",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.12.1/rules_docker-v0.12.1.tar.gz"],
)

container_repositories()

container_go_deps()

container_pull(
    name = "ci_core",
    registry = "l.gcr.io",
    repository = "google/ubuntu1604",
    tag = "latest",
)

http_file(
    name = "gcloud_archive",
    downloaded_file_path = "google-cloud-sdk.tar.gz",
    sha256 = "a2205e35b11136004d52d47774762fbec9145bf0bda74ca506f52b71452c570e",
    urls = [
        "https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-220.0.0-linux-x86_64.tar.gz",
    ],
)
