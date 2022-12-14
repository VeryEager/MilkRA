# Milk Droplet Analysis

## Preprocessing How-To

There are several assumptions made about the structure of the project which cannot be violated. You will first need to place your data into the `data/` directory. Each sub-directory within `data/` should contain a single set of droplet images. Please keep your naming conventions consistent, as folder and file names are used during the export process and can cause confusion if named ambiguously.

Please note that the input directory `data/` and the output directory `output/` are not cleared between runs; this is to ensure data is not accidentally lost. However, files within the `output/` directory are at risk of being overwritten when the program is run again. Copy results from the `output/` directory to your local device immediately after running the script if you wish to keep them.

### Running the Script

First activate your conda environment using the terminal command `conda activate milkra`. After this, navigate to the directory of the script, `cd path/to/MilkRA/preprocessing`. To run the script, use the terminal command `python main.py`. There are several command-line arguments available:

| Argument           | Value               | Description                                                                                                                                                                                         |
|--------------------------|--------------------------|--------------------|
| `--mode`           | `single` or `multi` | Mode of the script; under `single` only one provided sub-directory in `data/` is preprocessed. Under `multi` all sub-directories are preprocessed. Default `single`                                 |
| `--annotate`       |                     | Whether to export annotated versions of droplet images with the reflection line and midpoint height drawn.                                                                           |
| `--crop`           |                     | Whether to automatically crop droplet images vertically and save them for future use. If images have already been cropped in a previous execution, their cropped versions are used. |
| `--datapath`       | `<directory>`       | Relative path to the input directory. Default `../data`                                                                                                                                             |
| `--csv_exprpath`   | `<directory>`       | Relative path to the output directory for .csv files. Default `../output/csv`                                                                                                                       |
| `--img_exprpath`   | `<directory>`       | Relative path to the output directory for annotated image files. Default `../output/annotations`                                                                                                    |
| `--croppath`       | `<directory>`       | Relative path where cropped images are saved if cropping is performed. Default `../cropped`                                                                                                         |
| `--dataset`        | `<folder name>`     | **Required when** `--mode = single`. The subdirectory of `data/` to preprocess. Default `None`                                                                                                      |
| `--height_radius`  | `<integer>`         | Radius to use when calculating height, enables smoother height estimations. When `0`, only the target column's height is calculated (no smoothing). Default `2`                                    |
| `--height_method`  | `top` or `bottom`   | Method to calculate the height of the droplet, using either a top-down or bottom-up algorithm. Default `top` |


The most important argument is `--mode`, which **must be added as an argument to any script run**. Note that in the `single` mode, the `--dataset` argument **must also be provided**. To add arguments to a script run, modify the terminal command used to run the python file: `python main.py --mode single --dataset example --annotate`.

### Recommendations
To ensure height measurements are correct it is recommended to run the script with `--annotate` and verify the annotated image files manually.  

In the ideal scenario (no measurement issues which would require a change of parameters & a re-run) an imageset only needs to be run once to obtain the .csv files. However, with `--annotate` and `--crop` the imageset is effectively copied twice in local storage. Therefore after an imageset has been processed without error it is strongly recommended that the `cropped/` and `output/annotations` directories are cleared.

### Troubleshooting
Occassionally scripts may produce errors - this is normal and is often the result of artifact(s) to the side of the droplet. Re-running these troublesome imagesets with `--crop` frequently fixes this issue. Should issues continue to persist, get in touch with Asher (stoutashe@myvuw.ac.nz). Attach the imageset and describe your script settings.


### Understanding Extracted Features
In every run two outputs are always guaranteed in the form of `csv` files. `<name>_raw.csv` contains raw measurements for each point measured, along with other information about the imageset such as the location of the midpoint and reflection lines. `<name>_preprocessed.csv` only contains pairwise means for each measured pair. For a clearer illustration, see the figure below

![alt text](https://github.com/veryeager/milkra/blob/main/content/README_diagram.png?raw=true)

## Machine Learning
### Baselines

## Visualizations
