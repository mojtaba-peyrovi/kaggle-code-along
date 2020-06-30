

> Written with [StackEdit](https://stackedit.io/).

### Alexa Review Notebook
link: (https://www.kaggle.com/roshansharma/amazon-alexa-reviews](https://www.kaggle.com/roshansharma/amazon-alexa-reviews)

There is a very useful screenshot I added to named /screenshots/matplotlib-anatomy.png

### Some Matplitlib & Seaborn points:

- There are several styles in Seaborn that we can see the list of them by running:
> python: plt.style.available

If we want to use a specific style, not the default we can do like this:
```
plt.style.use('dark_background')
```
- if we want to rotate the ticks, we can say like this:
```
plt.xticks(rotation=90)
```
### NLP with Scikit Learn:
First, we want to see the frequency of each word. We can use CountVectorizer() module from sklearn library.

#### CountVectorizer:
For a list of strings, creates a matrix (one row per value in the list) and each row shows the count of each word's repetition. 
The number of columns for this matrix equals the number of unique words in the list (the matrix is sparse).

> ### What are N-grams?
> N-grams of texts are extensively used in text mining and natural language processing tasks. They are basically a set of co-occurring words within a given window and when computing the n-grams you typically move one word forward (although you can move X words forward in more advanced scenarios).
> For example, for the sentence  _“The cow jumps over the moon”_. If N=2 (known as bigrams), then the ngrams would be:

>-   the cow
>-   cow jumps
>-   jumps over
>-   over the
>-   the moon


CountVectorizer, converts raw text to a numerical representation of words and N-grams. This way we can easily use the matrix as a feature for machine learning.
By default CounterVectorizer does the following to your list of text values:
> -   lowercases your text (set  `lowercase=false`  if you don’t want lowercasing)
>-   uses utf-8 encoding
>-   performs tokenization (converts raw text to smaller units of text)
>-   uses word level tokenization (meaning each word is treated as a separate token)
>-   ignores single characters during tokenization (say goodbye to words like ‘a’ and ‘I’)

**CountVectorizer.vocabulary_ :** returns a dictionary of words and their positions.

#### Stop Words: 
The words we don't care for , in the text like "the", "and", "is" are stop words and we can pass them directly in CountVectorizer when we want to instantiate it.  like this:
```
cv = CountVectorizr(stop_words=["and","is","the"])
```
- The other method, is to automatically remove the words with less appearance than a specific threshold specified by us. like this:
```
#ignore terms that appeared in less than 2 documents 
cv = CountVectorizer(data,min_df=2)
```
And if we want to see what words have been removed, we can say:
```
cv.stop_words_
# it will return the list of all filtered words
```
and again to see what is remaining, we can use cv.vocabulary_

- We can also pass max_df for words that are too common that we want to ignore them. we can pass absolute values, like 10,20,30, or a proportion(e.g. 0.85 meaning, ignore words appeared in 85% of the documents as they are too common).

```
# ignore terms that appear in 50% of the documents
cv = CountVectorizer(data,max_df=0.50)
```
A value between 0.75-0.85 normally works well.

- Another way, is to just pass the word English as stop_words and it automatically removes all english stop words.

