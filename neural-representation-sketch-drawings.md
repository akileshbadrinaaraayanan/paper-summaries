# A Neural Representation of Sketch Drawings.

## Introduction

* This paper proposes recurrent neural network based generative model that is capable of producing sketches of common objects in vector format. 

* It is one of the few papers that attempt to explore generative model for vector images as against the several different methods for modelling pixel images.

* The authors provide a framework for both unconditional and conditional generation of vector images composed of a sequence of lines.

## Dataset

* Obtained from [QuickDraw](https://quickdraw.withgoogle.com/) where in each class consists of 70K training samples, 2.5K validation samples and 2.5K test samples.

* A sketch is a list of points, and each point is a vector consisting of 5 elements: (∆x, ∆y, p1, p2, p3). 

* The first two elements are the offset distance in the x and y directions of the pen from the previous point. 

* The last 3 elements represents a binary one-hot vector of 3 possible states. 

* The first pen state, p1, indicates that the pen is currently touching the paper, and that a line will be drawn connecting the next point with the current point.

* The second pen state, p2, indicates that the pen will be lifted from the paper after the current point, and that no line will be drawn next.

* The final pen state, p3, indicates that the drawing has ended, and subsequent points, including the current point, will not be rendered.

## Model

* It’s a Seq2Seq Variational Autoencoder (VAE) in which the encoder is a bidirectional RNN. 

* The final hidden state of the encoder is projected into two vectors µ and σ using a FC layer. Along with this, a Gaussian noise N (0, I) is added to obtain the final latent vector that is conditioned on the input sketch. z = µ + σ  N (0, I)

* Decoder is an [autoregressive RNN](https://arxiv.org/pdf/1310.8499.pdf) that samples output sketches conditional on a given latent vector z. 

* At each step i of the decoder RNN, we feed the previous point, S<sub>i−1</sub> and the latent vector z in as a concatenated input x<sub>i</sub> , where S<sub>0</sub> is defined as (0, 0, 1, 0, 0). The output at each time step are the parameters for a probability distribution of the next data point S<sub>i</sub>.

