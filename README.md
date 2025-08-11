Executive Summary: Accentr: Building an Accent Classifier
Group Members: Anusha Pai Asnodkar & Jack Neustadt

Introduction:

Our initial project pitch was: “Do you want to know what you would sound like as a Brit?  Are you an actor trying to land a  role, but can’t quite get the accent down?  Are you a dialect coach?  Do you want your AI  assistant to sound more like a local?  Look no further than Accentr (final name TBD).  Our project will be a CycleGAN that transforms audio of someone speaking (English) into a  particular accent.” Due to time constraints, we limited our project to a simpler goal: an accent classifier.  The classifier would take as an input audio clip of accented speech and try to predict said accent.  

Dataset (Acquisition, Cleaning, and Preprocessing):

We acquired English audio files web scraped from the Speech Accent Archive, and a corresponding table of metadata (age in years, sex, country, English learning method, English residence duration in years, and URL to audio). This data set has 661 audio samples, from a variety of countries.

We also acquired English audio files from the Mozilla Common Voice Archive (version 2) and its corresponding metadata.  These consist of ~65k audio files of accented speech along with a transcription of the spoken text.  We did not make use of the transcriptions.  These audio clips are shorter and of lower quality than those of the Speech Accent Archive, but there are much more of them (65000 vs 661).

We transformed our audio data in 2D Mel spectrograms so that we could use convolutional neural networks to match potential features in the spectrograms to the accent classifications.  We had hoped that the success of convolutional neural networks on image classification problems would translate well into our analysis of accent classification, but unfortunately, we were not very successful in creating a working model.

Model Selection and Results:

We tried a variety of model architectures, but the basic building blocks are based on the ResNet blocks (2D convolutions, 2D batch normalizations, a ReLU activation function, and 2D max-pooling).  The 2D model is then flattened and transformed through linear mapping functions to get the final accent classifications.

We found that our models dramatically underperformed compared to a pre-trained model.  Whereas the pre-trained model had accuracies of 79% and 95% on the Speech Accent Archive and Common Voice Archive datasets, respectively, our models only achieved 73.1% and 25% accuracy on the respective test sets.  Clearly, something is wrong with our model architecture or pre-processing stages, and so we need to do more to achieve our goals.

Future Steps and Potential Improvements:

The obvious next steps are to improve our models by learning more about and exploring convolutional neural networks.  Based on our models’ low accuracy, there are very likely problems with our convolution kernels, and so improving our understanding of the details of our convolutional networks is key to improving our modeling. 

Additionally, many accent classification methods in academic literature leverage audio embeddings to improve the accuracy of accent classification. Our initial attempts to train on Wav2Vec2 embeddings were not fruitful, but warrant further investigation.

Our project was initially pitched as creating a CycleGAN to transform audio clips of one accent to another, but we had to pare down the project to just an accent classification scheme due to time constraints.  We would like to implement this in the future, which would mean shifting focus to the generator and transformer aspects of a CycleGAN, in addition to improving our classification scheme.
