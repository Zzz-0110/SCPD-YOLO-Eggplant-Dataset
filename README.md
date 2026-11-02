# SCPD-YOLO-Eggplant-Dataset
## Download

The original images and bounding box annotations are hosted on Zenodo:

[Download the dataset from Zenodo](https://doi.org/10.5281/zenodo.23879164)

DOI: 10.5281/zenodo.23879164
# Eggplant Field Detection Dataset

## Overview

This dataset contains 1,700 original images of eggplants collected in a field environment, together with bounding box annotations for eggplant fruit detection. The images include occlusion, dense fruit distributions, small targets, and varying illumination conditions.

The dataset was used in the study introducing SCPD-YOLO, a lightweight eggplant detection network. This release provides the original images, annotations, and the original training, validation, and test split.

## Dataset composition

| Subset     | Original images |
| ---------- | --------------: |
| Training   |           1,208 |
| Validation |             260 |
| Test       |             232 |
| Total      |           1,700 |

Among the original images, 162 belong to six groups defined by the combination of shooting position and illumination conditions. Five groups were assigned to training and one to validation. The remaining images were randomly partitioned. The `train/`, `val/`, and `test/` directories preserve the assignment used in the study; use this partition rather than generating a new random split when comparing results.

## File organization

The data should be organized as follows after extraction:

```text
Eggplant_dataset/
├── train/
│   ├── images/             1,208 original training images (.jpg)
│   └── labels/             1,208 corresponding annotations (.txt)
├── val/
│   ├── images/             260 validation images (.jpg)
│   └── labels/             260 corresponding annotations (.txt)
├── test/
│   ├── images/             232 test images (.jpg)
│   └── labels/             232 corresponding annotations (.txt)
├── dataset.yaml            Dataset paths and class definition
├── README.md
└── LICENSE
```

Images and annotations are paired within each subset. For example, `train/images/eggplant_000001.jpg` corresponds to `train/labels/eggplant_000001.txt`. The same filename can occur in different subsets, so retain the directory structure rather than combining all images or labels into a single folder.

## Annotation format

The dataset contains one object class:

| Class ID | Class name |
| -------- | ---------- |
| 0        | Eggplant   |

Annotations are provided in YOLO text format. Each image has a corresponding `.txt` file with the same filename stem. Each line describes one annotated fruit:

```text
class_id x_center y_center width height
```

The center coordinates, width, and height are normalized by the image width and height. Coordinates are measured from the top-left corner of the image. Each image can contain multiple annotated fruits.

## Download and use

Download the dataset archives attached to this Zenodo record. The training set is distributed across three independently extractable archives: train1.rar, train2.rar, and train3.rar, containing 400, 400, and 408 image–annotation pairs, respectively.

After extraction, combine the images from train1/images/, train2/images/, and train3/images/ into train/images/. Similarly, combine their annotation files into train/labels/. Preserve all original filenames. Place the extracted val/ and test/ directories alongside train/, following the directory structure shown above.

Place dataset.yaml in the dataset root directory and set its path field to the absolute location of the dataset on your system. Retain the supplied training, validation, and test partition when comparing results with this study.

## License and attribution

The released images and annotations are provided under the **Eggplant Dataset Personal Non-Commercial Use License**, a custom license included in `LICENSE`. 

The license permits individuals to use the dataset for personal, non-commercial learning, research, and evaluation, with attribution. It does not automatically authorize organizational, institutional, or commercial use; contact the dataset provider for permission for uses outside the permitted scope.

When using the dataset or reporting results based on it, acknowledge **Eggplant Field Detection Dataset**, identify its original repository URL and release version, and retain the supplied attribution and license notices. Indicate any modifications. Publication details will be added when available.

## Contact

For questions about the dataset or to report annotation issues, contact:

**zhuangheng0110@163.com**
