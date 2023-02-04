
This is the repository containing results and code for the v2.0 version of the MLPerf™ Inference benchmark.

# MLPerf Inference v2.0 Implementations
This is a repository of NVIDIA-optimized implementations for the [MLPerf](https://mlcommons.org/en/) Inference Benchmark on A30 GPUS.

## Benchmarks
**Please refer to /closed/NVIDIA for detailed instructions, including performace guides, and instructions on how to run with new systems.** 

## List of Benchmarks

Please refer to the `README.md` in each benchmark directory for implementation details.
- [3d-unet](closed/NVIDIA/code/3d-unet/tensorrt/README.md)
- [bert](closed/NVIDIA/code/bert/tensorrt/README.md)
- [rnnt](closed/NVIDIA/code/rnnt/tensorrt/README.md)
- [resnet50](closed/NVIDIA/code/resnet50/tensorrt/README.md)
- [ssd-resnet34](closed/NVIDIA/code/ssd-resnet34/tensorrt/README.md)
- [ssd-mobilenet](closed/NVIDIA/code/ssd-mobilenet/tensorrt/README.md)

## Other Directories

- [common](closed/NVIDIA/code/common) - holds shared scripts to generate TensorRT optimized plan files and to run the harnesses.
- [harness](closed/NVIDIA/code/harness) - holds source codes of the harness interfacing with LoadGen.
- [plugin](closed/NVIDIA/code/plugin) - holds source codes of TensorRT plugins used by the benchmarks.

