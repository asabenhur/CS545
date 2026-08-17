# CS 545: Machine Learning — course notebooks

[![Text: CC BY-SA 4.0](https://img.shields.io/badge/text-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Code: MIT](https://img.shields.io/badge/code-MIT-yellow.svg)](https://opensource.org/license/mit)

Jupyter notebooks for CS 545 at Colorado State University, taught by
[Asa Ben-Hur](https://www.cs.colostate.edu/~asa/). 

## Modules

This course introduces modern deep learning techniques, and takes a
"transformers first" approach instead of teaching the material
according to its historic development.

| Folder       | Topics                                                                 |
|--------------|------------------------------------------------------------------------|
| `00_prerequisites/` | A Python primer, NumPy and PyTorch, Matplotlib        |
| `01_linear/`    | Linear regression, generalization and weight decay; logistic and softmax regression |
| `02_mlp/`       | Multilayer perceptrons and backpropagation                            |
| `03_recurrent/` | Recurrent networks and LSTMs, applications in sentiment analysis |
| `04_attention/` | The building blocks of transformers:  Attention, multi-head attention, positional encoding, dropout and residual connections; BERT |
| `05_llm/`       | Language modeling and perplexity, training a generative model from scratch, pretrained LLMs, fine-tuning with LoRA |
| `06_cnn/`       | The components of convolutional networks (padding and stride, channels, pooling); the LeNet network             |
| `07_cnn_modern/`| Modern convolutional networks:  AlexNet, VGG and blocks, batch and layer normalization, ResNet, fine-tuning, CNNs for text |
| `08_training/`  | Training deep learning models:  Gradient descent and SGD, minibatches and momentum, adaptive methods, learning-rate schedules |


## Setup

All the libraries needed to run the notebooks are listed in `environment.yml` at the root of
this repository.  We suggest using conda to fully automate the install
process.  That way, conda is the only package you will need to install by hand.


**1. Install conda.** If you do not already have it, we suggest installing
[Miniforge](https://github.com/conda-forge/miniforge), choosing the installer
that matches your operating system and processor (Apple Silicon and Intel
Macs take different ones). Miniforge is a minimal conda that draws packages
from `conda-forge` by default, which is the channel this course uses. An
existing Anaconda or Miniconda installation works too.

**2. Create the environment.** From the root of this repository:

```bash
conda env create -f environment.yml
```

This installs Python, PyTorch, Jupyter and everything else in one step. Expect
it to take a few minutes and a couple of gigabytes of disk (This step
assumes you have downloaded the repository.)

**3. Activate it.**

```bash
conda activate 545
```

Note that every time you open a new terminal window, you will need to
activate this environment.  If a notebook reports a missing package, check this
first.

**4. Start Jupyter** from the directory of the module you want to work
in e.g.,

```bash
cd 04_attention
jupyter lab
```

or open a given notebook with `jupyter lab module04_01_sentiment_transformer.ipynb`.
Run notebooks from inside their own module directory: they look for datasets
at `../data`, and will download them to the wrong place otherwise.

### Maintaining the environment

To update an existing environment after this file changes, rather than
creating it from scratch:

```bash
conda env update -f environment.yml --prune
```

To delete it and start over: `conda env remove -n 545`.

### GPUs

The environment installs a CPU build of PyTorch, which also provides
Apple-Silicon GPU support through MPS. If you
have an NVIDIA GPU, activate the environment and then install a CUDA build
following the selector at <https://pytorch.org>. The notebooks select the
device automatically and run on a laptop CPU either way; a GPU only makes the
longer training cells faster.

### Data

Datasets are downloaded on first use into the `data/` directory at the root of
this repository, shared by every module so that nothing is fetched twice.


## Attribution and license

These notebooks are based on the PyTorch version of
[Dive into Deep Learning](https://d2l.ai) by Aston Zhang, Zachary C. Lipton,
Mu Li and Alexander J. Smola, used under
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) and heavily
modified by [Asa Ben-Hur](https://www.cs.colostate.edu/~asa/) with
[Claude](https://claude.com) AI. Some figures are reproduced from the
original. The material has been substantially rewritten, reorganized and
extended; errors introduced along the way are ours, not the original authors'.

The prose — markdown cells, figures and other written material — is released
under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/); see
[LICENSE](LICENSE). ShareAlike applies: anything you build on this text must
carry the same license.

The code — the contents of code cells, and accompanying scripts — is released
under the [MIT license](https://opensource.org/license/mit); see
[LICENSE-CODE](LICENSE-CODE). Portions derive from d2l's sample code, which
its authors make available under a
[modified MIT license](https://github.com/d2l-ai/d2l-en/blob/master/LICENSE-SAMPLECODE).
