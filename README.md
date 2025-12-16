<div align="center">
<h1>RESfM: Robust Deep Equivariant Structure from Motion</h1>
  
### [Paper](https://openreview.net/pdf?id=wldwEhQ7cl) | [Project Page](https://robust-equivariant-sfm.github.io/)


**[Weizmann Institute of Science](https://www.weizmann.ac.il/pages/)**; **[NVIDIA Research](https://research.nvidia.com/home)**


[Fadi Khatib](https://fadikhatib.github.io/), [Yoni Kasten](https://ykasten.github.io/), [Dror Moran](https://scholar.google.com/citations?user=kS5jfSoAAAAJ&hl=en), [Meirav Galun](https://www.weizmann.ac.il/math/meirav/), [Ronen Basri](https://www.weizmann.ac.il/math/ronen/home)
</div>

```bibtex
@inproceedings{khatib2025resfm,
  title={Resfm: Robust deep equivariant structure from motion},
  author={Khatib, Fadi and Kasten, Yoni and Moran, Dror and Galun, Meirav and Basri, Ronen},
  booktitle={The Thirteenth International Conference on Learning Representations},
  year={2025}
}
```


## Overview

Robust Deep Equivariant Structure from Motion (RESfM, ICLR 2025) is a deep-learning framework for multiview SfM that overcomes the assumption of clean point tracks. Unlike prior equivariant architectures, RESfM integrates a learnable inlier/outlier classifier into a row-and-column permutation‑equivariant backbone. This design enables it to accurately recover camera poses and 3D structure from noisy, outlier‑contaminated tracks, achieving results competitive with classical methods like COLMAP while being significantly faster. The method generalizes across large datasets with hundreds of views.


## Quick Start
This repository is implemented with python 3.8.
## Setup

First, clone this repository to your local machine, and set up the Conda environment with all required dependencies:

```bash
git clone https://github.com/FadiKhatib/resfm.git  
cd resfm/code
conda env create -f environment.yaml
conda activate resfm
```

### Folders
The repository should contain the following folders:
```
resfm
├── code
├── datasets
│   ├── megadepth
│   └── 1dsfm
    └── ...
├── environment.yml
├── results
```

### Data and Pretrained Model
<p>
Download the data from 
<a href="https://www.dropbox.com/scl/fi/17vytqklc9tyy68cikjdn/datasets.zip?rlkey=zrzmdvnw8jogurgeos5vyfvsg&st=r2d09j6g&dl=0" target="_blank">this link</a>, 
and the pretrained model from 
<a href="https://www.dropbox.com/scl/fi/eqjwgo2zqbscndg2n0y9x/pretrained_model.zip?rlkey=99iou8db1f1kvwk062wlq57ks&st=j5t002qj&dl=0 target="_blank">this link</a>.
</p>


## How to use
To train RESfM on multiple scenes:
```
python multiple_scenes_learning.py --conf confs/RESFM_Learning.conf --wandb 0
```
To evaluate RESfM on test scenes using a pretrained checkpoint:
```
python multiple_scenes_learning.py --conf confs/RESFM_Learning.conf --wandb 0 --pretrainedPath PATH/TO/CHECKPOINT --phase "FINE_TUNE"
```



## Exporting to COLMAP Format



The reconstruction result (camera parameters and 3D points) will be automatically saved in the COLMAP format.


## Integration with Gaussian Splatting


The exported COLMAP files can be directly used with [gsplat](https://github.com/nerfstudio-project/gsplat) for Gaussian Splatting training



## Acknowledgements

Thanks to these great repositories: [ESFM](https://github.com/drormoran/Equivariant-SFM), [GASFM](https://github.com/lucasbrynte/gasfm), [Kornia](https://github.com/kornia/kornia), [PyCOLMAP](https://colmap.github.io/pycolmap/index.html)

## Checklist

- [ ] Release all the datasets
- [ ] Release the code for creating tracks from images


## License
See the [LICENSE](./LICENSE.txt) file for details about the license under which this code is made available.

