# Adversarial Training Methods
Adversarial and virtual adversarial training methods for semi-supervised text classification.

Based on the paper:
[Adversarial training methods for semi-supervised text classification, ICLR 2017, Miyato T., Dai A., Goodfellow I.
](https://arxiv.org/abs/1605.07725)
####Without the pre-training phase

## Requirements

Package | Version
:-------: | :-------:
[Python](https://www.python.org/downloads/) | 3.5.4
[Jupyter](http://jupyter.org/install) | 1.0.0
[Tensorflow](https://www.tensorflow.org/versions/r1.5/) | r1.5
[GloVe](https://nlp.stanford.edu/projects/glove/) | 1.2
[NLTK](http://www.nltk.org/install.html) | 3.2.5
[ProgressBar2](https://pypi.python.org/pypi/progressbar2) | 3.34.3
[Matplotlib](https://matplotlib.org/2.1.2/index.html) | 2.1.2
[Argparse](https://pypi.python.org/pypi/argparse/1.1) | 1.1


## Dataset creation

Download the [IMDB](http://ai.stanford.edu/~amaas/data/sentiment/) dataset.

Then we have to do the following steps:
* preprocess both train and unlabeled sequences tokenizing and removing punctuation
* set the vectors length at 256 and remove words appearing in less than 3 reviews in the GloVe training script
* run GloVe training script
* 5% of the training set is used for validation

## Training

Sequences are truncated at 1200 (pyramidal model), 600 and 400 to test the sensitivity of the model to reviews lengths. In particular we cut off or add zero-padding at the initial part of the review.

## Results

Method | Seq. Length | Epochs | Accuracy
:------: | :-----------: | :------: | :--------:
baseline | 400 | 10 | 0.906  
adversarial | 400 | 10 | 0.914  
virtual adv. | 400 | 10 | **0.921**
baseline | 600 | 10 | 0.904  
adversarial | 600 | 10 | 0.912  
pyramidal baseline | 1200 | 10 | 0.910  
pyramidal adversarial | 1200 | 10 | 0.916  
