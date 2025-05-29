# Finetuning Image Caption Generation model using PyTorch XPU Backend

## Overview

Image caption generation is a crucial task in computer vision and natural language processing, enabling automatic description of visual content. This sample focuses on fine-tuning the VL model [BLIP*large*](https://huggingface.co/Salesforce/blip-image-captioning-large) using **Hephaestus dataset**, leveraging the Intel XPUs using **PyTorch XPU** backend for optimized performance.

## Contents

- [Sample Workflow](./README.md#sample-workflow)
- [Dataset](./README.md#sample-workflow)
- [Pre-requisites](./README.md#pre-requisites)
- [Structure of this directory](./README.md#Structure-of-this-directory)
- [Run the `finetune_image_captioning.ipynb` sample](./README.md#sample-structure)
   - [Using `uv`](./README.md#using-uv)
   - [AI PC from Intel](./README.md#ai-pc-from-intel)
- [Sample Execution](./README.md#sample-execution)


## Sample Workflow

<img width="1000" alt="image" src="./assets/workflow6.png">

## Dataset

The [Hephaestus dataset](https://github.com/Orion-AI-Lab/Hephaestus) is a large-scale multitask dataset designed to enhance the understanding of Interferometric Synthetic Aperture Radar (InSAR) data. This code sample leverages the data used in [Hephaestus: A large scale multitask dataset towards InSAR understanding](https://openaccess.thecvf.com/content/CVPR2022W/EarthVision/papers/Bountos_Hephaestus_A_Large_Scale_Multitask_Dataset_Towards_InSAR_Understanding_CVPRW_2022_paper.pdf) as published in CVPR 2022 workshop Earthvision. The dataset was created to address various computer vision problems related to geophysical processes and geology, particularly focusing on volcanoes. Out of a total of 19,919 InSAR images, we selected 1,374 images with unique captions for the fine-tuning task.

## Pre-requisites

| Optimized for                      | Description                                                                                                                                                                 |
| :----------------------------------| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| OS                        | Windows 11 64-bit (22H2, 23H2) and newer or Ubuntu* 22.04 64-bit (with Linux kernel 6.6+) and newer                                                                                                                                                                                                              |
| Hardware                  | Intel® Core™ Ultra Processors, Intel Arc™ Graphics, or Intel Graphics, Intel® Data Center GPU Max Series                                                                                                                                                                                                         |
| Software                  | [Intel® GPU drivers from Intel® Arc™ & Iris® Xe Graphics for Windows](https://www.intel.com/content/www/us/en/download/785597/intel-arc-iris-xe-graphics-windows.html), [uv](https://docs.astral.sh/uv/)                                                                                                                                                                                       |
| Minimum RAM required      | 32 GB or more                                                                                                                                                                        |
| Optional                  | Monitor GPU Utilization using [Intel XPU Manager](https://github.com/intel/xpumanager)
                                                                                     


## Structure of this directory

    
This sample directory contains:

| **Notebook**                            | **Description**                                                                                   |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------|
| [finetune_image_captioning.ipynb](./finetune_image_captioning.ipynb) | The python script to finetune a VL model for image captioning.       |

| **Assets :Input Dataset**     | **Description**                                                                                   |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------|
| [images.zip](./Hephaestus_dataset/images.zip)     | Contains the 1374 images for the finetuning.                                          |
| [annotations.zip](./Hephaestus_dataset/annotations.zip)       | Each annotation files contains the details about their respective image including their caption.       |

| **Assets :Outputs example**             | **Description**                                                                                   |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------|
| [loss_vs_epoch.png](./assets/loss_vs_epoch.png) | Plots training loss and validation loss for each epoch.                                   |
| [bertscore.png](./assets/bertscore.png)   | Plots the BERT score for the test set before and after finetuning                               |
| [results_before_training.csv](./assets/results_before_training.csv)   | Contains the generated caption, actual caption and their BERT score for images from the test set, prior to finetuning |
| [results_after_training.csv](./assets/results_after_training.csv)   | Contains the generated caption, actual caption and their BERT score for images from the test set, post finetuning |



## Run the `Finetune Image Captioning` Sample:

### Using `uv`

The sample uses [uv](https://docs.astral.sh/uv/) for environment management. Steps to install `uv` can be found [here](https://docs.astral.sh/uv/getting-started/installation/). 
    
1. In a terminal, navigate to `Finetune-Image-Captioning` folder:
   ```bash
   cd <path/to/Finetune-Image-Captioning/folder>
   ```
   
2. Launch Jupyter Notebook

   ```bash
   uv run jupyter-lab
   ```
   > **NOTE:** Run the below command if you face any dependency issues:
   > ```bash
   >   uv clean
   > ```

### AI PC from Intel
<div class="alert alert-block alert-info"> <b>NOTE:</b> You can run the step on both, <b>Windows and Ubuntu</b>. </div>

1. Open the [finetune_image_captioning.ipynb](./finetune_image_captioning.ipynb) notebook file in the jupyter notebook, select the default kernel i.e. `Python(ipykernel)` and run the code cells one by one in the notebook.

## Sample execution 
Users would be observing the below shown output by executing the cell for inferencing prior to finetuning.
<img alt="image" width=600 src="./assets/screenshot1.jpg"/>

Users would be observing the below shown output by executing the cell for training and inferencing post training.
<img alt="image" width=600 src="./assets/screenshot2.jpg"/>

Users would be observing GPU utilization as this sample runs is optimized to run on Intel XPUs
<img alt="image" width=600 src="./assets/gpu_usage_xpu.png"/>

## License

Code samples are licensed under the MIT license. See [License.txt](https://github.com/oneapi-src/oneAPI-samples/blob/master/License.txt) for details.

Third party program Licenses can be found here: [third-party-programs.txt](https://github.com/oneapi-src/oneAPI-samples/blob/master/third-party-programs.txt).
