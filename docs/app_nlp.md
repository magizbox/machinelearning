# Natural Language Processing (NLP)

![](https://www.ibm.com/developerworks/mydeveloperworks/blogs/nlp/resource/nlp-shakespeare.jpg)

## NLP Tasks

Morphological Analysis

Discourse Analysis

<h3>Sentiment Analysis</h3>

<a href="https://www.metamind.io/about" target="_blank">MetaMind</a>, @RichardSocher

<h3>Named Entity Recognition</h3>

<a href="http://research.microsoft.com/en-us/people/chiw/kdd15tutorial.aspx" target="_blank">KDD 2015 Tutorial: Automatic Entity Recognition and Typing from Massive Text Corpora - A Phrase and Network Mining Approach</a>

<h3>Relationship Extraction</h3>

<a href="http://www.alchemyapi.com/api/relation-extraction" target="_blank">AlchemyAPI</a>

## NLP Applications

**Information Retrieval (IR)**

Information retrieval (IR) is the activity of obtaining information resources relevant to an information need from a collection of information resources. Searches can be based on metadata or on full-text (or other content-based) indexing.

**Information Extraction (IE)**

Information extraction (IE) is the task of automatically extracting structured information from unstructured and/or semi-structured machine-readable documents. In most of the cases this activity concerns processing human language texts by means of natural language processing (NLP).

**Machine Translation**

**Question Answering (QA)**

Question answering (QA) is a computer science discipline within the fields of information retrieval and natural language processing (NLP), which is concerned with building systems that automatically answer questions posed by humans in a natural language.

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

# Vietnamese NLP

[Hồ Tú Bảo, Về xử lý tiếng Việt trong công nghệ thông tin](http://www.jaist.ac.jp/~bao/Writings/VLSPwhitepaper%20-%20Final.pdf)

## Part I. Core Problems

### 1.1 Dictionaries

* [2004, Hồ Ngọc Đức, The Free Vietnamese Dictionary Project](http://www.informatik.uni-leipzig.de/~duc/Dict/)

### 1.2 Wordnet

* [viet wordnet](http://viet.wordnet.vn/wnms/editor/search/by-word/y%C3%AAu/2%7Cv)

### 1.3 Corpus

**<a href="http://viet.jnlp.org/download-du-lieu-tu-vung-corpus" target="_blank">VNESEcorpus</a>**, 650.000 sentences, 10.000 articles from vietnamnet.vn, dantri.com.vn, nhanhdan.com.vn. Size: 64.59 Mb

**<a href="http://viet.jnlp.org/download-du-lieu-tu-vung-corpus" target="_blank">VNTQcorpus(small)</a>**, 300.000 sentences, 1.000 articles from vnthuquan.net
Size: ~35 Mb

**<a href="http://viet.jnlp.org/download-du-lieu-tu-vung-corpus" target="_blank">VNTQcorpus(big)</a>**, 1.750.000 sentences, 13.000 articles from vnthuquan.net, Size: ~240 Mb

### 1.4 [Sentence Segmentation](http://magizbox.com/index.php/machine-learning/ds-applications/natural-language-processing/sentence-segmentation/)

Unknown

### 1.5 Word Segmentation

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png) **[Vitk](https://github.com/phuonglh/vn.vitk)** `spark`

Authors: [Le Hong Phuong](http://mim.hus.vnu.edu.vn/phuonglh)
Date: May 08, 2016

This is the first release of a Vietnamese text processing toolkit, which is called "Vitk", developed by Phuong LE-HONG at College of Natural Sciences, Vietnam National University, Hanoi.

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png) **[vnTokenizer](http://mim.hus.vnu.edu.vn/phuonglh/softwares/vnTokenizer)** `java`

Authors: [Le Hong Phuong](http://mim.hus.vnu.edu.vn/phuonglh)
Date: September 28, 2009

vnTokenizer is a software for tokenizing Vietnamese texts. It segments Vietnamese texts into lexical units (words, names, dates, numbers and other regular expressions) with a high accuracy, of about 98% on a test set extracted from the Vietnamese treebank.

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png)  **<a href="http://jvnsegmenter.sourceforge.net/" target="_blank">JVnSegmenter</a>** `java`

Authors: Cam-Tu Nguyen (ncamtu@gmail.com), Xuan-Hieu Phan (pxhieu@gmail.com)
Date: Mar 24, 2007

A Java-based Vietnamese Word Segmentation Tool

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png) **<a href="https://github.com/rockkhuya/DongDu" target="_blank">DongDu</a>** `C++`

Authors: rockkhuya(<a href="mailto:rockkhuya@gmail.com">rockkhuya@gmail.com</a>)

A Vietnamese word segmentation tool.

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png) **[Roy_VnTokenizer](https://github.com/roy-a/Roy_VnTokenizer)** `python`

Authors: Anindya Roy
Date: Jan 22, 2014

Vietnamese tokenization

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png) **<a href="http://vlsp.vietlp.org:8080/demo/?page=seg_pos_chunk" target="_blank">Online Tool from VLSP</a>** `online`

Not Available

### 1.6 Part-of-speech tagging (POS Tagging)

VCCorp 2016: 94.5% [^1]
Vitk 2016: accurary 95% (Vietnamese Tree Bank)

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png) **[Vitk](https://github.com/phuonglh/vn.vitk)** `spark`

Authors: [Le Hong Phuong](http://mim.hus.vnu.edu.vn/phuonglh)
Date: May 08, 2016

The part-of-speech tagger of Vitk can tag about 1,105,000 tokens per second, on a single machine, giving an accuracy of about 95% on the Vietnamese treebank.

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png) **<a href="http://mim.hus.vnu.edu.vn/phuonglh/softwares/vnTagger" target="_blank">vnTagger</a>** `java`

Vietnamese part-of-speech tagging

Authors: [Le Hong Phuong](http://mim.hus.vnu.edu.vn/phuonglh)
Date: Aug 05, 2010

**Paper**

* ![](http://icons.iconarchive.com/icons/graphicloads/folded/24/doc-page-folded-icon.png) [Le Hong Phuong, 2010, An empirical study of maximum entropy approach for part-of-speech tagging of Vietnamese texts](http://mim.hus.vnu.edu.vn/phuonglh/node/40)

### 1.7 Coreference

VCCorp 2016: 57% [^1]

**Thesis & Papers**:

* ![](http://icons.iconarchive.com/icons/graphicloads/folded/24/doc-page-folded-icon.png) [2011, Giải quyết bài toán đồng tham chiếu trong văn bản tiếng việt dựa vào phương pháp máy vector hỗ trợ SVM](http://www.coltech.vnu.edu.vn/~thuyhq/Student_Thesis/K52_Le_Duc_Trong_Thesis.pdf)

### 1.8 Dependency Grammar

VCCorp 2016: 73% [^1]

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/doc-page-folded-icon.png) [2013, Nguyễn Vi Dương, Nguyễn Thị Đảm, Bộ chuyển đổi từ văn phạm thành phần sang văn phạm phụ thuộc cho tiếng Việt](https://bitbucket.org/epilab/vnlp/downloads/DependencyGrammarForVNese.doc)

### 1.9 Chunking

VCCorp 2016: 83% [^1]

### [1.10 Named Entity Recognition (NER)](http://magizbox.com/index.php/machine-learning/ds-applications/natural-language-processing/name-entity-recognization/)

VCCorp 2016: 84.8% [^1]

**Papers**:

* ![](http://icons.iconarchive.com/icons/graphicloads/folded/24/doc-page-folded-icon.png) [2007, Named Entity Recognition in Vietnamese documents](https://www.nii.ac.jp/pi/n4/4_5.pdf)
* ![](http://icons.iconarchive.com/icons/graphicloads/folded/24/doc-page-folded-icon.png) [2005, Named Entity Recognition in Vietnamese Free-Text and Web Documents Using Conditional Random Fields](http://lamda.nju.edu.cn/nguyenct/files/papers/ncamtu-09-paper_ner.pdf)

### 1.11 Relations Extraction Systems

Unknown

### 1.12 Sentiment Analysis

![](http://icons.iconarchive.com/icons/graphicloads/folded/24/setting-folded-icon.png) **[Sentiment Analysis](https://bitbucket.org/epilab/vnlp/downloads/sentiment-analysis.zip)** `java`

Authors: [Epi Lab](https://bitbucket.org/epilab/)
Date: Aug 01, 2013

### 1.13 Language Identification

Unknown

## Part 2. Vietnamse NLP Groups

**Groups**

* [vnlp.net, (2010-now)](http://vnlp.net/)
* [kde lab, (2014-now)](http://kde.soict.hust.edu.vn/)

**People**

* [Assoc. Prof. Ha Quang Thuy](http://www.coltech.vnu.edu.vn/~thuyhq/)
* [Prof. Tu-Bao Ho](http://www.jaist.ac.jp/~bao/)
* [Khoat Than](http://is.hust.edu.vn/~khoattq/)
* [Cam Tu Nguyen](http://www.dais.is.tohoku.ac.jp/~ncamtu/index.htm)
* [CAM-TU NGUYEN](http://lamda.nju.edu.cn/nguyenct/?AspxAutoDetectCookieSupport=1)
* [Le Hong Phuong](http://mim.hus.vnu.edu.vn/phuonglh/)
* [Phan Xuan Hieu](https://sites.google.com/site/pxhieu/)
* [Trần Mai Vũ](http://fit.uet.vnu.edu.vn/gioi-thieu/giang-vien/vutm/)
* [Nguyễn Kiêm Hiếu](http://soict.hust.edu.vn/index.php/bo-mon-trung-tam/he-thong-thong-tin/can-bo/227-ts-nguyen-kiem-hieu)

## Part 3. Applications

### [VAV - Trợ lý ảo cho người Việt](https://play.google.com/store/apps/details?id=com.mdnteam.vav)

Date: Nov 2015 - now

<img src="https://lh3.googleusercontent.com/TOdXdeSwJ6qQy4gYqWJbPbep8Sb82h9oZPsor3WWXyi72HafO3xttiBlD-dpnKAahyY=h900-rw" style="height:80px"/>

**MDN-Team, Khoa CNTT, Trường ĐH Công nghệ, ĐHQG HN Tools**

> Bạn đang nghĩ đến một ứng dụng thông minh trên di động cho phép bạn tương tác bằng giọng nói để hẹn chuông báo thức, đặt lịch cho một cuộc họp, bật định vị, gọi điện cho ai đó, truy cập một trang web bất kỳ, tìm đường trên bản đồ, định vị cây ATM của một ngân hàng nào đó gần với bạn, hay thưởng thức một bản nhạc mình yêu thích … Ứng dụng Trợ lý ảo VAV chính là câu trả lời cho bạn.
> Được thiết kế và phát triển dựa trên các kỹ thuật trí tuệ nhân tạo (học máy, phân tích và hiểu ngôn ngữ tự nhiên), VAV có thể hiểu được ý định của bạn dù bạn diễn đạt câu lệnh của mình theo nhiều cách khác nhau mà không cần tuân theo bất kỳ khuôn mẫu nào cho trước. Những gì VAV hướng tới là trở thành một trợ lý ảo thông minh giúp bạn thực hiện những điều mình muốn và là một người đồng hành thân thiện, dí dỏm bên bạn.

[^1]: [2016, Big Challenges for Data Scientists at VCCORP](https://drive.google.com/file/d/0B6LYda0EhWbSelc2VTlZVFZia1E/view?usp=sharing)



