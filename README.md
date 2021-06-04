# intent-of-users-of-chatbot-AraBERT-
The problem data is given by Dexwand; the data describes the intent of usersof a chatbot in an application related to COVID-19.  Your goal is to predict theintent of the users given the text they wrote.  The challenge is how limited thedata is; this happens a lot in industry especially in Arabic NLP.
# Contents:

1- Arabic NLP Approaches and Difficulties.
2- The Approaches 
3- Intro to Attention, Transformers and Arabert.
4- Our code and results.
5- Inference Time and Memory Reduction.
6- Final Thoughts and Improvements with Deployment.

# 1- Arabic NLP Approaches and Difficulties:

- The main challenge is that Arabic has complex morphology and various dialects. 

- The advancements to English NLP are not easily transferred to the development of Arabic NLP resources.

# 2- The Approaches:

- AraBERT Model and Transformers.  using a pre-trained AraBERT due to lack of data.

# 3- Intro to Attention, Transformers and Arabert:

LSTM/GRU Attention mechanisms are a way of alleviating the vanishing gradient problem by focusing relevant parts of an input sequence and  knowledge of past positional context

AraBERT is a pre-trained model using BERT and has 110 million parameters and tokenization resulted in a vocabulary size of 64K words derived from various sources

BERT stands for Bidirectional Encoder Representations from Transformers. It is designed to pre-train representations from unlabeled text by jointly conditioning on left and right context

# 4-  code and results:

1) Preprocessing the dataset.

2) Building the model and tuning the hyperparameters.

3) Predicting the test dataset.

   Building & Tuning the model:
-  Hugging Face transformers trainer were used due to its simplicity and ease of implementation. 
- We used mostly the default AraBERT parameters. 
- We increased the learning rate to avoid overfitting, changed the  batch size in both train and eval into 32 and increased the number of epochs to 25.

# 5-  Inference Time and Memory Reduction

In our try To reduce inference time we have mainly used two functions. 

To not sacrifice much accuracy in prediction we used just these built in pytorch functions:

model.eval(): To notify all your layers that you are in eval mode, that way, batchnorm or dropout layers will work in eval mode.

torch.set_grad_enabled(False): To impact the autograd engine and deactivate it to reduce memory usage and speed up computations.

We could have used Quantization, Pruning  and  converting the weights to  fp16.

# 6- Final Thoughts and Improvements with Deployment:

This model is just a step in the way we hope to complete and make use of in production and practical life as follows:
Deploying the model in a chatbot using Google cloud, IBM Watson.

