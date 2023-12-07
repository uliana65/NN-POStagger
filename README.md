# NN POS Tagger

POS tagger for German language based on a 1-layer LSTM with the Adam optimizer and Cross Entropy loss function. 

## Training

Follow this [jupyter notebook](https://github.com/uliana65/NN-POStagger/blob/main/NN_postagger.ipynb) to train a model. Make sure data_loader.py is in the same folder as the notebook.

Corpus language: German
Corpus format: CoNLL (here I used [UD_German-GSD](https://universaldependencies.org/treebanks/de_gsd/index.html))
Embeddings: [FastText](https://pytorch.org/text/stable/_modules/torchtext/vocab/vectors.html#FastText) word embeddings pretrained on Wikipedia; on initialization, takes some time to load embeddings then uses the cached ones

## Performance

I experimented with two learning rates (0.01, 0.05) and two hidden layer sizes (300, 150) during training. The plots below show the model's training and development accuracy as well as the loss plotted for each epoch (x-axis). 

![training_performance](https://github.com/uliana65/NN-POStagger/blob/main/figures/training_1.png)
![training_performance](https://github.com/uliana65/NN-POStagger/blob/main/figures/training_3.png)

As evident from the plots above, a smaller learning rate (0.01) seems to converge faster with smaller number of hidden units. After the 10th epoch, 300-units model reaches about 94.3% training accuracy, 89% development accuracy and the loss is slightly above 0.18. While a smaller 150-units model has a better loss at this stage (<0.18). Considering that a higher number of hidden units results in longer a training time and their performance is comparable, a smaller model is more preferable. 
On the other hand, a bigger learning rate (0.05) with 150-units hidden layer appears to overshoot the minima which shows in more distinct fluctuations of the loss and training accuracy after the 5th epoch (plot below). Overall, after full 30 epochs this learning rate leads to a worse performance compared to a smaller one with the same hidden layer size. 

![training_performance](https://github.com/uliana65/NN-POStagger/blob/main/figures/training_4.png)

Further training (>34 epochs) leads to overfitting: the loss drops to 0.12 and the training accuracy rises to 95.5%, while the development accuracy starts declining.

Final model's test accuracy: 89.99%
Test accuracy by part of speech:
| POS | Accuracy | Percentage in training data |
| --- | -------- | --------------------------- |
NOUN|0.88|18.5%
VERB|0.82|7.9%
ADJ|0.85|6.1%
ADV|0.75|7.7%
PROPN|0.9|6.1%
PRON|0.88|5.5%
AUX|0.92|4.1%
ADP|0.98|9.6%
NUM|0.82|1.6%
CCONJ|0.94|2.8%
SCONJ|0.77|1%
DET|0.95|12%
PART|0.82|1.3%
SYM|0.5|0.02%
PUNCT|0.99|14.1%
INTJ|0.0|0.02%
_|0.99|1.6%
X|0.04|0.2%

We can see, that the accuracy is near perfect for POS tags like PUNCT, DET, and ADP, whose set of tokens is rather limited and distributional frequency is high. On the other hand, the most frequent tag NOUN is below 90% accuracy, which indicates the complexity of this core category. Both form (das Leben (NOUN) vs. lebel (VERB), der Dumme (NOUN) vs. dumme (ADJ)) and structure (NOUN can appear after/before any other POS) make this category ambiguous.

## Tagging
[RECIPE FOR LOADING PARAMS AND LINK? TO WEBSITE]
