### WORKSPACE
```
http_archive(
    name = "com_grail_bazel_compdb",
    strip_prefix = "bazel-compilation-database-0.3.0",
    urls = ["https://github.com/grailbio/bazel-compilation-database/archive/0.3.0.tar.gz"],
)

# load("@com_grail_bazel_compdb//:deps.bzl", "bazel_compdb_deps")
# bazel_compdb_deps()
```

### BUILD
```
# exec_root = bazel info execution_root
load("@com_grail_bazel_compdb//:aspects.bzl", "compilation_database")

compilation_database(
    name = "example_compdb",
    targets = [
              "//tensorflow/examples/label_image",
    ],
    # ideally should be the same as `bazel info execution_root`.
    exec_root = "/data01/home/mengshangqi.123/.cache/bazel/_bazel_mengshangqi.123/369c43b8cbd3f0070bef89d31a1b1c82/execroot/org_tensorflow",
)
```
