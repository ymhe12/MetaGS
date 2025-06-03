# MetaGS: A Meta-Learned Gaussian-Phong Model for Out-of-Distribution 3D Scene Relighting

Yumeng He,  [Yunbo Wang](https://wyb15.github.io/)<sup>†</sup>, [Xiaokang Yang](https://scholar.google.com/citations?user=yDEavdMAAAAJ&hl=zh-CN)<br>

[arXiv](https://arxiv.org/abs/2405.20791) | [PDF](https://arxiv.org/pdf/2405.20791) | [Dataset](https://drive.google.com/drive/folders/1AoJctpU_sUyVev3luqXhE2-OjAauL8MN?usp=drive_link)

This repository contains the official code for our paper: **MetaGS: A Meta-Learned Gaussian-Phong Model for Out-of-Distribution 3D Scene Relighting**.


## Installation

1. Create an environment
    ```bash
    conda create -n metags python=3.10
    conda activate metags
    ```
    
2. Install dependencies
    ```bash
    git clone https://github.com/ymhe12/MetaGS.git
    cd MetaGS
    git submodule update --init --recursive
    pip install -r requirements.txt
    pip install -e submodules/depth-diff-gaussian-rasterization
    pip install -e submodules/simple-knn
    pip install ./bvh
    ```


## Experiments

### Training

1. Stage 1&2: Gaussian initialization & Normal finetuning
    ```shell
    python train.py -s <path_to_your_dataset> -m <path_to_ouput_folder> --eval
    ```

2. Stage 3: Meta-learning
    ```shell
    python train_meta.py -s <path_to_your_dataset> -m <path_to_ouput_folder> --eval
    ```

### Evaluation
1. Generate NVS renderings
    ```shell
    python render.py -m <path_to_ouput_folder>
    ```

2. Calculate error metrics
   ```shell
    python metrics.py -m <path_to_ouput_folder>
    ```

### Full script
You can run the full experiment using: (remember ro edit the $DATADIR and $OUTPUT location)
```shell
sh run.sh
```



## Acknowledgements

We appreciate the following github repos where we borrow code from: 
* [gaussian splatting](https://github.com/graphdeco-inria/gaussian-splatting)
* [Relightable3DGaussian](https://github.com/NJU-3DV/Relightable3DGaussian)

Thanks for their amazing works!


## Citation

If you find our work helps, please cite our paper:

```bibtex

@misc{he2025metagsmetalearnedgaussianphongmodel,
      title={MetaGS: A Meta-Learned Gaussian-Phong Model for Out-of-Distribution 3D Scene Relighting}, 
      author={Yumeng He and Yunbo Wang and Xiaokang Yang},
      year={2025},
      eprint={2405.20791},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2405.20791}, 
}

```
