# C++ framework for Face Matching v2.0
This package contains codes for extracting features from normalized images and computing matching scores from lists of gallery and probe images.


## Requirement
1. CUDA 8.0
2. CUDNN 6.0
3. Tensorflow (included in the 3rdparty folder)
4. Mxnet 1.0 (included in the 3rdparty folder)
5. OpenCV3.4.0


## Installation/Compilation
```
cd sample_codes/FaceMatcher_main
make clean; make
```

## Usage
* Step 1: Matching gallery and probe, run the following: `./run_matching.sh <gallery_list_file> <probe_list_file> <output_score_file>`

```
cd bin/facematcher
./run_matching.sh ../../sample_images/small_test/list_gallery.txt ../../sample_images/small_test/list_probe.txt ../../results/score_mat.txt
```

* Step 2: Compute accuracy from score matrix, run the following: `./run_get_accuracy_all_threshold.sh <gallery_list_file> <probe_list_file> <score_file> <output_accuracy_file>`

```
./run_get_accuracy_all_threshold.sh ../../sample_images/small_test/list_gallery.txt ../../sample_images/small_test/list_probe.txt ../../results/score_mat.txt ../../results/acc_all.txt
```
NOTE: These examples are for small testing set, all the probe images are from hard error cases we received previously
