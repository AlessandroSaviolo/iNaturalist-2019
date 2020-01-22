# iNaturalist 2019

This project is part of a series of projects for the course _Selected Topics in Visual Recognition using Deep Learning_ that I attended during my exchange program at National Chiao Tung University (Taiwan). See `task.pdf` for the details of the assignment. See `report.pdf` for the report containing the representation and the analysis of the produced results.

The purpose of this project is to implement a classifier for the [iNaturalist 2019 Challenge](https://www.kaggle.com/c/inaturalist-2019-fgvc6). The implementation is based on the official PyTorch implementation of the paper "[BBN: Bilateral-Branch Network with Cumulative Learning for Long-Tailed Visual Recognition](https://arxiv.org/abs/1912.02413)". 

## 1. Requirements

- PyTorch ≥ 1.0
- torchvision ≥ 0.2.2_post3
- TensorboardX
- Python 3.x

## 2. Dataset

The images and annotations can be downloaded from [iNaturalist 2019](https://www.kaggle.com/c/inaturalist-2019-fgvc6/data).

## 3. Data format

The annotation of a dataset is a dictionary consisting of two fields: `annotations` and `num_classes`.
The field `annotations` is a list of dict with `image_id`, `fpath`, `im_height`, `im_width` and `category_id`.

Here is an example.
```
{
    'annotations': [
                    {
                        'image_id': 1,
                        'fpath': '/home/BBN/iNat19/images/train_val2019/Plantae/7477/3b60c9486db1d2ee875f11a669fbde4a.jpg',
                        'im_height': 600,
                        'im_width': 800,
                        'category_id': 7477
                    },
                    ...
                   ]
    'num_classes': 8142
}
```

You can use the following code to convert from the original format of iNaturalist. 
```
python tools/convert_from_iNat.py --file train2019.json --root iNat19/images --sp jsons
```

## 4. Pretrain Model

- [BBN pretrain model for iNaturalist 2018](https://drive.google.com/open?id=18aT-eIpmxQMP9PrNOB1Q5Vjmzr7tvEdb)

## 5. Usage

To train long-tailed iNaturalist2019 with imbalanced ratio of 50:
```
python main/train.py  --cfg configs/iNaturalist2019.yaml     
```

To validate with the best model:
```
python main/valid.py  --cfg configs/iNaturalist2019.yaml
```

You can change the experimental setting by simply modifying the parameter in the yaml file.

## 6. Credits

The [Megvii-Nanjing GitHub Repository](https://github.com/Megvii-Nanjing/BBNb) has deeply helped the development of this project.
