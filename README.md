# TextProcessingPackage

[![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg)](https://github.com/preethampaul/TextProcessingPAckage/blob/master/LICENSE) </br>
Most of the text based problems require a lot of pre processing. </br>
The package is an attempt to reduce the time of preprocessing so that the user can focus on developing solutions to problems

The package contains the following techniques:
* Removal of unenecessary punctuations
* Removal of html/xml tags
* Removal of stop words (optional)
* Removal of digits (optional)
* Expanding short forms (aren't -> are not)
* Lemmatization (optional)
* Creation of word clouds with combinaton of n words (n-grams)
* Addition of words to stopwords list

Currently in work
* Topic Modeling using LDA and Non Negative Matrix factorizations using both sklearn and gensim

## Installation
```
pip install TextPreProc
```

## Code Snippets
#### Preprocessing of text with lemmatization

```
from DataAndProcessing import text_cleaner
dataframe = text_cleaner(data, column_name='column_with_textdata', remove_stopwords=True, listOfStopWords = ['no','none'], append_stopwords=True, remove_digits=False, do_lemmatization=True)
```

#### Create Word Cloud

```
from DataAndProcessing import create_word_cloud
create_word_cloud(dataframe, column_name='column_with_textdata', n=1, save_fig=False)
```
where n = 1,2,3 means unigram, bigram and trigram respectively

#### Append words to the standard NLTK stopwords list
```
from DataAndProcessing import add_stopwords
add_stopwords(listOfStopWords, is_new = False)
```
### Topic Modelling
```
from TopicModelling import Topic_Modelling
tm = Topic_Modelling(dataframe, 
                     column_name='response_text', 
                     vectorizer_type = 'bow', 
                     topic_modelling_type = 'lda', 
                     vectorizer_parameters = {'strip_accents': 'unicode'}, 
                     topic_model_parameters = {'init': 'random'}, 
                     num_topics = 10, 
                     show_visualization = True, 
                     save_fig = False, 
                     fig_title = 'Topics in the data', 
                     is_sklearn = True)
tm.fit_transform()
```
Output
* None (Currently the model does not produce any output)
Parameters and values
* **vectorzier_type**: 'bow' or 'tfidf' (Default: 'bow')
* **topic_modelling_type**: 'lda' or 'nmf' (Default: 'lda')
* **vectorizer_parameters**: dictionary of parameters for sklearn CountVectorizer or TFIDFVectorizer (Default: Default model parameters)
* **topic_model_parameters**: dictionary of parameters for sklearn NMF or LatentDirichletAllocation (Default: Default model parameters)
* **num_topics**: number of topics (Default: 10)
* **show_visualization**: True or False (Default: True)
* **save_fig**: True or False (Default: False)
* **fig_title**: Title for the plot (Default: 'Topics in the data')
* **is_sklearn**: True or False (Currently the module supports on Sklearn modules) 

### Return the trained vectorizer and topic models
```
tm.return_models(return_vectorizer = True, return_topic_model = True)
```
Output
* Returns dictionary of models 

Parameters and values
* **return_vectorizer** = True or False (Default: False)
* **return_topic_model** = True or False (Default: True)
