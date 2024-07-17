# GraspNet and Pointnet2 PyTorch Upgrade (v1.13.1)

Our main contribution is upgrading GraspNet and Pointnet2_PyTorch to the latest PyTorch version (v1.13.1). Currently, there isn't a comprehensive implementation available, and most of the work involves patching various bugs. This version consolidates all the necessary fixes and improvements, providing a stable and reliable implementation. You can directly use this upgraded version to replace the original GraspNet and Pointnet2_PyTorch implementations.

## Environment Requirements
- Ubuntu 23.04
- Torch 1.13.1
- Torchvision 0.14.1
- CUDA 11.8

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Citation](#citation)
- [References](#references)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Introduction
GraspNet is designed to facilitate the generation of reliable grasp poses for robotic systems. This implementation, based on PyTorch v1.13.1, leverages advanced techniques to improve the success rate and adaptability of robotic grasping in cluttered and dynamic environments. Additionally, this repository includes an upgraded version of Pointnet2_PyTorch, also compatible with PyTorch v1.13.1.

## Installation
To install the necessary modules, please follow these steps:

```bash
git clone https://github.com/H-Freax/GraspNet_Pointnet2_PyTorch1.13.1.git
cd GraspNet_Pointnet2_PyTorch1.13.1
```

Additionally, you need to install the `pointnet2` and `knn` modules:

```bash
cd graspnet/pointnet2
python setup.py install

cd ../knn
python setup.py install
```

### Potential Issues of Installation
When installing `graspnetAPI`, you might encounter the following problem:

```
× python setup.py egg_info did not run successfully.
│ exit code: 1
╰─> [18 lines of output]
The 'sklearn' PyPI package is deprecated, use 'scikit-learn'
rather than 'sklearn' for pip commands.
```

**Solution:**
```bash
export SKLEARN_ALLOW_DEPRECATED_SKLEARN_PACKAGE_INSTALL=True
```

Check the compatible version of `torch` and `torchvision` of your machine (especially the CUDA version) if the following problem occurs:

```
RuntimeError: CUDA error: no kernel image is available for execution on the device
```

**Solution:** Install torch with the right CUDA version, e.g.

```bash
# CUDA 11.8
pip3 install torch==1.13.1+cu117 torchvision==0.14.1+cu117 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cu117
```

If you still face errors, please try the following:

```bash
sudo apt-get install python3-dev
conda install gxx_linux-64
conda install gcc_linux-64
```

Change float to float64 if necessary.

Install CUDA 11.8:

1. Download the CUDA 11.8 installer from [NVIDIA](https://developer.nvidia.com/cuda-downloads).
2. Run the installer:
   ```bash
   sudo bash cuda_11.8.0_520.61.05_linux.run
   ```

Add the following lines to your `~/.bashrc`:

```bash
export CUDA_HOME=/usr/local/cuda-11.8
export PATH=$CUDA_HOME/bin:$PATH
export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH
export PATH=$PATH:/usr/local/cuda-11.8/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.8/lib64
export CUDADIR=/usr/local/cuda-11.8
```

## Usage
To use this upgraded version of GraspNet and Pointnet2_PyTorch, simply replace the original implementations with this repository and follow the usual steps for data preparation and inference.

## Citation
Please cite our paper in your publications if it helps your research:

```
@misc{qian2024thinkgrasp,
        title={ThinkGrasp: A Vision-Language System for Strategic Part Grasping in Clutter},
        author={Yaoyao Qian and Xupeng Zhu and Ondrej Biza and Shuo Jiang and Linfeng Zhao and Haojie Huang and Yu Qi and Robert Platt},
        year={2024},
        eprint={2407.11298},
        archivePrefix={arXiv},
        primaryClass={cs.RO}
    }
```

## References
This work builds on and refers to the following projects:

- [Vision-Language-Grasping](https://github.com/xukechun/Vision-Language-Grasping)
- [GraspNet-baseline](https://github.com/graspnet/graspnet-baseline)
- [Pointnet2_PyTorch](https://github.com/erikwijmans/Pointnet2_PyTorch)

### Additional References
```
@article{pytorchpointnet++,
  Author = {Erik Wijmans},
  Title = {Pointnet++ Pytorch},
  Journal = {https://github.com/erikwijmans/Pointnet2_PyTorch},
  Year = {2018}
}

@inproceedings{qi2017pointnet++,
  title={Pointnet++: Deep hierarchical feature learning on point sets in a metric space},
  author={Qi, Charles Ruizhongtai and Yi, Li and Su, Hao and Guibas, Leonidas J},
  booktitle={Advances in Neural Information Processing Systems},
  pages={5099--5108},
  year={2017}
}

@article{fang2023robust,
  title={Robust grasping across diverse sensor qualities: The GraspNet-1Billion dataset},
  author={Fang, Hao-Shu and Gou, Minghao and Wang, Chenxi and Lu, Cewu},
  journal={The International Journal of Robotics Research},
  year={2023},
  publisher={SAGE Publications Sage UK: London, England}
}

@inproceedings{fang2020graspnet,
  title={GraspNet-1Billion: A Large-Scale Benchmark for General Object Grasping},
  author={Fang, Hao-Shu and Wang, Chenxi and Gou, Minghao and Lu, Cewu},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  pages={11444--11453},
  year={2020}
}

@INPROCEEDINGS{10161041,
  author={Xu, Kechun and Zhao, Shuqi and Zhou, Zhongxiang and Li, Zizhang and Pi, Huaijin and Zhu, Yifeng and Wang, Yue and Xiong, Rong},
  booktitle={2023 IEEE International Conference on Robotics and Automation (ICRA)}, 
  title={A Joint Modeling of Vision-Language-Action for Target-oriented Grasping in Clutter}, 
  year={2023},
  pages={11597-11604},
  doi={10.1109/ICRA48891.2023.10161041}
}
```

## Contributing
We welcome contributions to improve GraspNet. If you are interested in contributing, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a new Pull Request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Acknowledgments
We would like to thank all contributors and the PyTorch community for their continuous support.
