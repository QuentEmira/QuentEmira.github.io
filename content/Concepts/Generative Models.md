Generative models are models that try to learn the Joint probability space of the dataset its working with.

By learning the joint probability p(X,Y), a generative model can use this to create new data points.

## Why does Joint Probability help in creating new data points?

Joint probability represents how probable every combination of X and Y is. This gives an idea of what combination of factors in X and Y come together in general, and what combination do not.

A simple analogy is about baking cake. If you learn to bake a cake (Y), and the ingredients and the process needed to bake the cake(X), and you do this for a lot of cakes(dataset), you then create your own cake by mixing and matching the ingredients, as you know what ingredient works with what, and what doesn't.

Now, to create new data, as we already have a Joint probability representation, we just need to use that in order to try and estimate what factors would come together.

## What are some examples of Generative Models?
- [[VAE]]
- [[GAN]]
- [[HMM]]
## How is the joint probability space represented?
Different models have different ways of representing the joint probability space.

One way is through [[Latent Space|latent space]].