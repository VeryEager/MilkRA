# Milk Droplet Analysis

## Preprocessing How-To

There are several assumptions made about the structure of the project which cannot be violated. You will first need to place your data into the `data/` directory. Each sub-directory within `data/` should contain a single set of droplet images. Please keep your naming conventions consistent, as folder and file names are used during the export process and can cause confusion if named ambiguously.

Please note that the input directory `data/` and the output directory `output/` are not cleared between runs; this is to ensure data is not accidentally lost. However, files within the `output/` directory are at risk of being overwritten when the program is run again. Copy results from the `output/` directory to your local device immediately after running the script if you wish to keep them.

### Running the Script

First activate your conda environment using the terminal command `conda activate milkra`. After this, navigate to the directory of the script, `cd path/to/...MilkRA/preprocessing`. To run the script, use the terminal command `python main.py`. There are several command-line arguments available:

| Argument  | Value | Description | 
| ------------- | ------------- | ---------- |
| `--mode`  | `single` or `multi` | Mode of the script; under `single` only one provided sub-directory in data is preprocessed. Under `multi` all sub-directories are preprocessed. Default `single`  |
| `--annotate`  | `True` or `False` | Whether to export annotated versions of droplet images with the reflection line and midpoint height drawn. Default `False`  |
| `--datapath`  | `<directory>`  | hh |
| `--csv_exprpath`  | `<directory>` | hh |
| `--img_exprpath`  | `<directory>` | hh |
| `--dataset`  | `<folder name>` | **Only required when `--mode = single`.** The subdirectory of `data/` to preprocess. Default `None` |

The most important argument is `--mode`, which **must be added as an argument to any script run**. 
