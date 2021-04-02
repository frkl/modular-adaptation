# modular-adaptation

This repository provides data splits for an ImageNet -> X cross-domain few-shot image classification benchmark used in [1].

## How to use

This benchmark evaluates performance of adapting an ImageNet-pretrained representation to a set of 40 ~100-way (number of classes) {2,5,10,20}-shot (number of training images per class) downstream image classification tasks from a diverse set of domains. Each task contains 5 sets of randomly sampled training/testing splits. Unlabeled images from the testing splits are welcomed to be used for unsupervised, semi-supervised or transductive learning. The tasks are drawn from 10 publicly available datasets:

* 6 DomainNet domains {Clipart, Infograph, Painting, Quickdraw, Real, Sketch} <http://ai.bu.edu/M3SDA/>
* CIFAR-100 <https://www.cs.toronto.edu/~kriz/cifar.html>
* FGVC-Aircraft <https://www.robots.ox.ac.uk/~vgg/data/fgvc-aircraft/>
* DTD-Textures <https://www.robots.ox.ac.uk/~vgg/data/dtd/>
* GTSRB-Traffic signs <https://benchmark.ini.rub.de/gtsrb_dataset.html>

The splits are provided as `{dataset name}/{02|05|10|20}-shot/{train|test}{split id}.json` with image names and labels.

Performance is evaluated both at task-level averaged over 5 splits, and at shot-level averaged over the 5 splits x 10 datasets. Feel free to report results only on specific datasets/shots.

## Baseline performance

Baseline performance of adapting a pretrained EfficientNet-B0 from [EfficientNet-Pytorch](https://github.com/lukemelas/EfficientNet-PyTorch) using ProtoNet, finetuning and the modular adaptation approach of [1] is provided below.

2-shot
| Approach   | QDraw | Infgrph | Sketch | Clipart | Pnting | Real  | CIFAR | Textures | Aircraft | Signs | Overall |
| ---------  | ----- | ------- | ------ | ------- | ------ | ----  | ----- | -------- | -------- | ----- | ------- |
| ProtoNet   | 21.37 |  8.35   | 21.59  | 35.60   | 36.89  | 66.68 | 32.33 | 40.62    | 11.85    | 27.30 | 30.26   |
| Finetuning | 31.88 |  8.61   | 22.68  | 35.54   | 34.22  | 57.02 | 28.87 | 30.40    | 16.61    | 58.37 | 32.42   |
| MAP[1]     | 30.10 |  9.91   | 27.38  | 39.25   | 39.66  | 69.25 | 35.63 | 41.19    | 14.01    | 57.42 | 36.38   |

5-shot
| Approach   | QDraw | Infgrph | Sketch | Clipart | Pnting | Real  | CIFAR | Textures | Aircraft | Signs | Overall |
| ---------  | ----- | ------- | ------ | ------- | ------ | ----  | ----- | -------- | -------- | ----- | ------- |
| ProtoNet   | 30.51 | 12.72   | 31.82  | 48.09   | 45.72  | 72.39 | 42.85 | 52.00    | 18.28    | 39.21 | 39.36   |
| Finetuning | 47.29 | 14.26   | 39.02  | 54.05   | 50.42  | 71.26 | 47.25 | 46.47    | 35.94    | 87.56 | 49.35   |
| MAP[1]     | 45.73 | 16.49   | 43.23  | 59.21   | 55.21  | 74.94 | 55.97 | 52.15    | 36.13    | 85.74 | 52.48   |

10-shot
| Approach   | QDraw | Infgrph | Sketch | Clipart | Pnting | Real  | CIFAR | Textures | Aircraft | Signs | Overall |
| ---------  | ----- | ------- | ------ | ------- | ------ | ----  | ----- | -------- | -------- | ----- | ------- |
| ProtoNet   | 35.23 | 16.75   | 40.85  | 54.99   | 51.44  | 75.50 | 49.25 | 56.04    | 22.86    | 44.74 | 44.77   |
| Finetuning | 58.14 | 20.00   | 48.88  | 65.98   | 58.22  | 77.05 | 59.54 | 56.22    | 51.51    | 92.79 | 58.83   |
| MAP[1]     | 55.33 | 23.64   | 49.74  | 68.45   | 59.70  | 77.66 | 61.50 | 54.36    | 53.34    | 94.06 | 59.78   |

20-shot
| Approach   | QDraw | Infgrph | Sketch | Clipart | Pnting | Real  | CIFAR | Textures | Aircraft | Signs | Overall |
| ---------  | ----- | ------- | ------ | ------- | ------ | ----  | ----- | -------- | -------- | ----- | ------- |
| ProtoNet   | 39.62 | 21.36   | 44.60  | 60.77   | 56.48  | 77.91 | 53.94 | 56.30    | 26.79    | 53.49 | 49.13   |
| Finetuning | 66.04 | 26.89   | 56.58  | 72.96   | 64.97  | 80.61 | 68.14 | 62.77    | 72.25    | 96.44 | 66.77   |
| MAP[1]     | 62.89 | 30.28   | 55.65  | 75.23   | 65.25  | 79.93 | 68.42 | 61.12    | 75.05    | 98.37 | 67.22   |



## Reference

[1] Xiao Lin*, Meng Ye*, Yunye Gong, Giedrius Buracas, Nikoletta Basiou, Ajay Divakaran, Yi Yao. ["Modular Adaptation for Cross-Domain Few-Shot Learning"](https://arxiv.org/abs/2104.00619). arXiv preprint arXiv:2104.00619, 2021. 
