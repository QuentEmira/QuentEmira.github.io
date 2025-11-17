#ai 
Converting words or tokens into vectors is vector embedding.

An embedding here is a representation of something, specifically chosen so that the model understands it.

In this case, the embedding is in the form of a vector, an array of numbers, representing multidimensionality.

## Why is vector embedding needed?
Models work with number.

Embedding is a way of representing tokens/words in a format for the model to differentiate and operate with.

Vector embedding is an even more specific way, where the embedding takes the form of an n-dimensional vector. The value of n differs based on the embedding model.

## How do words get their corresponding vectors?
Initially, words get a random vector to represent them. This means that each and every word is a point on the vector space. They have a direction, and a scale to them.

After this, as the model (that decides the proper vector embedding) trains on data, it changes the values of these vectors, and at the end of training each word gets its corresponding vector.

## What is the difference between the vector given at random, and the vector given after training?
The interpretation here is that the embedding model encodes semantic understanding about the word, and words similar to it based on the vector.

So, two words that are similar would be closer, whereas two words that are opposites, or unrelated, would be farther.

## How are these words compared?
They are compared using the 'direction' they face, disregarding the scale of the vector. So, two vectors are similar if the angle between them is very small, regardless of how big or small any of those vectors are.

## How does the model learn to put similar words closer?
This is done based on context words. Based on the idea of [[Distributional Hypothesis]].

Based on the words surrounding a particular word, its position is changed.