## Python Implementation for TextRank

This repository is based on [pytextrank](https://github.com/ceteri/pytextrank). Refer to original repository for more information.

Modifications:

-  Removed unused argument `Parse=True` which causes error with spaCy `spacy_nlp` function. Refer to [laxatives' Pull Request](https://github.com/ceteri/pytextrank/pull/11).
-  Modified functions to avoid writing intermediate results to json files
-  Added function `top_keywords_sentences` which return the top keywords and sentences to for easy use

## Differences vs the initial Mihalcea paper
Python implementation of *TextRank*, based on the
`Mihalcea 2004 <http://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf>`_
paper.

Modifications to the original algorithm by
`Rada Mihalcea <https://web.eecs.umich.edu/~mihalcea/>`_, et al.
include:

-  fixed bug; see `Java impl, 2008 <https://github.com/ceteri/textrank>`_
-  use of lemmatization instead of stemming
-  verbs included in the graph (but not in the resulting keyphrases)
-  named entity recognition
-  normalized keyphrase ranks used in summarization

The results produced by this implementation are intended more for use
as *feature vectors* in machine learning, not as academic paper
summaries.

Inspired by `Williams 2016 <http://mike.place/2016/summarization/>`_
talk on *text summarization*.


## Example Usage

```python
import xang1234_pytextrank as pyt

text='This is a test senctence for pytextrank'
sentence, keywords= pyt.top_keywords_sentences(text, phrase_limit=15, sent_word_limit=150)
```
For more details of usage, refer to [this post](https://xang1234.github.io/textrank/)

## Dependencies and Installation

This code has dependencies on several other Python projects:

-  `spaCy <https://spacy.io/docs/usage/>`_
-  `NetworkX <http://networkx.readthedocs.io/>`_
-  `datasketch <https://github.com/ekzhu/datasketch>`_
-  `graphviz <https://pypi.python.org/pypi/graphviz>`_


Also, the runtime depends on a local file called ``stop.txt`` which
contains a list of *stopwords*. You can override this in the
`normalize_key_phrases()` call.
