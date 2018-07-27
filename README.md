# Time-Series-using-keras-R


## Recurrent neural networks

When our data has a sequential structure, it is recurrent neural networks (RNNs) we use to model it.

As of today, among RNNs, the best established architectures are the GRU (Gated Recurrent Unit) and the LSTM (Long Short Term Memory). For today, let’s not zoom in on what makes them special, but on what they have in common with the most stripped-down RNN: the basic recurrence structure.

In contrast to the prototype of a neural network, often called Multilayer Perceptron (MLP), the RNN has a state that is carried on over time.

![RNN](https://blogs.rstudio.com/tensorflow/posts/2018-06-25-sunspots-lstm/images/rnn.png)

At each time, the state is a combination of the current input and the previous hidden state. This is reminiscent of autoregressive models, but with neural networks, there has to be some point where we halt the dependence.

That’s because in order to determine the weights, we keep calculating how our loss changes as the input changes. Now if the input we have to consider, at an arbitrary timestep, ranges back indefinitely - then we will not be able to calculate all those gradients. In practice, then, our hidden state will, at every iteration, be carried forward through a fixed number of steps.

### Libraries needed

```r
# Core Tidyverse
library(tidyverse)
library(glue)
library(forcats)

# Time Series
library(timetk)
library(tidyquant)
library(tibbletime)

# Visualization
library(cowplot)

# Preprocessing
library(recipes)

# Sampling / Accuracy
library(rsample)
library(yardstick) 

# Modeling
library(keras)
library(tfruns)
```
