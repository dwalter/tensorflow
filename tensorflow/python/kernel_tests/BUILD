# Tests of TensorFlow kernels written using the Python API.

package(
    default_visibility = ["//tensorflow:internal"],
    features = [
        "-layering_check",
        "-parse_headers",
    ],
)

licenses(["notice"])  # Apache 2.0

load("//tensorflow:tensorflow.bzl", "py_tests")
load("//tensorflow:tensorflow.bzl", "cuda_py_tests")

py_library(
    name = "gradient_checker",
    srcs = ["gradient_checker.py"],
    srcs_version = "PY2AND3",
)

medium_kernel_test_list = [
    "concat_op_test.py",
    "division_future_test.py",
    "fft_ops_test.py",
    "pooling_ops_test.py",
    "rnn_test.py",
    "random_gamma_test.py",
    "scatter_ops_test.py",
    "seq2seq_test.py",
    "slice_op_test.py",
    "sparse_ops_test.py",
    "sparse_matmul_op_test.py",
    "sparse_tensor_dense_matmul_op_test.py",
]

sharded_kernel_test_list = [
    "batch_matrix_band_part_op_test.py",
    "cwise_ops_test.py",
    "embedding_ops_test.py",
    "linalg_grad_test.py",
    "conv_ops_3d_test.py",
]

cpu_only_kernel_test_list = [
    "attention_ops_test.py",
    "bcast_ops_test.py",
    "benchmark_test.py",
    "candidate_sampler_ops_test.py",
    "cholesky_op_test.py",
    "clip_ops_test.py",
    "decode_csv_op_test.py",
    "decode_png_op_test.py",
    "decode_raw_op_test.py",
    "determinant_op_test.py",
    "diag_op_test.py",
    "edit_distance_op_test.py",
    "fifo_queue_test.py",
    "identity_op_py_test.py",
    "in_topk_op_test.py",
    "io_ops_test.py",
    "listdiff_op_test.py",
    "logging_ops_test.py",
    "lrn_op_test.py",
    "matrix_inverse_op_test.py",
    "matrix_solve_op_test.py",
    "matrix_triangular_solve_op_test.py",
    "matrix_solve_ls_op_test.py",
    "parsing_ops_test.py",
    "partitioned_variables_test.py",
    "random_shuffle_queue_test.py",
    "save_restore_ops_test.py",
    "segment_reduction_ops_test.py",
    "self_adjoint_eig_op_test.py",
    "sparse_add_op_test.py",
    "sparse_concat_op_test.py",
    "sparse_split_op_test.py",
    "sparse_reorder_op_test.py",
    "sparse_reshape_op_test.py",
    "sparse_to_dense_op_py_test.py",
    "sparsemask_op_test.py",
    "summary_ops_test.py",
    "template_test.py",
    "topk_op_test.py",
    "unique_op_test.py",
    "variable_scope_test.py",
    "variables_test.py",
    "where_op_test.py",
]

py_tests(
    name = "cpu_only_kernel_tests",
    size = "small",
    srcs = cpu_only_kernel_test_list,
)

py_tests(
    name = "reader_ops_test",
    size = "small",
    srcs = ["reader_ops_test.py"],
    additional_deps = [
        "//tensorflow/python:lib",
    ],
)

cuda_py_tests(
    name = "kernel_tests",
    size = "small",
    srcs = [
        "argmax_op_test.py",
        "array_ops_test.py",
        "batch_matmul_op_test.py",
        "batchtospace_op_test.py",
        "bias_op_test.py",
        "bitcast_op_test.py",
        "cast_op_test.py",
        "check_ops_test.py",
        "constant_op_test.py",
        "control_flow_ops_py_test.py",
        "conv_ops_test.py",
        "cross_grad_test.py",
        "denormal_test.py",
        "dense_update_ops_no_tsan_test.py",
        "dense_update_ops_test.py",
        "depthtospace_op_test.py",
        "depthwise_conv_op_test.py",
        "division_past_test.py",
        "dynamic_partition_op_test.py",
        "dynamic_stitch_op_test.py",
        "extract_image_patches_op_test.py",
        "functional_ops_test.py",
        "gather_nd_op_test.py",
        "gather_op_test.py",
        "gradient_checker_test.py",
        "gradient_correctness_test.py",
        "init_ops_test.py",
        "linalg_ops_test.py",
        "matmul_op_test.py",
        "morphological_ops_test.py",
        "multinomial_op_test.py",
        "numerics_test.py",
        "one_hot_op_test.py",
        "pack_op_test.py",
        "pad_op_test.py",
        "padding_fifo_queue_test.py",
        "pooling_ops_3d_test.py",
        "py_func_test.py",
        "random_crop_test.py",
        "random_ops_test.py",
        "reduce_join_op_test.py",
        "reduction_ops_test.py",
        "relu_op_test.py",
        "reshape_op_test.py",
        "reverse_sequence_op_test.py",
        "rnn_cell_test.py",
        "scalar_strict_test.py",
        "session_ops_test.py",
        "shape_ops_test.py",
        "softmax_op_test.py",
        "softplus_op_test.py",
        "softsign_op_test.py",
        "spacetobatch_op_test.py",
        "spacetodepth_op_test.py",
        "sparse_serialization_ops_test.py",
        "sparse_tensor_dense_matmul_grad_test.py",
        "sparse_xent_op_test.py",
        "split_op_test.py",
        "stack_ops_test.py",
        "string_to_hash_bucket_op_test.py",
        "string_to_number_op_test.py",
        "summary_audio_op_test.py",
        "summary_image_op_test.py",
        "tensor_array_ops_test.py",
        "trace_op_test.py",
        "transpose_op_test.py",
        "unpack_op_test.py",
        "variable_ops_test.py",
        "xent_op_test.py",
        "zero_division_test.py",
    ],
)

cuda_py_tests(
    name = "medium_kernel_tests",
    size = "medium",
    srcs = medium_kernel_test_list,
)

cuda_py_tests(
    name = "kernel_tests_with_sharding",
    size = "medium",
    srcs = sharded_kernel_test_list,
    shard_count = 50,
)

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = [
            "**/METADATA",
            "**/OWNERS",
        ],
    ),
    visibility = ["//tensorflow:__subpackages__"],
)
