
# How to run MLPerf Inference Edge on MicroShift
We will be using the Nvidia-optimized Inference for Edge implementation from MLPerf™ v2.0.

## Prerequisites
The host system needs to be configured so that containers run on MicroShift can access GPUs.
 - Install RHEL 8.7 and MicroShift 4.12 on the host machine
 - A30 Nvidia GPU (in this example case) on your host machine.
 - Install the NVIDIA GPU driver 
 - Install NVIDIA Container Toolkit
 - Install NVIDIA Device Plugin



### Download the datasets for MLPerf Inference Edge 2.0:

Please refer to [/closed/NVIDIA](closed/NVIDIA/README.md) for detailed instructions on how to download the data and preprocess it.
The models, datasets, and preprocessed datasets are stored in a central location referred to as a "Scratch Space". Because of the large amount of data that needs to be stored in the scratch space, it is recommended that the scratch be at least 3 TB. We stored the data on NVMe SSD. It will take approximately one day to download all the data. 

### Start the container interactively and run script to add your system to the 'KnownSystem' list

To start the container interactively run 
```bash
oc apply -f mlperf_inferencev20_setup.yaml
```

Connect to the running container 
```bash 
oc rsh oc rsh -n test mlinferencesetup
```

From inside the container run the following to add your system to the 'KnownSystem' list 

```python3 scripts/custom_systems/add_custom_system.py```
 

## Run the MLPerf v2.0 Inference Edge Benchmarks

To run the MLPerf Inference Edge benchmarks, execute the following command.  This creates a pod in MicroShift that runs the MLPerf inference benchmarks.

```bash
oc apply -f mlperf_inferencev20.yaml
```

View the log as the benchmarks run. 
```bash
oc logs -f mlinference --namespace test 
```

Once the benchmarks complete, the end of log should list outcome of test. Here is an example of what you should see at the end of the log output. 
```bash
======================= Perf harness results: =======================

A30x1_TRT-custom_k_99_MaxP-Offline:
    3d-unet: result_samples_per_second: 1.68985, Result is VALID
    bert: result_samples_per_second: 1657.5, Result is VALID
    rnnt: result_samples_per_second: 6508.62, Result is VALID

A30x1_TRT-custom_k_99_MaxP-SingleStream:
    3d-unet: result_90.00_percentile_latency_ns: 1032063563, Result is VALID
    bert: result_90.00_percentile_latency_ns: 2163848, Result is VALID
    rnnt: result_90.00_percentile_latency_ns: 22444932, Result is VALID

A30x1_TRT-lwis_k_99_MaxP-Offline:
    resnet50: result_samples_per_second: 17984.5, Result is VALID
    ssd-mobilenet: result_samples_per_second: 25625.6, Result is VALID
    ssd-resnet34: result_samples_per_second: 476.856, Result is VALID

A30x1_TRT-lwis_k_99_MaxP-SingleStream:
    resnet50: result_90.00_percentile_latency_ns: 496206, Result is VALID
    ssd-mobilenet: result_90.00_percentile_latency_ns: 282757, Result is VALID
    ssd-resnet34: result_90.00_percentile_latency_ns: 2846111, Result is VALID
```



Check the logs to see if everything ran. 
Logs are saved to build/logs/[timestamp]/[system ID]/... every time make run_harness is called.


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

