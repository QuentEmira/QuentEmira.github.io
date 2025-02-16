The key find here is that smaller models trained to mimic the outputs of larger models tend to perform as well as larger models trained on the training dataset.

The training here occurs with soft targets and hard targets. Soft targets provide more information than hard targets, making it a better learning source for smaller models.

The soft targets are calculated with a temperature of 1, so as to make sure that smaller model don't overfit to specific result (this ends up being similar to training on hard targets)

Distilling of knowledge from larger models to smaller models is possible. This, though, has to be reasonable.

It is achieved with a mixture of soft targets and hard targets, with an additional bias to push towards the correct label. A high temperature is used to produce said soft targets. The temperature used for producing the soft target must then be used for the training of the smaller model. Depending on the model size, the temperature will have to change.

The were able to train a smaller model to detect 3 from the MNIST dataset, when 3 was not a part of the training set at all. What they did was train on the other numbers, and then give the model information about the probabilities of all classes. So, it learnt about number 3, without ever having seen it. This is incredible!!

Obviously, the models they worked with were small, generally 2 layer models with 300 nodes. They also did the same experiment with speech data, trying to learn from an ensemble model. This worked a bit, but not well.

They also had an image model, and used its soft targets to train and mixture of specialist to detect and differentiate between confusing classes. This was successful.

This is very cool. How far can we push this? Information, soft information, not just hard information, is just very intriguing.

Source: https://arxiv.org/pdf/1503.02531