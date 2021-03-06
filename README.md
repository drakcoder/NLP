# NLP
A simple NLP model using the IMDB Dataset:

## What is NLP?
Natural Language Processing, or NLP for short, is defined as the manipulation of the natural language ,that is generally used by people, by a software.

## The current application:
The current application revolves around the paired data given IMDB.

Source :https://www.kaggle.com/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews

After importing and studying the dataset, we can notice that the positive and negative reviews are distributed equally ,i.e, 25000 each.

![graph](https://user-images.githubusercontent.com/67307833/112130650-b4feb200-8bee-11eb-9859-2f2a1596c66f.png)

* **Pre-processing:**

The data given consists of HTML tags, we need to remove them using re library from python. After this we replace the values of 'Positive' with 1 and 'Negative' with 0.

* **Tokenization:**

Tokenization is essentially splitting a phrase,sentence,paragraph,or an entire text document into smaller units, such as induvidual words or terms, each of these smaller units are called Tokens

* **Embedder:**
Here we will be using a pre-trained embedder called GloVe developed by Stanford University.

  source:https://nlp.stanford.edu/projects/glove/
A word embedding is a learned representation for text where words that have the same meaning have similar representation.

* **Model:**
The first model will be having an Embedding layer in the beginning followed by a flattening layer which sets all the nodes into a single layer followed by a layer of two nodes which will determine the truth value of the input.

![Capture](https://user-images.githubusercontent.com/67307833/112135525-e0d06680-8bf3-11eb-84fc-886acc1303d8.JPG)

After the first training we can see the training accuracy to be 81% and the validation accuracy to be 73%, here we can notice a decrease in accuracy by roughly 8%.
This generally refers that the model is over-fitting the training set.

* **LSTM**

Now we will be adding an LSTM layer to our previous model.

![image](https://user-images.githubusercontent.com/67307833/112137114-de6f0c00-8bf5-11eb-8dbe-80add7092030.png)

Now after training the model we can see the training accuracy to be 85% and the validation accuracy to 83% which is a difference of 2%. This means that the model is still slightly overfitting the training dataset.

## Why does LSTM work better in this case?

LSTM uses a bi-directional wrapper which propagates inputs forward and backward throughout the LSTM layer and then concatenates the outputs, this helps the LSTM learn long term dependencies, unlike regular RNN.

* **Long-term Dependencies**:
  Long-term Dependencies problems are the problems where the desired outputs depend on the inputs presented at times far in the past.
  
  Let us consider a sentence "Fish live in the *water*". 
  
  Its pretty easy to predict the answer as sky from the previous words. 
  
  But when we consider a sentence like "I grew up in France, I speak fluent *French*".
  
  Here it may recognize that the word in italics should be a language but the model may find it hard to bridge the gap between the first sentence and the last word to actually predict the word French and not just any language.
  
In theory, regular RNN's are supposed to be capable of handling such issues, but in practice they perform poorly when there are long-term dependency problems.
