<div align="center">
    <h2 align="center">Data Leakage Detection and De-duplication in Large Scale Geospatial Image Datasets</h2>
    <h3 align="center">Oral @ CVPR 2026</h3>
    <a href="https://yeshwanth95.github.io/">Yeshwanth Kumar Adimoolam<sup>1</sup></a>, <a href="https://poullis.org/">Charalambos Poullis<sup>2</sup></a>, <a href="https://melinos.github.io/">Melinos Averkiou<sup>3</sup></a><br>
    <sup>1</sup>Cyprus University of Technology, <sup>2</sup>Concordia University, <sup>3</sup>CYENS CoE, Cyprus
</div>

[[Demo Website](https://datainspector.app/)]    [[Paper](https://arxiv.org/abs/2304.02296)]    [[Video](https://youtu.be/NzW8-Q3upx0?si=vvbDnZKaZDTyzUFl)]

## Updates

April 13, 2023 - We have released an interactive web interface to manually inspect the full extent of data leakage and duplication in the AICrowd Mapping Challenge v1 dataset. The web interface can be found at [datainspector.app](https://datainspector.app/)


## Highlights
- We propose an easy-to-adopt de-duplication and leakage detection pipeline for large-scale image datasets that utilizes collision detection of perceptual hashes of images.
- We employ the proposed de-duplication pipeline to identify and eliminate instances of data duplication and leakage in the AICrowd mapping challenge dataset. Approximately 250k of the 280k training images were either exact or augmented duplicates.
- We demonstrate cases of significant overfitting of the recent state-of-the-art methods, potentially invalidating the results of a number of prior art reporting on this dataset for the task of building footprint extraction.

## Installation

```
conda create -n hash_and_search python=3.10
conda activate hash_and_search
pip install -r requirements.txt
```
Alternatively, the following requirements can be installed manually:
```
ImageHash
numpy
Pillow
PyWavelets
scipy
tqdm
```

## Compute Hashes
To compute p-hashes for images in a folder, run:

```
python compute_hashes.py <input_images_directory> <output_directory> <output_hashtable_filename>
```

To compute p-hashes of augmented images in the dataset, run:
```
python compute_hashes_augmented.py <input_images_directory> <output_directory> <output_hashtable_filename>
```

## Compare Hashes
Once hashtables are constructed for two image datasets, it is possible to compare the hashtables to detect duplicates using the following command:
```
python compare_hashes.py <needles_hashtable> <haystack_hashtable> <output_filename>
```
The above command results in a `.json` file containing all instances of duplicates in the haystack set for each image in the needles set.

## Visualise Duplicates
To inspect and visualise these duplicates between the needles and haystack sets, run:

```
python inspect_hashes.py
python json_to_html.py
```
These commands would generate a HTML file that can be opened in any standard web browser. To view the HTML file:

1. Download the CrowdAI dataset train split images from [here](https://www.aicrowd.com/challenges/mapping-challenge/dataset_files).
2. Place the train images in the same folder as the HTML file in the following directory structure: `./data/train/images/<place_images_here>`.
    ```
    └───data
        └───train
            └───images
                └───<place_images_here.>
    ```

3. Open the HTML file in a standard web browser (e.g., Google Chrome).

<!-- ## Dataset -->

<!-- Download link coming soon... -->
<!-- Download the deduplicated and corrected subset of the CrowdAI dataset [here](). -->

## Citation
If you find our work useful in your research, please consider citing:
```
@misc{adimoolam2026deduplication,
      title={Data Leakage Detection and De-duplication in Large Scale Geospatial Image Datasets}, 
      author={Yeshwanth Kumar Adimoolam and Charalambos Poullis and Melinos Averkiou},
      year={2026},
      eprint={2304.02296},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2304.02296}, 
}
```

## Acknowledgement
This repository benefits from
- [ImageHash](https://github.com/JohannesBuchner/imagehash)
- [https://www.hackerfactor.com/blog/index.php?/archives/432-Looks-Like-It.html](https://www.hackerfactor.com/blog/index.php?/archives/432-Looks-Like-It.html)
<!-- - [hawp](https://github.com/cherubicXN/hawp) -->
<!-- - [hawp](https://github.com/cherubicXN/hawp) -->
<!-- - [hawp](https://github.com/cherubicXN/hawp) -->
<!-- - [hawp](https://github.com/cherubicXN/hawp) -->
