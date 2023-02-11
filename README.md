
# How to run MLPerf Inference Edge on MicroShift
We will be using the Nvidia-optimized Inference for Edge implementation from MLPerf™ v2.0.

## Prerequisites
The host system needs to be configured so that containers run on MicroShift can access GPUs.
 - Install RHEL 8.7 and MicroShift 4.12 on the host machine
 - A30 Nvidia GPU on your host machine.
 - Install the NVIDIA GPU driver 
 - Install NVIDIA Container Toolkit
 - Install NVIDIA Device Plugin



### Download the datasets for MLPerf Inference Edge 2.0:

Please refer to [/closed/NVIDIA](closed/NVIDIA/README.md) for detailed instructions on how to download the data and preprocess it.

### Start the container interactively and run script to add your system to the 'KnownSystem' list

To start the container interactively run 
```bash
oc apply -f mlperf_inferencev20_setup.yaml
```

Connect to the running container ```oc rsh  mlinferencesetup```

From inside the container run the following to add your system to the 'KnownSystem' list 

```python3 scripts/custom_systems/add_custom_system.py```
 

## Run the MLPerf v2.0 Inference Edge Benchmarks


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

