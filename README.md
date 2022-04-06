# I.	Introduction
Autoencoders can shrink the inputs down into just a few nodes in the middle of the hidden layers, then proceed to expand the information back to its original size in an effort to recreate the input. I used an autoencoder to reduce the amount of noise in an image. Since the autoencoder can only remember a limited amount of information, the autoencoder is trained to only remember the most important information. This lets the model encode the image without the noise so when it expands, it is left with a noise-reduced image. My goal was to create a model that reduced as much noise as possible in the fewest number of nodes in the middle hidden layer.

# II.	Model
To start I found a TensorFlow tutorial for noise reduction autoencoders. I switched the dataset from a fashion dataset to a number dataset. Using the model architecture from the tutorial yielded only black screens as its outputs.
 
![first output](/assets/not_working.png "Title")
 
After changing the convolutional layers to dense layers, I got actual numbers to appear, however, there was still noise leftover in the image.
 
![second output](/repository/assets/better.png "Title")
  
The biggest thing that helped was adding additional hidden layers that progressively got smaller for the encoding phase. The fewest number of nodes in the encoding section was 8 nodes. Anything smaller than that did not retain enough information for noise reduction with the dense network. Even when adding more layers, anything smaller than 8 was too little for the model to work with.

## End result
As I got a final model working well, increased the noise as high as I could. The final model after being trained for 50 epochs yielded this result.
 
![final output](/repository/assets/50_epochs.png "Title")
  
There is a lot of noise in these images, but we can see what the number is supposed to look like. These outputs are very close to the original image. I could even change the noise to the point where not even a human could recognize what the number was supposed to be. But the model was able to predict most of the numbers correctly.
 
![extra noise output](/repository/assets/extra_noise.png "Title")

# Conclusion 
The model turned out very well. I was only basing its success based on human evaluation, checking visually to see if the numbers in the output were what they were supposed to be. A more quantifiable metric could be to feed the outputs into a classification neural network. This would allow me to see how many of the outputs were good enough to be recognized by a neural network. This may come in future work.
