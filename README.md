# Feed-Forward vs LSTM vs Transformer on Sequential data (Time Series)

RNN are commonly used to analyze sequential data. Analyzing this type of data
requires consideration of the order of elements. To that extent, RNN have the ability
to memorize small chunks of data and use it to predict the next item in line or to
classify time series signals such as electrocardiograms in the medical field. Not
only that, but this memory also makes this kind of network suitable for the analysis
of language (NLP), in which the analysis of sequences provides information about
semantic and context. LSTM are among the most used of this type, but are prone to
problems such as vanishing gradients, slow training and they struggle with long
sequences. Transformers bring the concept of “Attention” to prevent this kind of
problem by focusing on the relevant part. We will see the efficiency of this mechanism

_This project is a part of a bigger project, which includes the comparison of these three types of neural networks on Sentiment analysis as well (full report can be found under the doc directory)_

### Goal

The goal is to predict the hourly temperature, for one or more time period, using
several neural networks

## Data

The data used for this experiment is the Jena climate dataset, from the Max Planck
Institute for Biogeochemistry

## Details

To fairly compare the different models, they have approximately the same number of
trainable weights.

The last Dense layer takes n units, where n is the number of
target values. Here, we can see the prediction is 1 hour ahead. The models are the
same for multi outputs, solely the number of units of the last layer changes.

The Adam optimizer is used for the three models, with default parameters.

The ReLu activation function is used for each layer, except the output layer and the
LSTM layers, which use the default activation function (tanh)

### Transformer

A ”classic” Transformer, as defined in the paper ”Attention is all you need”, is
a sequence to sequence model, which means the encoder takes the input and creates latent variables.

The decoder takes the target, shifted by n steps as input, and the
latent variables from the encoder as context. The decoder learns to predict the
target, based on the target shifted by n and the output (state) of the encoder.

The implemented Transformer here, is not a sequence to sequence model. The
encoder is the same, however the decoder takes the output of the encoder as input,
and the input of the encoder as context.

## References

-   TensorFlow time series: https://www.tensorflow.org/tutorials/structured_data/time_series#setup

-   Transformers: https://www.tensorflow.org/text/tutorials/transformer
