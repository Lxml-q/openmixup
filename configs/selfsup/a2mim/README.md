# A2MIM

> [Architecture-Agnostic Masked Image Modeling -- From ViT back to CNN](https://arxiv.org/abs/2205.13943)

## Abstract

Masked image modeling (MIM), an emerging self-supervised pre-training method, has shown impressive success across numerous downstream vision tasks with Vision transformers (ViT). Its underlying idea is simple: a portion of the input image is randomly masked out and then reconstructed via the pre-text task. However, why MIM works well is not well explained, and previous studies insist that MIM primarily works for the Transformer family but is incompatible with CNNs. In this paper, we first study interactions among patches to understand what knowledge is learned and how it is acquired via the MIM task. We observe that MIM essentially teaches the model to learn better middle-level interactions among patches and extract more generalized features. Based on this fact, we propose an Architecture-Agnostic Masked Image Modeling framework (A2MIM), which is compatible with not only Transformers but also CNNs in a unified way. Extensive experiments on popular benchmarks show that our A2MIM learns better representations and endows the backbone model with the stronger capability to transfer to various downstream tasks for both Transformers and CNNs. 

<div align="center">
<img src="https://user-images.githubusercontent.com/44519745/174272666-30bc3177-e61f-4331-9f32-91f47aad6578.png" width="100%"/>
</div>

## Results and Models

In this page, we provide benchmarks to evaluate our pre-trained models. If not mentioned, all models are pre-trained on ImageNet dataset.

### Classification

The classification benchmarks includes 1 downstream task datasets, **ImageNet**. If not specified, the results are Top-1 (%). We also provide configs on ImageNet-100 dataset according to the setting on ImageNet.

#### ImageNet Fine-tuning Evaluation

* For ViT models, the **Top-1** classification accuracy is obtained from end-to-end fine-tuning 100 epochs on ImageNet.

| Backbone  | Pre-train epoch | Fine-tuning Top-1 |                                                           Pre-train Config                                                           |                                                                 Fine-tuning Config                                                                  |                                                                                                                           Download                                                                                                                            |
| :-------: | :-------------: | :---------------: | :----------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| ViT-Base  |       800       |       84.18       | [config](https://github.com/Westlake-AI/openmixup/tree/main/configs/selfsup/a2mim/imagenet/vit_base_l0_sz224_8xb128_accu2_step_ep800.py) | [config](https://github.com/Westlake-AI/openmixup/tree/main/configs/benchmarks/classification/imagenet/vit_base_p16_swin_ft_simmim_sz224_4xb128_accu2_cos_ep100.py) | model \| log |

* For ResNet-50, the top-1 classification accuracy of **RSB A3** and **RSB A2** are obtained from end-to-end fine-tuning 100 and 300 epochs on ImageNet.

|  Backbone | Pre-train epoch | Fine-tuning Top-1 |                    Pre-train Config                   |                                                                  Fine-tuning Config                                                                  |   Download   |
|:---------:|:---------------:|:-----------------:|:-----------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------:|:------------:|
| ResNet-50 |       100       |       78.76       | [config](./imagenet/r50_l3_sz224_8xb256_cos_ep100.py) | [config](https://github.com/Westlake-AI/openmixup/blob/main/configs/benchmarks/classification/imagenet/r50_rsb_a3_ft_sz160_4xb512_cos_fp16_ep100.py) | model \| log |
| ResNet-50 |       300       |       78.90       | [config](./imagenet/r50_l3_sz224_8xb256_cos_ep300.py) | [config](https://github.com/Westlake-AI/openmixup/blob/main/configs/benchmarks/classification/imagenet/r50_rsb_a2_ft_sz224_8xb256_cos_fp16_ep300.py) | model \| log |

#### ImageNet-100 Fine-tuning Evaluation

Based on the setting of ImageNet, we also perform fast experiments on ImageNet-100 for 800-epoch pre-training and 100-epoch fine-tuning.

|  Backbone  | Pre-train epoch | Fine-tuning Top-1 |                                                           Pre-train Config                                                           |                                                                 Fine-tuning Config                                                                  |                                                                                                                           Download                                                                                                                            |
| :--------: | :-------------: | :---------------: | :----------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| DeiT-Small |       800       |       87.24       | [config](https://github.com/Westlake-AI/openmixup/tree/main/configs/selfsup/a2mim/imagenet100/deit_small_l8_sz192_4xb256_accu2_cos_ep800.py) | [config](https://github.com/Westlake-AI/openmixup/tree/main/configs/benchmarks/classification/imagenet100/deit_small_p16_swin_ft_sz224_4xb256_cos_ep100.py) | model \| log |
| ResNet-50  |       800       |       89.32       | [config](https://github.com/Westlake-AI/openmixup/tree/main/configs/selfsup/a2mim/imagenet100/r50_l3_sz192_4xb256_accu2_cos_fp16_ep800.py) | [config](https://github.com/Westlake-AI/openmixup/tree/main/configs/benchmarks/classification/imagenet100/r50_swin_ft_sz224_4xb256_accu2_cos_ep100.py) | model \| log |


## Citation

```bibtex
@article{Li2022A2MIM,
  title={Architecture-Agnostic Masked Image Modeling -- From ViT back to CNN},
  author={Li, Siyuan and Wu, Di and Wu, Fang and Zang, Zelin and Wang, Kai and Shang, Lei and Sun, Baigui and Li, Hao and Li, Stan. Z.},
  journal={ArXiv},
  url={https://arxiv.org/abs/2205.13943},
  year={2022}
}
```
