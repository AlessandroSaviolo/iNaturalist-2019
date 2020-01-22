# iNaturalist 2019

Final project "iNaturalist 2019 at FGVC6 Fine-grained classification spanning a thousand species"
https://www.kaggle.com/c/inaturalist-2019-fgvc6

## BBN: Bilateral-Branch Network with Cumulative Learning for Long-Tailed Visual Recognition with Shift-Invariant Convolutional Neural Network
This repository is based on the official PyTorch implementation of paper [BBN: Bilateral-Branch Network with Cumulative Learning for Long-Tailed Visual Recognition](https://arxiv.org/abs/1912.02413).

## Main requirements

  * **PyTorch ≥1.0**
  * **torchvision ≥0.2.2_post3**
  * **TensorboardX**
  * **Python 3**

## Pretrain models for iNaturalist

We provide the BBN pretrain models for iNaturalist 2018: [Google Drive](https://drive.google.com/open?id=18aT-eIpmxQMP9PrNOB1Q5Vjmzr7tvEdb)

  ## Usage
```bash
# To train long-tailed iNaturalist2019 with imbalanced ratio of 50:
python main/train.py  --cfg configs/iNaturalist2019.yaml     

# To validate with the best model:
python main/valid.py  --cfg configs/iNaturalist2019.yaml
```

You can change the experimental setting by simply modifying the parameter in the yaml file.

## Data format

The annotation of a dataset is a dict consisting of two field: `annotations` and `num_classes`.
The field `annotations` is a list of dict with
`image_id`, `fpath`, `im_height`, `im_width` and `category_id`.

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
The images and annotations can be downloaded at [iNaturalist 2019](https://www.kaggle.com/c/inaturalist-2019-fgvc6/data)

```bash
# Convert from the original format of iNaturalist
python tools/convert_from_iNat.py --file train2019.json --root iNat19/images --sp jsons
```
