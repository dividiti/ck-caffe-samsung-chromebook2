# [cknowledge.org/ai](https://cknowledge.org/ai): Crowdsourcing benchmarking and optimisation of AI

A suite of open-source tools for [collecting knowledge on optimising AI](http://bit.ly/hipeac49-ckdl):
* [Android app](https://play.google.com/store/apps/details?id=openscience.crowdsource.video.experiments&hl=en_GB)
* [Desktop app](https://github.com/dividiti/ck-crowdsource-dnn-optimization)
* [CK-Caffe](https://github.com/dividiti/ck-caffe)
* [CK-Caffe2](https://github.com/ctuning/ck-caffe2)
* [CK-TensorFlow](https://github.com/ctuning/ck-tensorflow)
* [CK-TensorRT](https://github.com/dividiti/ck-tensorrt)
* etc.

# [PUBLIC] Benchmarking Caffe with OpenBLAS on Samsung Chromebook 2

The Jupyter notebook ([view on github.com](https://github.com/dividiti/ck-caffe-samsung-chromebook2/blob/master/script/batch_size-openblas_threads-models/analysis.20170520.ipynb); [view on nbviewer.jupyter.org](https://nbviewer.jupyter.org/github/dividiti/ck-caffe-samsung-chromebook2/blob/master/script/batch_size-openblas_threads-models/analysis.20170520.ipynb?raw) in this Collective Knowledge repository analyses the **execution time** of inference (forward propagation):
- on the [Samsung Chromebook 2](http://www.samsung.com/us/computer/chrome-os-devices/XE503C12-K01US-specs) **platform**:
  - [CPU] quad-core ARM Cortex-A15 @ 1900 MHz;
  - [CPU] quad-core ARM Cortex-A7 @ 1300 MHz (not used);
  - [GPU] quad-core ARM Mali-T628 @ 600 MHz (not used);
  - [GPU] dual-core ARM Mali-T628 @ 600 MHz (not used);
  - [GPU] OpenCL driver 6.0 (`r6p0-02rel0.b77b627bc37583eeaa34bbee29868088`);
  - [GPU] OpenCL standard 1.1;
  - [RAM] 2 GB;
  - Gentoo Linux [over](community.arm.com/groups/arm-mali-graphics/blog/2014/12/18/installing-opencl-on-chromebook-2-in-30-minutes) ChromeOS:
```
$ cat /etc/lsb-release
CHROMEOS_AUSERVER=https://tools.google.com/service/update2
CHROMEOS_BOARD_APPID={24E2E4F7-F92C-6115-3E26-02C7EAA02946}
CHROMEOS_CANARY_APPID={90F229CE-83E2-4FAF-8479-E368A34938B1}
CHROMEOS_DEVSERVER=
CHROMEOS_RELEASE_APPID={24E2E4F7-F92C-6115-3E26-02C7EAA02946}
CHROMEOS_RELEASE_BOARD=peach_pit-signed-mp-v3keys
CHROMEOS_RELEASE_BRANCH_NUMBER=69
CHROMEOS_RELEASE_BUILDER_PATH=peach_pit-release/R58-9334.69.0
CHROMEOS_RELEASE_BUILD_NUMBER=9334
CHROMEOS_RELEASE_BUILD_TYPE=Official Build
CHROMEOS_RELEASE_CHROME_MILESTONE=58
CHROMEOS_RELEASE_DESCRIPTION=9334.69.0 (Official Build) stable-channel peach_pit 
CHROMEOS_RELEASE_NAME=Chrome OS
CHROMEOS_RELEASE_PATCH_NUMBER=0
CHROMEOS_RELEASE_TRACK=stable-channel
CHROMEOS_RELEASE_VERSION=9334.69.0
DEVICETYPE=CHROMEBOOK
GOOGLE_RELEASE=9334.69.0
$ uname -a
Linux localhost 3.8.11 #1 SMP Wed May 10 18:37:16 PDT 2017 armv7l ARMv7 Processor rev 3 (v7l) SAMSUNG EXYNOS5 (Flattened Device Tree) GNU/Linux
```
- using 3 CNN **models** (net architecture + weights):
  - [AlexNet](https://github.com/BVLC/caffe/tree/master/models/bvlc_alexnet);
  - [GoogleNet](https://github.com/BVLC/caffe/tree/master/models/bvlc_googlenet);
  - [SqueezeNet 1.1](https://github.com/DeepScale/SqueezeNet/tree/master/SqueezeNet_v1.1);

- using 1 **library** version:
  - [CPU] [OpenBLAS](https://github.com/xianyi/OpenBLAS) 0.2.19;

- with the **number of threads** varying from 1 to 4;

- with the **batch size** varying from 1 to 4.
