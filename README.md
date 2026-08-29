# NumPy Neural Networks on MNIST

A from-scratch NumPy implementation of multilayer perceptrons and convolutional
neural networks for MNIST, accompanied by a systematic model-configuration
study and a small Flask training interface.

## Highlights

- Implements dense, convolution, pooling, activation, dropout, loss, and SGD
  components without a deep-learning framework.
- Evaluates MLP/CNN depth, activation, optimiser, loss, pooling, dropout, and
  early-stopping combinations.
- Screened 576 configurations on a reduced training set, then retrained 29
  finalists on the full dataset.
- Best recorded full-data test accuracy: **99.26%** for a large CNN with
  Leaky ReLU, SGD, cross-entropy, max pooling, dropout, and early stopping.

## Files

- `function.py` - reusable NumPy layers, models, data loading, training, and
  evaluation utilities.
- `模型配置遍历脚本.py` - configuration sweep.
- `模型配置选择应用脚本.py` - finalist selection and full-data evaluation.
- `app.py` and `templates/index.html` - browser interface for interactive MLP
  training.
- `results_summary.md` - reduced-data screening results.
- `full_training_summary.md` - full-data finalist results.
- `v*.py` and `pro_v*.py` - retained experiment history showing the model's
  development; new users should start with `function.py` and the two named
  runner scripts above.

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Download the four standard MNIST IDX gzip files into `dataset/MNIST`, or set
`MNIST_DATA_DIR` to a directory containing them.

## Run the interactive demo

```bash
python app.py
```

Then open `http://127.0.0.1:5000`.

## Reproduce the configuration study

```bash
python 模型配置遍历脚本.py --help
python 模型配置选择应用脚本.py --help
```

The exhaustive search is compute-intensive. The committed Markdown summaries
provide the archived results without requiring a full rerun.

