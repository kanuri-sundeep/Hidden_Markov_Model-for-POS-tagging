# Hidden_Markov_Model-for-POS-tagging

We will apply vertibi algorithm from scratch to predict the POS tags of a sentence. 

We use two tagged data sets collected from the **Wall Street Journal (WSJ)**. 

[Here](http://relearn.be/2015/training-common-sense/sources/software/pattern-2.6-critical-fork/docs/html/mbsp-tags.html) is an example 'tag-set' or Part of Speech designation describing the two or three letter tag and their meaning. 
- One data set (**WSJ-2_21.pos**) will be used for **training**.
- The other (**WSJ-24.pos**) for **testing**. 
- The tagged training data has been preprocessed to form a vocabulary (**hmm_vocab.txt**). 
- The words in the vocabulary are words from the training set that were used two or more times. 
- The vocabulary is augmented with a set of 'unknown word tokens', described below. 

The training set will be used to create the emission, transmission and tag counts. 

The test set (WSJ-24.pos) is read in to create `y`. 
- This contains both the test text and the true tag. 
- The test set has also been preprocessed to remove the tags to form **test_words.txt**. 
- This is read in and further processed to identify the end of sentences and handle words not in the vocabulary using functions provided in **utils_pos.py**. 
- This forms the list `prep`, the preprocessed text used to test our  POS taggers.

A POS tagger will necessarily encounter words that are not in its datasets. 
- To improve accuracy, these words are further analyzed during preprocessing to extract available hints as to their appropriate tag. 
- For example, the suffix 'ize' is a hint that the word is a verb, as in 'final-ize' or 'character-ize'. 
- A set of unknown-tokens, such as '--unk-verb--' or '--unk-noun--' will replace the unknown words in both the training and test corpus and will appear in the emission, transmission and tag data structures.
