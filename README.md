# PyTorch Natural Language Inference [In Progress]

This repo contains tutorials covering how to do natural language inference (NLI) using [PyTorch](https://github.com/pytorch/pytorch) 1.2 and [TorchText](https://github.com/pytorch/text) 0.4 using Python 3.7.

These tutorials will cover getting started with NLIby introducing a simple network with no recurrent layers. The second covers how to use TorchText's `NestedField` in order to get the characters for each word which will be used to construct a sentence encoder for the premise and hypothesis which processes not only the words in each sentence, but also the individual characters.

**If you find any mistakes or disagree with any of the explanations, please do not hesitate to [submit an issue](https://github.com/bentrevett/pytorch-nli/issues/new). I welcome any feedback, positive or negative!**

## Getting Started

To install PyTorch, see installation instructions on the [PyTorch website](pytorch.org).

To install TorchText:

``` bash
pip install torchtext
```

We'll also make use of spaCy to tokenize our data. To install spaCy, follow the instructions [here](https://spacy.io/usage/) making sure to install the English and German model with:

``` bash
python -m spacy download en
```

## Tutorials

* 1 - [Simple NLI Model](https://github.com/bentrevett/pytorch-nli/blob/master/1%20-%20Simple%20NLI%20Model.ipynb)

    This tutorial covers how to implement a basic NLI model. This model embeds the tokens in each sentence into 300-dimensional GloVe embeddings (which are frozen) and then creates an embedding for the entire sentence by simply summing the tokens of all embeddings within the sentence. These are then fed into 3 linear layers which output a prediction. Although this model is simple, it achieves comparable performance to using RNNs over each sentence. We also show to to implement a simple model with RNNs.

* 2 - [NestedField, Sentence Encoders and Inference](https://github.com/bentrevett/pytorch-nli/blob/master/2%20-%20NestedField%2C%20Sentence%20Encoders%20and%20Inference.ipynb)

    Now we have a basic NLI model working we can improve on it. In this tutorial we introduce the `NestedField` - a TorchText field that processes another field. The `NestedField` provides an easy way to get both the words and characters for the sequences we want to tag. We will also create a sentence encoder that will take in boths the words and characters within a sentence - processing the words with a RNN and the characters with a CNN - and produces a single sentence embedding vector for both the premise and the hypothesis - which are fed into the rest of our model. Finally, we show how to use the model for inference, allowing us to perform natural language inference on any sentence.

## References

Here are some things I looked at while making these tutorials. Some of it may be out of date.

- https://github.com/Smerity/keras_snli