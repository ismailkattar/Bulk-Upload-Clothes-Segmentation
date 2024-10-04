<p align="center">
  <h1 align="center">Bulk Upload Image Segmentation</h1>
</p>

# Introduction
Ever struggled with the daily question, "What should I wear?". This project focuses on the initial step towards building a personalized AI-powered wardrobe. By utilizing Instance Segmentation, a computer vision technique, our model can extract and classify itmes from images. This foundation lays the groundwork for the future developments, such as personalized outfit recommendations.

<div align="center">
  <img src="https://github.com/ismailkattar/ZAKA-GIT-TRAINING/blob/main/Images/Prediction.png" alt="Result"/>
</div>

# Data
For Training, different number of images were used from Fashionpedia. In order to reduce the complex structure of the dataset, half of the categories were dropped(23 out of 46) and the remaining categories are: 
```
+---------+-----------------------------------------+----------------+
| ClassId |                   Name                  | SuperCategory  |
+---------+-----------------------------------------+----------------+
|    0    |                   shoe                  | legs and feet  |
|    1    |                  dress                  |   wholebody    |
|    2    |         top, t-shirt, sweatshirt        |   upperbody    |
|    3    |                  pants                  |   lowerbody    |
|    4    |                  jacket                 |   upperbody    |
|    5    |               bag, wallet               |     others     |
|    6    |                   belt                  |     waist      |
|    7    |              shirt, blouse              |   upperbody    |
|    8    |                  skirt                  |   lowerbody    |
|    9    |                 glasses                 |      head      |
|    10   |            tights, stockings            | legs and feet  |
|    11   | headband, head covering, hair accessory |      head      |
|    12   |                  watch                  | arms and hands |
|    13   |                   coat                  |   wholebody    |
|    14   |                  shorts                 |   lowerbody    |
|    15   |                   hat                   |      head      |
|    16   |                 sweater                 |   upperbody    |
|    17   |                  scarf                  |     others     |
|    18   |                 cardigan                |   upperbody    |
|    19   |                 jumpsuit                |   wholebody    |
|    20   |                   vest                  |   upperbody    |
|    21   |                   cape                  |   wholebody    |
|    22   |                leg warmer               | legs and feet  |
+---------+-----------------------------------------+----------------+
```
For more details about the original dataset: [iMaterialists (Fashion) 2020 FGVC7](https://www.kaggle.com/c/imaterialist-fashion-2020-fgvc7/overview/evaluation) and [Fashionpedia](https://fashionpedia.github.io/home/index.html).

# Training Details 
![image](https://github.com/user-attachments/assets/2962ffdb-3dd7-4da2-9422-a4ee42481c80)


Since our case need an accurate model with high speed and <a href="https://docs.ultralytics.com/tasks/segment/">YOLOv8-seg</a> architecture has proven to contain both. In this study, 3 different training runs with YOLOv8s-seg has been conducted:
<ul>
  <li>First: Trained on 1500 images and 160 for validation, 50 epochs, image size = 1024 and <a href="https://docs.ultralytics.com/usage/cfg/">the default YOLOv8 augmentation settings</a>.</li>
  <li>Second: Trained on 7.5K images and 1K for validation, 200 epochs, image size = 1024 and <a href="https://docs.ultralytics.com/usage/cfg/">the default YOLOv8 augmentation settings</a>.</li>
  <li>Last: Trained on 3600 images and 900 for validation, 50 epochs, image size = 640 and  <a href="https://docs.ultralytics.com/usage/cfg/">the default YOLOv8 augmentation settings</a>. </li>
</ul>
**Note** : For segmentation, YOLOv8 consist of five detection modules instead of 3.

# Results
Here are some visual and numerical validation results: 

### Numerical Result
|Run| seg_loss | cls_loss | Precision(M) | Recall(M) | mAP50(M) |
|:---:|:---:|:---:|:---:|:---:|:---:|
| First | 1.78 | 1.59 | 0.53 | 0.39 | 0.41 |
| Second | 1.67 | 1.49 | 0.53 | 0.32 | 0.31 |
| Last | 1.61 | 1.29 | 0.56 | 0.46 | 0.46 |

### Visual Results

<p align="center">
  <h4 align="center">Prediciton using First Run</h1>
</p>

<div align="center">
  <img src="https://github.com/ismailkattar/ZAKA-GIT-TRAINING/blob/main/Images/First Resullt/Image 1.png" alt="Result"/>
</div>

<p align="center">
  <h4 align="center">Prediciton using Second Run</h1>
</p>

<div align="center">
  <img src="https://github.com/ismailkattar/ZAKA-GIT-TRAINING/blob/main/Images/Second Result/Image 1.png" alt="Result"/>
</div>

<p align="center">
  <h4 align="center">Prediciton using Last Run</h1>
</p>

<div align="center">
  <img src="https://github.com/ismailkattar/ZAKA-GIT-TRAINING/blob/main/Images/Last Result/Image 1.png" alt="Result"/>
</div>

# References

* [iMaterialist (Fashion) 2020 at FGVC7](https://kaggle.com/competitions/imaterialist-fashion-2020-fgvc7)
* [Fashionpedia](https://fashionpedia.github.io/home/index.html)
* [ultralytics](https://docs.ultralytics.com/)
