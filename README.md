
# EAST: An Efficient and Accurate Scene Text Detector

This is a Keras implementation of EAST insprired from [argman](https://github.com/argman/EAST)'s work.

The original paper by Zhou et al. is available on [arxiv](https://arxiv.org/abs/1704.03155).

+ Only RBOX geometry is implemented
+ Differences from the original paper
    + Uses ResNet-50 instead of PVANet
    + Uses RMSprop optimizer instead of the original Adam

### Data

You can use your own data, but the annotation files need to conform the ICDAR 2015 format.

ICDAR 2015 dataset can be downloaded from this [site](http://rrc.cvc.uab.es/?ch=4&com=introduction). You need the data from Task 4.1 Text Localization.\
You can also download the [MLT dataset](http://rrc.cvc.uab.es/?ch=8&com=introduction), which uses the same annotation style as ICDAR 2015, there.

Alternatively, you can download a training dataset consisting of all training images from ICDAR 2015 and ICDAR 2013 datasets with annotation files in ICDAR 2015 format [here](https://drive.google.com/a/nlab-mpg.jp/uc?id=1p9a3K0czxIJ6zx0cFMURnKg5ydTK3jlk&export=download).\
You can also get a subset of validation images from the MLT 2017 dataset containing only images with text in the Latin alphabet for validation [here](https://drive.google.com/a/nlab-mpg.jp/uc?id=1Ljye_kHCfZ54wHQINOivgClUAj8EF-v-&export=download).\
The original datasets are distributed by the organizers of the [Robust Reading Competition](http://rrc.cvc.uab.es/) and are licensed under the [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/).

### Training

You need to put all of your training images and their corresponding annotation files in one directory. The annotation files have to be named `gt_IMAGENAME.txt`.\
You also need a directory for validation data, which requires the same structure as the directory with training images.

Training is started by running `train.py`. It accepts several arguments including path to training and validation data, and path where you want to save trained checkpoint models. You can see all of the arguments you can specify in the `train.py` file.

#### Example Notebook
You can use the [EAST.ipynb](https://github.com/anish52/EAST-Text-Detector/blob/main/EAST.ipynb) jupyter notebook to understand a simpler version of the implementation.

### Test

The images you want to classify have to be in one directory, whose path you have to pass as an argument. Classification is started by running `eval.py` with arguments specifying path to the images to be classified, the trained model, and a directory which you want to save the output in.

#### Execution example
```
python eval.py --gpu_list=0 --test_data_path=../data/ICDAR2015/test/ --model_path=tmp/icdar2015_east_resnet50/model_XXX.h5 --output_dir=tmp/icdar2015_east_resnet50/eval/
```

### Detection examples
![image_1](examples/img_13.jpg)
![image_2](examples/img_42.jpg)
