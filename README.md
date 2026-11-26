# White Blood Cell Classification

Classifies microscope images of blood cells into **8 types** with a convolutional neural network, and compares it with transfer learning on MobileNetV2.

Classes: basophil, eosinophil, erythroblast, immature granulocyte (`ig`), lymphocyte, monocyte, neutrophil, platelet.

## Pipeline

1. Load images with `image_dataset_from_directory` at 128 × 128 pixels, with an 80/20 train/validation split.
2. Apply data augmentation and rescale pixel values to [0, 1].
3. Weight classes by inverse frequency (`compute_class_weight('balanced')`) to handle uneven class sizes.
4. Train a small CNN from scratch, then a MobileNetV2 transfer-learning model with frozen ImageNet weights.
5. Evaluate with a classification report and confusion matrix on the validation set.

## Dataset

The notebook expects the blood-cell image archive (`bloodcells_dataset/`, one folder per class). It is **not included**. Obtain it from its original source and update the paths in cell 1 or cell 5. The notebook was written for Google Colab, so cell 0 mounts Google Drive.

## Run it

1. Open the notebook in Google Colab or Jupyter.
2. Install the requirements: `pip install -r requirements.txt`.
3. Run the cells in order.

## Status

The notebook's saved outputs do not include a finished training run. Training in the saved version stopped during epoch 1 of 5. Re-run the notebook before quoting any accuracy figure. Record the final validation accuracy, macro F1 and the confusion matrix here once you have them.

## Project structure

```
Blood cells biomedical image classification.ipynb   # full pipeline
requirements.txt
```

## Author

Chillagattu Jathin · [LinkedIn](https://www.linkedin.com/in/jathins7)
