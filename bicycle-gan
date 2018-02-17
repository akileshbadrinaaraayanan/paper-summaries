# Towards Multimodal Image-to-Image Translation
UC Berkeley and Adobe Research, NIPS 2017.

## Introduction

* Existing image to image translation works produce only single output. 

* This paper models a distribution of possible outputs in a conditional generative modeling setting.

* A learnt low-dimensional latent code is used in addition to input image to generate possible outputs.

* Bijective mapping between the latent encoding and output modes.

* Objective remains to produce realistic and diverse samples while remaining close to the input.

## Methods explored

### Pix2Pix + noise 

* Traditional pix2pix model in which randomly drawn noise z is added to generator in order to induce stochasticity.

* Used as a baseline. 

### cVAE-GAN 

* The ground truth image B is first encoded to get a latent representation Q(z|B) and the generator uses both the input image A
and Q to generate image B<sup>^</sup>.

* Discriminator loss and L1 loss between B and B<sup>^</sup>

* Similar to a VAE, KL divergence between Q and N (0, I) is minimized.

### cLR-GAN

* Similar to the baseline, in addition to the input image A, noise vector N(z) is used by the generator to generate B<sup>^</sup>.

* However, the generated image is passed through an encoder to get a latent representation z and L1 loss between this z and N(z) is minimized.

* In addition, there is a discriminator loss on B<sup>^</sup>
