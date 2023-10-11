**Meeting Summary 9/28/23**
- Continue on [PyTorch Dependency Packaging owner list](https://fedoraproject.org/wiki/SIGs/PyTorch/packagingStatus#PyTorch_Dependency_Packaging)
- The list may have issues, please update it if you find anything WRT bits which are not needed or not package-able for Fedora
  - cutlass, cudnn_frontend were raised as concerns as they require CUDA
  - Onnx-tensorrt require Nvidia TensorRT also require CUDA
  - NCCL also require CUDA
- bazel has been an issue for other projects, most notably tensorflow. There appear to be at least one PyTorch dep which requires bazel for building
  - [Previous review attempt](https://bugzilla.redhat.com/show_bug.cgi?id=1470842)
  - It may be possible to use cmake or patch out the bazel requirements but this will need more exploration
- Enabling the examples in the [pytorch example repo](https://github.com/pytorch/examples) was proposed as a goal for the SIG
  - Some of the examples are not likely to run well with CPU only (vision transformer, dgan etc.)
  - Running the mnist examples in the pytorch example repo seems like a better short term goal
    - mnist, mnist_forward_forward, mnist_hogwild, mnist_rnn
- Explore meeting-bot for text logging/meeting minutes

Action items
- thunderbirdtr (Onuralp Sezer) will attempt to package NNPACK
