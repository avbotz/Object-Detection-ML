# Object-Detection-ML

Instructions for training machine learning models. As of January 9, 2021, 
Botz uses the EfficientDet-D0 model for detecting objects.

## Requirements

- Python 3
- [LabelImg](https://github.com/tzutalin/labelImg.git)
- [Custom-Dataset-Tools](https://github.com/CraigWang1/custom-dataset-tools.git)

## Instructions

1 - Collect images. Store all of them in a single folder.
    If the images are located within multiple sub-folders within a single main folder,
    use custom-dataset-tools/dataset/extract_sub_dirs.py (example usage @ custom-dataset-tools/dataset/).

2 - Use custom-dataset-tools' `renumber_dir.py` to renumber the images
    to renumber the images in sequential order.
    Example usage:

        $ cd custom-dataset-tools/dataset
        $ python3 renumber_dir.py \
            --image_dir /home/joe/images \
            --annot_dir /home/joe/images \
            --ext png \
            --start 0

3 - Label images with labelImg's labelling tools. 
    Use custom-dataset-tools' `labelimg_help.py` to speed up the process.
    Example usage:

        $ cd custom-dataset-tools/labelling
        $ python3 labelimg_help.py

4 - Resize the images so that the longest size of the image is 512 pixels long.
    This is the size of the image that the EfficientDet-D0 model uses.
    Use custom-dataset-tools' `resize.py` for this purpose.
    Example usage:

        $ cd custom-dataset-tools/dataset
        $ python3 resize.py \
            --image_dir /home/joe/img_dset \
            --annot_dir /home/joe/img_set \
            --save_dir /home/joe/resized_dset \
            --ext png \
            --one_side 512

5 - Zip the folder with the resized dataset.

6 - Upload the zip file to Google Drive.

7 - Train the ML models online using [this Colab link](https://colab.research.google.com/notebook#fileId=1Qn06AoMEO0thnaN06ciW7N21iSV0prxE&offline=true&sandboxMode=true).
    Follow the instructions in the comments of the Colab. Make sure that after you have finished 
    training, follow the subsequent instructions to save the model in .pb format. This is the
    format that the sub uses. 
    Make your own copy of the Colab if you wish to make changes.

## TODO

- Add pictures
- Add an instructions section for training a model on a personal PC