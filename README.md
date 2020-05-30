# Modified Viterbi
Modified Viterbi Algorithm that solves POS tagging of unknown words

Implementing an HMM-based POS tagger using the Viterbi algorithm with the Penn Treebank training corpus.
The vanilla Viterbi algorithm resulted in 91% accuracy.
The approximately 9% loss of accuracy was majorly due to the fact that when the algorithm encountered an unknown word
(i.e. not present in the training set, such as 'Twitter'), it assigned an incorrect tag arbitrarily.
This is because, for unknown words, the emission probabilities for all candidate tags are 0, 
so the algorithm arbitrarily chooses (the first) tag.

# Dataset used:
Treebank dataset of NLTK with the 'universal' tagset

# Solution
To solve this problem of randomly tagging the unknown words in the test set, two approaches have been taken

1. Tagging the unknown words with the most occuring tag in the training set, in this case which is a 'NOUN'.
The tag 'NOUN' occurs for 28.68% in the set.
Also, since 'NOUN' is the most occuring generally in an English Corpus, it is a fair choice to make to tag 
unknown words rather than tagging randomly.
Result: By this simple technique, the accuracy went up to 93.96%

2. Tagging the unknown words using RegEx
There are instances of the unknown words that end with 'ing' or 'ed' which are in most cases Verbs.
There are also instances of numbers that appear in the dataset, which should be tagged as 'NUM'.
So, by identifying such patterns for the incorrectly tagged words and using it for a RegExpTagger,the results obtained were
promising.
Result: The final accuracy obtained with this technique 96.16%

