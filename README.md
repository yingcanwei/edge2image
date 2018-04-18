# edge2image
This project uses a conditional generative adversarial network (cGAN) to learn a mapping from an input image to an output image.

## Setup

### Prerequisites
- Tensorflow 1.4.1

### Recommended
- Linux with Tensorflow (GPU edition + cuDNN will be better)

### Getting Started

```sh
# clone this repo
git clone https://github.com/yingcanwei/edge2image.git
cd edge2image
# download the edges2shoes dataset (generated from http://vision.cs.utexas.edu/projects/finegrained/utzap50k/)
python tools/download-dataset.py edges2shoes
# train the model (this may take more than 48 hours depending on GPU, on CPU you will be waiting for a bit)
python edge2image.py \
  --mode train \
  --output_dir edges2shoes_train \
  --max_epochs 200 \
  --input_dir edges2shoes/train \
  --which_direction AtoB
# test the model
python edge2image.py \
  --mode test \
  --output_dir edges2shoes_test \
  --input_dir edges2shoes/val \
  --checkpoint edges2shoes_train
```

The test run will output an HTML file at `edges2shoes_test/index.html` that shows input/output/target image sets.


