# PYNQ-ZU_Tutorial

This repository (repo.) provides you the materials to getting started with FPGA application development using PYNQ-ZU board - an AMD (Xilinx before) Zynq Ultrascale+ development board.

## PYNQ-ZU Toolchain Version Compatibility Matrix

| PYNQ | [Vivado/Vitis](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vitis.html) | Vitis-AI | DPU-PYNQ |    ROS   |
|:----:|:------------:|:--------:|:--------:|:--------:|
| [2.7 (Austin)](https://github.com/Xilinx/PYNQ/releases/tag/v2.7.0) | <= 2020.2 | [1.4.1](https://github.com/Xilinx/Vitis-AI/releases/tag/v1.4.1) | [1.4.0](https://github.com/Xilinx/DPU-PYNQ/releases/tag/v1.4.0) | :heavy_check_mark: [noetic](4_ROS/README.md) |
| [3.0 (Belfast)](https://github.com/Xilinx/PYNQ/releases/tag/v3.0.0) | <= 2022.1 | [2.5](https://github.com/Xilinx/Vitis-AI/releases/tag/v2.5) | [2.5.1](https://github.com/Xilinx/DPU-PYNQ/releases/tag/v2.5.1) | :x: [humble](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html) |

**Note**
- After installing Vitis_HLS/Vivado/Vitis, follow this [instruction to patch an Y2K22 fix](https://support.xilinx.com/s/article/76960?language=en_US).
- Installing ROS2 `humble` on PYNQ 3.0 (Belfast) is facing unresolved issue: APT's unmet dependencies.
