# Part 2: Computer Vision Problem Formulation and CNN Prototype

## Dataset source
Shared Google Drive folder: https://drive.google.com/drive/folders/1akV6po4Nrgkc3yQrJkzA6cJlV-wBvUYs?usp=sharing

Raw image files are intentionally not included in this repository. Place the original `images/` folder and `labels.csv` in a local `data/` directory before running the notebook.

## Problem identification
This is an **image classification** problem because each image belongs to exactly one defect category. The classes are: dent, normal, scratch, stain. The model learns visual patterns and predicts one class label per image.

## Dataset exploration
- Total images: 480
- Number of classes: 4
- Image dimensions observed from sample: 96 x 96 pixels
- Images per class:

| class   |   image_count |
|:--------|--------------:|
| dent    |           120 |
| normal  |           120 |
| scratch |           120 |
| stain   |           120 |

The dataset is balanced because each class has a similar number of images.

## Preprocessing
Images are resized to a fixed size, normalized to 0-1 pixel values, split into train/validation/test sets, and optionally augmented using random flips/rotations/zoom to improve generalization.

## CNN architecture
The notebook defines a CNN with convolution, ReLU activation, max pooling, flattening, dense layers, dropout, and a softmax output layer for four-class classification.

## Evaluation outputs
- `results/accuracy_loss_curves.png`: training and validation curves.
- `results/confusion_matrix.png`: class-level prediction comparison.
- `sample_predictions/prediction_outputs.png`: sample images from each class.

## CNN concept explanation
**Convolution:** A convolution layer applies small filters over an image to detect patterns such as edges, textures, scratches, stains, and shapes.

**Pooling:** Pooling reduces spatial size while keeping important features, making the network faster and more robust to small shifts in the image.

**ReLU:** ReLU keeps positive values and turns negative values to zero. It is simple, fast, and helps CNNs learn non-linear visual patterns.

**Why CNNs for images:** Regular dense networks ignore spatial structure. CNNs preserve local relationships between nearby pixels, making them more suitable for visual data.

## Business use case: Manufacturing
A CNN defect classifier can support automated quality inspection on a production line. It can flag normal, scratch, dent, or stain cases, reduce manual inspection effort, improve consistency, and prioritize human review for uncertain or high-risk items.
