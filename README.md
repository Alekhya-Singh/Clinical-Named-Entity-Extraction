# Clinical-Named-Entity-Extraction-using-Conditional-Random-Fields

**Clinical Named-Entity Extraction** works on the basis of information extraction from clinical notes. The system is fed with clinical reports as an unstructured or unannotated form of a text and it has to produce an annotated form (structured form) of text by identifying and extracting entities that correspond to patient’s medical problems, tests,and treatments.

**CRF** based model performs clinical entity extraction from discharge summaries using both domain knowledge such as UMLS Metathesaurus (which is a large biomedical dictionary that contains medical terms, billing codes or drugs name) as well as linguistic features like wordshapes and ngrams.

## Process:
The data provided by 2010 i2b2 Shared Task Challenge are used for training and testing the system and preprocessed by removing the overlapped entities from concept files,Tokenizing. The tokens are converted into lowercase and then stem to their base or root form using Lancaster Stemmer and Porter Stemmer of ‘nltk’. Stemmed tokens are assigned with Part-Of-Speech (POS) tags using “nltk pos_tagger” of the general domain.For sequence labeling, the model has used BOI notation to represent a chunk (a group of tokens).

#### Feature Extraction
Features such as word unigram, last-2 characters, word shape, part-of-speech, regexes of units, length, umls-cui, umls-rel, umls-abr, prev3-unigrams, and next3-unigrams are extracted for every single token.

The tokenized words are converted into vector representation of words as a process of word embedding using DictVectorizer.

These features are then passed through the wrapper known as CRFsuites which is a fast implementation of Conditional Random Fields (CRFs) for labeling sequential data.

The performance of the system presented in this paper was evaluated using the standard measures of precision (fraction of extracted named
entities that are correct), recall (fraction of named entities extracted out of all the gold-standard named entities) and F-measure (harmonic mean of precision and recall).These evaluation metrics depends on FN (False Negative), FP(False Positive) and TP(True Positive).

### Command line flags let you specify two different sequence classification algorithms:
  1. CRF (default) - with linguistic and domain-specific features
  2. LSTM
  
## Sample data:
 
Cannot provide i2b2 data, there is a sample to demonstrate how the data is formatted (not actual data from i2b2, though).

data/examples/ex_doc.txt
This is a text file. Discharge summaries are written out in plaintext, just like this. It is paired with a concept file, which has its annotations.

data/examples/ex_doc.con
This is a concept file. It provides annotations for the concepts (problems, treatments, and tests) of the text file. The format is as follows - each instance of a concept has one line. The line shows the text span, the line number, token numbers of the span (delimited by white space), and the label of the concept.
