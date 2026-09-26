# PolyMFO and HiSeg: High-Resolution Foreign-Object Segmentation on Specular Polybag Surfaces

[![NumPy](https://img.shields.io/badge/NumPy-2.5.2-013243?logo=numpy&logoColor=white)](https://numpy.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.6.0%2Bcu124-EE4C2C?logo=pytorch&logoColor=white)](https://pytorch.org/)
[![Pillow](https://img.shields.io/badge/Pillow-12.3.0-blue)](https://python-pillow.org/)
[![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-PolyMFO-yellow)](https://huggingface.co/datasets/VNSO-AI/PolyMFO)
[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)

Official repository for the paper:

> **PolyMFO and HiSeg: High-Resolution Foreign-Object Segmentation on Specular Polybag Surfaces**

**Authors:** Tran Cao Minh, Hai Tran, Jia-Ching Wang *(Senior Member, IEEE)*, and Ha Minh Tan  
**Status:** Submitted to an IEEE journal, 2026.

This repository contains the source code and research utilities associated with **PolyMFO** and **HiSeg**.  
The PolyMFO benchmark dataset is hosted separately on Hugging Face.

## Dataset

The **PolyMFO** dataset is available at:

**https://huggingface.co/datasets/VNSO-AI/PolyMFO**

PolyMFO is a high-resolution benchmark for **foreign-object inspection on specular polybag surfaces**, supporting both **image classification** and **binary segmentation**.

### Dataset visualization

Representative samples from PolyMFO are shown below. Each example includes the input image, its binary segmentation mask, and the corresponding anomaly overlay.

![PolyMFO dataset visualization](https://huggingface.co/datasets/VNSO-AI/PolyMFO/resolve/main/PolyMFO_V1/visual_dataset/visual_dataset.jpg)

### Task summary

| Task | Input | Output | Description |
|---|---|---|---|
| Classification | RGB image | Class label | Predict whether an image is normal or belongs to one of 9 foreign-object categories |
| Segmentation | RGB image | Binary mask | Localize the foreign object at the pixel level |

### Dataset summary

| Property | Value |
|---|---:|
| Total images | 575 |
| Image resolution | 2160 × 2160 |
| Tasks | Classification, Segmentation |
| Training images | 460 |
| Testing images | 115 |
| Split | Predefined 80% training / 20% testing |
| NumPy files | Precomputed `.npy` files are provided |

The dataset is distributed with a **predefined 80/20 split**, consisting of **460 training images** and **115 testing images**.  
To facilitate reproducible experiments, we also provide **precomputed NumPy (`.npy`) files** for both classification and segmentation tasks.

### Number of images

| Split | Normal | Anomaly | Total |
|---|---:|---:|---:|
| Training | 230 | 230 | 460 |
| Testing | 58 | 57 | 115 |
| Total | 288 | 287 | 575 |

### Anomaly class distribution

| Class ID | Foreign-object type | Training | Testing | Total |
|---|---|---:|---:|---:|
| F001 | White textile thread | 23 | 5 | 28 |
| F002 | Black textile thread | 29 | 7 | 36 |
| F003 | Human hair | 26 | 6 | 32 |
| F004 | Transparent plastic film fragment | 15 | 4 | 19 |
| F005 | Cling film fragment | 20 | 5 | 25 |
| F006 | Colored plastic film fragment | 26 | 7 | 33 |
| F007 | Cardboard fragment | 39 | 10 | 49 |
| F008 | Plastic flash fragment | 23 | 6 | 29 |
| F009 | Cable tie fragment | 29 | 7 | 36 |

Please refer to the Hugging Face dataset card for the complete dataset description, directory structure, and usage restrictions.


## Download the Dataset

The PolyMFO dataset is hosted on Hugging Face:

**https://huggingface.co/datasets/VNSO-AI/PolyMFO**

### Using the Hugging Face `datasets` library

After installing the project dependencies from `requirements.txt`, load the dataset with:

```python
from datasets import load_dataset

ds = load_dataset("VNSO-AI/PolyMFO")
```

### Clone the dataset repository

You can also clone the full dataset repository directly:

```bash
git clone https://huggingface.co/datasets/VNSO-AI/PolyMFO
```

The dataset already includes a predefined **80/20 train-test split**, with **460 training images** and **115 testing images**.

For convenience and reproducibility, ready-to-use NumPy (`.npy`) files are provided for both **classification** and **segmentation** tasks.

## Environment Setup

Clone the repository:

```bash
git clone https://github.com/CaoMinhh/PolyMFO.git
cd PolyMFO
```

All project dependencies are listed in [`requirements.txt`](requirements.txt).

### Option 1: Conda

Create and activate the environment:

```bash
conda create -n polymfo python=3.12 -y
conda activate polymfo
pip install -r requirements.txt
```

### Option 2: uv

Create a virtual environment:

```bash
uv venv --python 3.12 .venv
```

Activate it:

**Windows PowerShell**

```powershell
.\.venv\Scripts\Activate.ps1
```

**Linux / macOS**

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
uv pip install -r requirements.txt
```

### Verify the environment

```bash
python -c "import torch, numpy, PIL, datasets, huggingface_hub; print('PyTorch:', torch.__version__); print('CUDA:', torch.version.cuda); print('NumPy:', numpy.__version__); print('Pillow:', PIL.__version__); print('datasets:', datasets.__version__); print('huggingface_hub:', huggingface_hub.__version__)"
```

The core package versions used in our experiments are:

| Package | Version |
|---|---|
| NumPy | `2.5.2` |
| PyTorch | `2.6.0+cu124` |
| Pillow | `12.3.0` |

The specified PyTorch build targets CUDA 12.4.

## Code and Reproducibility

This GitHub repository contains the code associated with the PolyMFO/HiSeg study, including data-processing and research utilities.

The dataset itself is **not stored in this GitHub repository**. Download PolyMFO from Hugging Face and use the dataset paths expected by the corresponding scripts in this repository.

For directly comparable benchmark results, use the predefined dataset split distributed with PolyMFO.

The **HiSeg training and evaluation code** and the corresponding **pre-trained model weights** are not publicly released at this time. Their public release will be considered in a future update to this repository.

## Paper Status

The manuscript

> **PolyMFO and HiSeg: High-Resolution Foreign-Object Segmentation on Specular Polybag Surfaces**

has been **submitted to an IEEE journal**.

Publication metadata, DOI, and final citation information will be updated after publication.

## Citation

If you use PolyMFO, HiSeg, or code from this repository in your research, please cite the associated work.

```bibtex
@unpublished{minh2026polymfo,
  title  = {PolyMFO and HiSeg: High-Resolution Foreign-Object Segmentation on Specular Polybag Surfaces},
  author = {{Tran Cao Minh} and {Hai Tran} and {Jia-Ching Wang} and {Ha Minh Tan}},
  year   = {2026},
  note   = {Submitted to an IEEE journal}
}
```

The citation entry will be updated after the paper is published.

## License

This project is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** license.

Non-commercial use is permitted with proper attribution. Commercial use is prohibited.

See the full license terms: https://creativecommons.org/licenses/by-nc/4.0/
