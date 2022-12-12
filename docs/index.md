---
layout: default
title: Home
nav_order: 1
description: "thingsvision: extracting features from deep neural nets"
permalink: /
---

# thingsvision - extracting features from deep neural nets.

`thingsvision` is a Python package that let's you easily extract image representations from many state-of-the-art neural networks for computer vision. In a nutshell, you feed `thingsvision` with a directory of images and tell it which neural network you are interested in. `thingsvision` will then give you the  representation of the indicated neural network for each image so that you will end up with one feature vector per image. You can use these feature vectors for further analyses. We use the word `features` for short when we mean "image representation".

To get started, please check out the [Getting Started](GettingStarted.md) page, or try our Colab notebooks for [Pytorch](https://colab.research.google.com/github/ViCCo-Group/thingsvision/blob/master/doc/pytorch.ipynb) and [Tensorflow](https://colab.research.google.com/github/ViCCo-Group/thingsvision/blob/master/doc/tensorflow.ipynb) .

## Model collection

Neural networks come from different sources. With `thingsvision`, you can extract image representations of all models from:
- [torchvision](https://pytorch.org/vision/0.8/models.html)
- [Keras](https://www.tensorflow.org/api_docs/python/tf/keras/applications)
- [timm](https://github.com/rwightman/pytorch-image-models)
- Self-supervised learning models (e.g. SimCLR) coming from [vissl](https://github.com/facebookresearch/vissl) or the Torch Hub.
- some custom models (VGG-16, Resnet50, Inception_v3 and Alexnet) trained on [Ecoset](https://www.pnas.org/doi/10.1073/pnas.2011417118)
- each of the many [CORnet](https://github.com/dicarlolab/CORnet) versions
- both [CLIP](https://github.com/openai/CLIP) variants (`clip-ViT` and `clip-RN`).<br> 

Note that you have to use the respective model name (`str`). For example, if you want to use VGG16 from torchvision, use `vgg16` as the model name and if you want to use VGG16 from TensorFlow/Keras, use the model name `VGG16`. You further have to specify the model source by setting the `source` parameter (e.g., `timm`, `torchvision`, `keras`).<br>

We provide more details on the model collection in the [Available Models](AvailableModels.md) page.

## Using `thingsvision` with the THINGS dataset:

If you happen to use the [THINGS image database](https://osf.io/jum2f/), make sure to correctly `unzip` all zip files (sorted from A-Z), and have all `object` directories stored in the parent directory `./images/` (e.g., `./images/object_xy/`) as well as the `things_concepts.tsv` file stored in the `./data/` folder. `bash get_files.sh` does the latter for you. Images, however, must be downloaded from the [THINGS database](https://osf.io/jum2f/) `Main` subfolder.  **The download is around 5GB**.

   - Go to <https://osf.io/jum2f/files/>
   - Select `Main` folder and click on "Download as zip" button (top right).
   - Unzip contained `object_images_*.zip` file using the password (check the `description.txt` file for details). For example:

        ``` {.bash}
        for fn in object_images_*.zip; do unzip -P the_password $fn; done
        ```

## Citation

If you use this GitHub repository (or any modules associated with it), we would grately appreciate to cite our [paper](https://www.frontiersin.org/articles/10.3389/fninf.2021.679838/full) as follows:

```latex
@article{Muttenthaler_2021,
	author = {Muttenthaler, Lukas and Hebart, Martin N.},
	title = {THINGSvision: A Python Toolbox for Streamlining the Extraction of Activations From Deep Neural Networks},
	journal ={Frontiers in Neuroinformatics},
	volume = {15},
	pages = {45},
	year = {2021},
	url = {https://www.frontiersin.org/article/10.3389/fninf.2021.679838},
	doi = {10.3389/fninf.2021.679838},
	issn = {1662-5196},
}
```
