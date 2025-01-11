---
aliases:
  - Term Frequency-Inverse Document Frequency
---
**TF-IDF** stands for Term Frequency Inverse Document Frequency of records. It can be defined as the calculation of how relevant a word in a series or corpus is to a text. The meaning increases proportionally to the number of times in the text a word appears but is compensated by the word frequency in the corpus (data-set).

**Terminologies:**
- ***~={yellow}Term Frequency=~***: In ~={green}document $d$=~, the frequency represents the number of instances of a given ~={green}word $t$=~. Therefore, we can see that it becomes more relevant when a word appears in the text, which is rational. Since the ordering of terms is not significant, we can use a vector to describe the text in the bag of term models. For each specific term in the paper, there is an entry with the value being the term frequency. $$tf(t,d) = \frac{\text{count of word t in document d}}{\text{number of words document in d}}$$
- ***~={yellow}Document Frequency=~***: This tests the meaning of the text, which is very similar to TF, in the whole corpus (data-set) collection. The only difference is that in document d, TF is the frequency counter for a term t, while df is the number of occurrences in the document set N of the term t. In other words, **~={cyan}the number of papers in which the word is present is DF=~**. $$df(t) = \text{occurrence of t in documents}$$
- ***~={yellow}Inverse Document Frequency:=~*** Mainly, it tests how relevant the word is. The key aim of the search is to locate the appropriate records that fit the demand. Since tf considers all terms equally significant, it is therefore not only possible to use the term frequencies to measure the weight of the term in the paper. 
  
  First, find the document frequency of a term t by counting the number of documents containing the term: $$df(t) = N(t)$$
  Where,
  $df(t) = \text{Document frequency of a term t}$
  $N(t)$ = Number of documents containing the term t.
  
  Term frequency is the number of instances of a term in a single document only; although the frequency of the document is the number of separate documents in which the term appears, it depends on the entire corpus. Now let’s look at the definition of the frequency of the inverse paper. ~={cyan}The IDF of the word is the number of documents in the corpus separated by the frequency of the text.=~$$idf(t) = \frac{N}{df(t)} = \frac{N}{N(t)}$$
  ~={cyan}The more common word is supposed to be considered less significant, but the element (most definite integers) seems too harsh. We then take the logarithm (with base 2) of the inverse frequency of the paper=~. So the if of the term t becomes:$$idf(t) = log(N/ df(t))$$
- ***~={yellow}Computation=~***: Tf-idf is one of the best metrics to determine how significant a term is to a text in a series or a corpus. tf-idf is a weighting system that assigns a weight to each word in a document based on its term frequency (tf) and the reciprocal document frequency (tf) (idf). The words with higher scores of weight are deemed to be more significant.

Usually, the tf-idf weight consists of two terms-
1. **Normalized Term Frequency (tf)**
2. **Inverse Document Frequency (idf)**

$$
\text{tf-idf(t, d)} = \text{tf(t, d)} * \text{idf(t)}
$$
In python tf-idf values can be computed using `TfidfVectorizer()` method in _sklearn_ module.
```python
sklearn.feature_extraction.text.TfidfVectorizer(input)
```
**Parameters:**
- **Input:** It refers to parameter document passed, it can be a filename, file or content itself.

**Attributes:**

- **vocabulary**__**:** It returns a dictionary of terms as keys and values as_ feature indices.
- **idf_**_**:** It returns the_ inverse document frequency vector of the document passed as a parameter.
  
**Returns:**
- **fit_transform():** It returns an array of terms along with tf-idf values.
- **get_feature_names():** It returns a list of feature names.

#### Step-by-step Approach
###### Import Modules
```python
from sklearn.feature_extration.text import TfidfVectorizer
```
###### Prepare Data
```
`# assign documents`

`d0` `=` `'Geeks for geeks'`

`d1` `=` `'Geeks'`

`d2` `=` `'r2j'`

`# merge documents into a single corpus`

`string` `=` `[d0, d1, d2]`
```