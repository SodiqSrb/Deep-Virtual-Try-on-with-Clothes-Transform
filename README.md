# Deep Virtual Try-on with Clothes Transform Using 3d models Avatar.
Source code for paper "Deep Virtual Try-on with Clothes Transform"
<img height="300" src=![IMG-20230118-WA0000](https://user-images.githubusercontent.com/114579958/213151565-c6d69783-3a76-4d7e-b80e-1e9b50db8d0d.jpg)

## Overall Architecture
<img height="500" src="https://github.com/b01902041/Deep-Virtual-Try-on-with-Clothes-Transform/blob/master/readme_img/All.png">

## Dependencies
Install dependencies using pip.
```shell
pip install -r requirements.txt
```

## Step1: CAGAN 
<img height="200" src="https://github.com/b01902041/Deep-Virtual-Try-on-with-Clothes-Transform/blob/master/readme_img/CAGAN.png">

### code and data ###
* Training:  `CAGAN.py`
```
python CAGAN.py
```
* Testing: `Testing_with_fixed_data.py`
```
python Testing_with_fixed_data.py
```
* Data: `MVC_image_pairs_resize_new.zip`

### parameters in code ###

#### Training: CAGAN.py

* Data should be put in

`"./MVC_image_pairs_resize_new/1/*.jpg"` (for person images)

`"./MVC_image_pairs_resize_new/5/*.jpg"` (for clothes images)

> 470: data = "data folder name"
>
> 471: train_A = "person images folder name"
>
> 473: filenames_1 = "person images folder name"
>
> 474: filenames_5 = "clothes images folder name"
>
> 617, 618: set "save model path" 

#### Testing: Testing_with_fixed_data.py

* Data should be put in

`"./MVC_image_pairs_resize_new/1/*.jpg"` (for person images)

`"./MVC_image_pairs_resize_new/5_test/*.jpg"` (for clothes images)

>215: set "model path"
>
>220: data = "data folder name"
>
>221: train_A = "person images folder name"
>
>222: filenames_5 = "clothes images folder name"
>
>224: out_root_dir = "output folder name"
>
>225: origin_dir = "save input person images"
>
>226: target_dir = "save target clothes images"
>
>227: output_dir = "save output images"
>
>228: mask_dir = "save output masks"
>
>230: testing_number = "how much data you want to test"


## Step2: Segmentation ##
<img height="200" src=![IMG-20230118-WA0001](https://user-images.githubusercontent.com/114579958/213151971-e59e903d-8e38-4657-aadf-715349d4960e.jpg)

### code ###
https://github.com/Engineering-Course/LIP_SSL

* Modify mask: `modify_mask.m`

* Save the masks file to png file: `show.m`

* Combine all the masks: `combine_with_CAGANmask.m`


## Step3: Transform ##
<img height="100" ![IMG-20230117-WA0056](https://user-images.githubusercontent.com/114579958/213150347-8a9069bd-2954-4325-b541-f79205ff726f.jpg)

### code and data ###

* Training: `unet.py` `data.py`
```
python unet.py
```

* Testing: `Testing_unet.py`
```
python Testing_unet.py
```
* Data: `transform_data.zip` `transform_test_data.zip`

### parameters in code ###
#### Training: unet.py

>336: model_dir = "save model path"
>
>337: result_dir = "save results path"
>
>223: set "loss type"

#### data.py

>15: set "data path"


#### Testing: Testing_unet.py

>16: test_data_path = "data path"
>
>17: test_img_folder = "target clothes image folder name"
>
>18: test_mask_folder = "mask folder name"
>
>19: model_name = "model name"
>
>20: result_dir = "save results path"


## Step4: Combination ##
<img height="200" ![IMG-20230117-WA0055](https://user-images.githubusercontent.com/114579958/213144243-4d49c259-5dae-4fa2-93e6-5ba975171fd1.jpg)



