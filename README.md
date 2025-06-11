# Bonito

This is an forked version of bonito including support for Nvidia Blackwell Series GPU

### Installation Instruction

The current bonito version 0.9.1 rely on pytorch 2.6.0, which is not compatible with sm_120 required by GPUs such as RTX 5090, RTX 5080...etc

In order to make bonito work on platform with those GPU, you first need:
* Create a virtual environment using either conda or pip, make sure python 3.12 is installed in your environment.
* Install pytorch 2.7.1 with CUDA 12.8 support (pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128). See: https://pytorch.org/get-started/locally/
* Using a Blackwell compatible version of flash-attn. The official flash-attn build current do not support blackwell GPUs, however loscrossos has compiled a custom wheel on top of flash-attn 2.7.4.post1 with support for Blackwell GPUs. Run "pip3 install <wheel_file>" in the same virtual environment as above. See: https://github.com/loscrossos/lib_flashattention
* The installation script in this forked bonito has been modified to be compatible with pytorch 2.7.1 and cuda 12.8 or above.
* Run command follow to install bonito with blackwell support:

(ont-train) $ git clone https://github.com/Amekn/bonito

(ont-train) $ cd bonito

(ont-train) $ pip install --upgrade pip

(ont-train) $ pip install -e .[cu128] --extra-index-url https://download.pytorch.org/whl/cu128

and...here you go, bonito should be installed in your current virtual environment now. 

### Licence and Copyright
(c) 2019 Oxford Nanopore Technologies Ltd.

Bonito is distributed under the terms of the Oxford Nanopore
Technologies, Ltd.  Public License, v. 1.0.  If a copy of the License
was not distributed with this file, You can obtain one at
http://nanoporetech.com

### Research Release

Research releases are provided as technology demonstrators to provide early access to features or stimulate Community development of tools. Support for this software will be minimal and is only provided directly by the developers. Feature requests, improvements, and discussions are welcome and can be implemented by forking and pull requests. However much as we would like to rectify every issue and piece of feedback users may have, the developers may have limited resource for support of this software. Research releases may be unstable and subject to rapid iteration by Oxford Nanopore Technologies.

### Citation

```
@software{bonito,
  title = {Bonito: A PyTorch Basecaller for Oxford Nanopore Reads},
  author = {{Chris Seymour, Oxford Nanopore Technologies Ltd.}},
  year = {2019},
  url = {https://github.com/nanoporetech/bonito},
  note = {Oxford Nanopore Technologies, Ltd. Public License, v. 1.0},
  abstract = {Bonito is an open source research basecaller for Oxford Nanopore reads. It provides a flexible platform for training and developing basecalling models using PyTorch.}
}
```