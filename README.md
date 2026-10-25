# Cricket Shot Classification with ResNet-50

# Cricket Shot Classification with ResNet-50

A computer-vision project that uses transfer learning with a pretrained **ResNet-50** model to classify cricket-shot images into four categories.

## Project overview

The notebook builds a PyTorch image-classification pipeline. It loads labeled images, creates a stratified train/validation split, applies image transformations, replaces the final ResNet-50 classification head, trains the new head, and evaluates predictions.

### Classes

- `drive`
- `legglance-flick`
- `pullshot`
- `sweep`

### Workflow

1. Load labeled images from class-specific folders.
2. Split images into training and validation sets (80/20, stratified).
3. Resize images to `224 × 224` and normalize them using ImageNet statistics.
4. Load ResNet-50 pretrained weights (`IMAGENET1K_V2`).
5. Freeze the pretrained backbone and train a custom classification head.
6. Evaluate the model with a confusion matrix, classification report, and prediction visualizations.

## Recorded result

The notebook's saved output reports approximately **97% validation accuracy** on 945 validation images for one run. Results depend on the dataset, split, training environment, and random factors; rerun the notebook to reproduce and verify them.

## Tech stack

- Python
- PyTorch and Torchvision
- scikit-learn
- NumPy
- Matplotlib and Seaborn
- Pillow
- Jupyter Notebook

## Dataset setup

The image dataset is **not included** in this repository. Use a dataset you have permission to use and distribute.

Create this directory structure from the repository root:

```text
data/
└── cricket_shots/
    ├── drive/
    ├── legglance-flick/
    ├── pullshot/
    └── sweep/
```

Put the corresponding image files inside each class folder. Supported extensions in the notebook include `.png`, `.jpg`, `.jpeg`, and `.webp`.

The notebook uses the relative path `data/cricket_shots`, so launch Jupyter from this repository's root directory.

## Installation

Create and activate a virtual environment, then install the dependencies:

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

macOS/Linux:

```bash
source .venv/bin/activate
python -m pip install -r requirements.txt
```

For GPU training, install the PyTorch/Torchvision build appropriate for your CUDA setup by following the [official PyTorch installation selector](https://pytorch.org/get-started/locally/). CPU execution is also possible but may be slower.

## Run the notebook

```bash
jupyter notebook CNN_ResNet50_Cricket_Shots.ipynb
```

Run the cells from top to bottom after setting up the dataset.

## Repository structure

```text
cnn-resnet50-cricket-shot-classification/
├── CNN_ResNet50_Cricket_Shots.ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── data/                  # Local dataset; not committed
```

## Notes and limitations

- The dataset is not bundled with the repository.
- The reported score is from a saved notebook run, not a guarantee of performance on unseen data.
- The notebook freezes the pretrained backbone and trains the replacement classification head.
- Dataset quality, class balance, duplicate images, and train/validation leakage can affect reported accuracy.
- Pretrained weights may need to be downloaded the first time the notebook runs.

## License

No license has been specified. Add a `LICENSE` file if you want to define reuse and distribution terms.
