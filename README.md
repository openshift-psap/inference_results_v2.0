
# How to run MLPerf Inference Edge on MicroShift
We will be using the Nvidia-optimized Inference for Edge implementation from MLPerf™ v2.0.

## Prerequisites

### Download the datasets for MLPerf Inference Edge 2.0:

Please refer to [/closed/NVIDIA](closed/NVIDIA/README.md) for detailed instructions on how to download the data and preprocess it.


## Benchmarks


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

