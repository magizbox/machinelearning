# Natural Language Processing (NLP)

![](https://www.ibm.com/developerworks/mydeveloperworks/blogs/nlp/resource/nlp-shakespeare.jpg)

> Is paris capital of France?
> YES

### Deep Learning

[A Primer on Neural Network Models for Natural Language Processing](http://u.cs.biu.ac.il/~yogo/nnlp.pdf)

### Courses

* CS224n: Natural Language Processing ([website](http://web.stanford.edu/class/cs224n/index.shtml), [video](https://www.youtube.com/watch?v=GZhhA3DBs9o&list=PLgtM85Maly3n2Fp1gJVvqb0bTC39CPn1N))
* [CS224d: Deep Learning for Natural Language Processing](http://cs224d.stanford.edu/)

# POS Tagging

![](https://www.safaribooksonline.com/library/view/natural-language-annotation/9781449332693/figs/web/nlml_0106.png)

A Part-Of-Speech Tagger (POS Tagger) is a piece of software that reads text in some language and assigns parts of speech to each word (and other token), such as noun, verb, adjective, etc., although generally computational applications use more fine-grained POS tags like 'noun-plural'.

## Methods

1. Sequence Classification [^1]

[^1]: [ Sequence Classification, Learning to Classify Text](http://www.nltk.org/book/ch06.html)

# Textual entailment

![](http://image.slidesharecdn.com/acl-tutorial-on-textual-entailment2964/95/acl-tutorial-on-textual-entailment-17-728.jpg?cb=1278312611)

Textual entailment (TE) in natural language processing is a directional relation between text fragments. The relation holds whenever the truth of one text fragment follows from another text. In the TE framework, the entailing and entailed texts are termed text (t) and hypothesis (h), respectively. Textual entailment is not the same as pure logical entailment- it has a more relaxed definition: "t entails h" (t ⇒ h) if, typically, a human reading t would infer that h is most likely true. The relation is directional because even if "t entails h", the reverse "h entails t" is much less certain. [^1]

[^1]: [Textual entailment](https://en.wikipedia.org/wiki/Textual_entailment)

# Language Modeling

Language Models [^1]

* N-Gram
* [Tfidf](http://magizbox.com/?p=3843)
* [word2vec](http://magizbox.com/?p=3083)

[^1]: [Week 2 - Language Modeling](https://class.coursera.org/nlp/lecture)

# N-Gram Model

# Tfidf

tf–idf, short for term frequency–inverse document frequency, is a numerical statistic that is intended to reflect how important a word is to a document in a collection or corpus. It is often used as a weighting factor in information retrieval and text mining. The tf-idf value increases proportionally to the number of times a word appears in the document, but is offset by the frequency of the word in the corpus, which helps to adjust for the fact that some words appear more frequently in general. [^1]

`tf` (Term Frequence)

`idf` (Inverse Document Frequency)

How term is important in corpus?

`tf-idf` - Term frequency–Inverse document frequency

How term is important in document?

## Python Lab

We exam a corpus with 2 documents

* Doc 1: *this is a sample*
* Doc 2: *this is another sample*

## Tf

<table>
<tr>
<td>Vocab</td>
<td>$latex tf=f_{t,d}$</td>
</tr>
<tr>
<td>this</td>
<td></td>
</tr>
<tr>
<td>is</td>
<td></td>
</tr>
<tr>
<td>a</td>
<td></td>
</tr>
<tr>
<td>sample</td>
<td></td>
</tr>
<tr>
<td>another</td>
<td></td>
</tr>
<tr>
</table>
[code lang="python"]
from sklearn.feature_extraction.text import TfidfVectorizer
X = ["this is a sample", "this is another example"]
vectorizer = TfidfVectorizer()
vectorizer.fit_transform(X)
[/code]

Now we find what are important terms of this corpus:

[code lang="python"]
for term in vectorizer.vocabulary_.keys():
    index = vectorizer.vocabulary_[term]
    score = vectorizer._tfidf.idf_[index]
    print "%10s: %2.2f" % (term, score)
[/code]
[code]
      this: 1.00
    sample: 1.41
        is: 1.00
   example: 1.41
   another: 1.41
[/code]

`sample`,`example` and `another` are important term in this corpus.

Next, we look at 2 more documents, and find what are import terms in those documents

[code lang="python"]
print vectorizer.vocabulary_
print vectorizer.transform(["another sample", "this example"])
[/code]

[code]
{u'this': 4, u'sample': 3, u'is': 2, u'example': 1, u'another': 0}
  (0, 3)	0.707106781187
  (0, 0)	0.707106781187
  (1, 4)	0.579738671538
  (1, 1)	0.814802474667
[/code]

In document 1, `sample` (index 3) and `another` (index 0) are equally, but in document 2, `example` (index 0) is more important than `this` (index 4). The reasons is `this` appears in whole corpus, there for it doesn't tell us any more information.

[^1]: [tf–idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf)

# Unigram Bigram Model

# Near-Duplicates

Simhash

[Detecting Near-Duplicates for Web Crawling](http://stackoverflow.com/questions/1908330/simhash-implementation-in-java)

[SimHash](http://aneurone.blogspot.com/2012/09/simhash.html)

# Word2vec

### Installation

[code]
conda install gensim
[/code]

### Lab

Step 1: I download some articles about Hà Nội (the captial of Việt Nam)

Step 2: I use vnTokenizer to tokenize words

Step 3: I train Word2Vec model

#### Resources

Word2vec-pride-vis <small>[code][/code](https://github.com/arnicas/word2vec-pride-vis), [interactive visualization](http://www.ghostweather.com/files/word2vecpride/)</small>

# Document Classification

Document classification or document categorization is a problem in library science, information science and computer science. The task is to assign a document to one or more classes or categories. This may be done "manually" (or "intellectually") or algorithmically. The intellectual classification of documents has mostly been the province of library science, while the algorithmic classification of documents is mainly in information science and computer science. The problems are overlapping, however, and there is therefore interdisciplinary research on document classification. [^2]

# Process [^1]

* Step 1: Generate document features: TFidf Model,
* Step 2: Fit features to a classifier: Multinomial Naive Bayes, Maxent Classifier, DecisionTreeClassifier
* Step 3: Evaluating: use F1 score

[^1]: [Working With Text Data](http://scikit-learn.org/stable/tutorial/text_analytics/working_with_text_data.html)
[^2]: [Document classification](https://en.wikipedia.org/wiki/Document_classification)

# Document Clustering

Document clustering (or text clustering) is the application of cluster analysis to textual documents. It has applications in automatic document organization, topic extraction and fast information retrieval or filtering. [^1]

* TopicModel > LDA

[^1]: [wikipedia, Document Clustering](https://en.wikipedia.org/wiki/Document_clustering)

# Task: Related terms in documents

[Algorithm to find related words in a text](http://stackoverflow.com/questions/7544266/algorithm-to-find-related-words-in-a-text)
[How to find related terms in documents](http://stackoverflow.com/questions/34650672/how-to-find-related-terms-in-documents)

# Topic Models: LDA

# Sentiment Analysis

# Name Entity Recognization

![](https://researchkb.files.wordpress.com/2014/02/ner.png)

Named-entity recognition (NER) (also known as entity identification, entity chunking and entity extraction) is a subtask of information extraction that seeks to locate and classify elements in text into pre-defined categories such as the names of persons, organizations, locations, expressions of times, quantities, monetary values, percentages, etc. [^1]

## Tutorial

[9 - 3 - Sequence Models for Named Entity Recognition-NLP-Professor Dan Jurafsky & Chris Manning](https://www.youtube.com/watch?v=mbMrRT5Osbk)

[^1]: [wikipedia, Named Entity Recognition](https://en.wikipedia.org/wiki/Named-entity_recognition)

# Relation Extraction

# Sentence Segmentation

![](https://s3.amazonaws.com/work-sample-images/blog_segmentation.jpg)

Sentence segmentation is the problem of dividing a string of written language into its component sentences. In English and some other languages, using punctuation, particularly the full stop/period character is a reasonable approximation. However even in English this problem is not trivial due to the use of the full stop character for abbreviations, which may or may not also terminate a sentence.

For example Mr. is not its own sentence in "Mr. Smith went to the shops in Jones Street." When processing plain text, tables of abbreviations that contain periods can help prevent incorrect assignment of sentence boundaries.

As with word segmentation, not all written languages contain punctuation characters which are useful for approximating sentence boundaries.

# English NLP

Dictionary / Wordnet [^1]

Corpus

* [English Wikipedia](https://dumps.wikimedia.org/enwiki/)

[^1]: [English dictionary as txt or xml file with support of synonyms](http://stackoverflow.com/questions/2667057/english-dictionary-as-txt-or-xml-file-with-support-of-synonyms)

# Tools

* [gensims]()
* [wiki]()



