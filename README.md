# FakeCLR: Exploring Contrastive Learning for Solving Latent Discontinuity in Data-Efficient GANs

![image](./docs/assets/FakeCLR.png)

> **FakeCLR: Exploring Contrastive Learning for Solving Latent Discontinuity in Data-Efficient GANs** <br>
> Ziqiang Li, Chaoyue Wang, Heliang Zheng, Jing Zhang, and Bin Li <br>

[[Paper](https://arxiv.org/pdf/2207.08630.pdf)]

In this paper, we revisit and compare different contrastive learning strategies in DE-GANs, and identify (i) the current bottleneck of generative performance is the discontinuity of latent space; (ii) compared to other contrastive learning strategies, Instance-perturbation works towards latent space continuity, which brings the major improvement to DE-GANs. Based on these observations, we propose FakeCLR, which only applies contrastive learning on perturbed fake samples, and devises three related training techniques: Noise-related Latent Augmentation, Diversity-aware Queue, and Forgetting Factor of Queue. Our experimental results manifest the new state of the arts on both few-shot generation and limited-data generation. On multiple datasets, FakeCLR acquires more than 15% FID improvement compared to existing DE-GANs. 

## Qualitative results

![image](./docs/assets/generated_images.png)

## Model

Here, some pretrained models can be downloaded


| Model | FID | Link |
| :--- | :------: | :--------: |
| Obama-100     | 26.95    | [link](https://drive.google.com/file/d/1W8Ovqulf6wp7eMTA8o0v5SV1UI3cv794/view?usp=sharing) |
| Grumpy-Cat-100    | 19.56     | [link](https://drive.google.com/file/d/1xtRLBScT6PCc4E8XKdDpPdENfow_03x8/view?usp=sharing) |
| Panda-100   | 8.42     | [link](https://drive.google.com/file/d/1e87yo651TyElSpgGg9CV5EKgC-W4Tmz8/view?usp=sharing) |
| AnimalFace Cat-160   | 26.34     | [link](https://drive.google.com/file/d/1VQrlyS5cK_lK04Q4ucYsgbwQ0AxUS-cb/view?usp=sharing) |
| AnimalFace Dog-389   | 42.02     | [link](https://drive.google.com/file/d/1zP81XEdJflCaYNcpQAhI8mshij76BdCO/view?usp=sharing) |



## Training

This repository is built based on [styleGAN2-ada-pytorch](https://github.com/NVlabs/stylegan2-ada-pytorch) and [InsGen](https://github.com/genforce/insgen). Therefore, dataset processing can follow [styleGAN2-ada-pytorch](https://github.com/NVlabs/stylegan2-ada-pytorch)

Compared to [InsGen](https://github.com/genforce/insgen), we only have one addition head (fake head) on top of the original discriminator. Furthermore, we add the iteration-based weight for negative samples in negative queue.


Please use the following command to start your own training:

```bash
python train.py --gpus=2 \
                --data=${DATA_PATH} \
                --cfg=paper256 \
                --batch=64 \
                --mirror=True \
                --kimg=10000 \
                --ada_linear=True \
                --outdir=training_example \
```

## Acknowledgements

We thank Janne Hellsten and Tero Karras for the pytorch version codebase of their [styleGAN2-ada-pytorch](https://github.com/NVlabs/stylegan2-ada-pytorch). We also Thank Ceyuan Yang, Yujun Shen, and Yinghao Xu for the pytorch version codebase of their [InsGen](https://github.com/genforce/insgen).

## BibTeX

```bibtex
@misc{li2022fakeclr,
    title={FakeCLR: Exploring Contrastive Learning for Solving Latent Discontinuity in Data-Efficient GANs},
    author={Ziqiang Li and Chaoyue Wang and Heliang Zheng and Jing Zhang and Bin Li},
    year={2022},
    eprint={2207.08630},
    archivePrefix={arXiv},
    primaryClass={cs.CV}
}
```
