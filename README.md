# Subreddit NLP Model

Slides: `NLP-slide-deck.pdf` in this same directory

This project uses NLP to differentiate between two different subreddits that have somewhat similar content. Both subreddit chosen have posts that follow the format of a long-form question post seeking indepth answers: r/askhistorians and r/askscience. The text-based nature of both of these subreddits make them well suited for this project.

There was minimal cleaning needed for this modeling. There was over 5000 rows gathered in total from both subreddits. And after de-duping and dropping all NaN values (where posts may have been photo-based), there was still well over 3500 rows. Leaving a good amount of data to run our models on.

Some interesting observations was that tri-grams were nearly useless as they did not offer topic-specific insight. They were merely "reddit phrases", as such only unigrams and bi-grams were explored. 

The model was fitted using a gridsearch with a count vectorizer and a MultinomialNB model. The following data shows the best parameters three different text formats. 

```
Basic model with no tuning parameters:
(0.9993009437259699, 0.9475890985324947)


Orginal Text
(0.9905627403005942, 0.9685534591194969)
{'cvec__binary': False,
 'cvec__max_df': 0.5,
 'cvec__max_features': None,
 'cvec__min_df': 1,
 'cvec__ngram_range': (1, 1)}

Stemmed Text
(0.9902132121635792, 0.9664570230607966)
{'cvec__binary': True,
 'cvec__max_df': 0.5,
 'cvec__min_df': 1,
 'cvec__ngram_range': (1, 1)}

Lemmatized Text
(0.9891646277525341, 0.960167714884696)
 'cvec__max_df': 0.5,
 'cvec__min_df': 1,
 'cvec__ngram_range': (1, 1)}

```
