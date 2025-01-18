K-Nearest Neighbours to classify tweet virality


```python
# Load and inspect tweet dataset
import pandas as pd

all_tweets = pd.read_json("random_tweets.json", lines=True)

print(all_tweets.loc[0]['user'])
print(len(all_tweets))
print(all_tweets.columns)
print(all_tweets.loc[0]['favorite_count'])
print(all_tweets.loc[0]['text'])
print(all_tweets.loc[0]['user']['location'])
```

    {'id': 145388018, 'id_str': '145388018', 'name': 'Derek Wolkenhauer', 'screen_name': 'derekw221', 'location': 'Waterloo, Iowa', 'description': '', 'url': None, 'entities': {'description': {'urls': []}}, 'protected': False, 'followers_count': 215, 'friends_count': 335, 'listed_count': 2, 'created_at': 'Tue May 18 21:30:10 +0000 2010', 'favourites_count': 3419, 'utc_offset': None, 'time_zone': None, 'geo_enabled': True, 'verified': False, 'statuses_count': 4475, 'lang': 'en', 'contributors_enabled': False, 'is_translator': False, 'is_translation_enabled': False, 'profile_background_color': '022330', 'profile_background_image_url': 'http://abs.twimg.com/images/themes/theme15/bg.png', 'profile_background_image_url_https': 'https://abs.twimg.com/images/themes/theme15/bg.png', 'profile_background_tile': False, 'profile_image_url': 'http://pbs.twimg.com/profile_images/995790590276243456/cgxRVviN_normal.jpg', 'profile_image_url_https': 'https://pbs.twimg.com/profile_images/995790590276243456/cgxRVviN_normal.jpg', 'profile_banner_url': 'https://pbs.twimg.com/profile_banners/145388018/1494937921', 'profile_link_color': '0084B4', 'profile_sidebar_border_color': 'A8C7F7', 'profile_sidebar_fill_color': 'C0DFEC', 'profile_text_color': '333333', 'profile_use_background_image': True, 'has_extended_profile': True, 'default_profile': False, 'default_profile_image': False, 'following': False, 'follow_request_sent': False, 'notifications': False, 'translator_type': 'none'}
    11099
    Index(['created_at', 'id', 'id_str', 'text', 'truncated', 'entities',
           'metadata', 'source', 'in_reply_to_status_id',
           'in_reply_to_status_id_str', 'in_reply_to_user_id',
           'in_reply_to_user_id_str', 'in_reply_to_screen_name', 'user', 'geo',
           'coordinates', 'place', 'contributors', 'retweeted_status',
           'is_quote_status', 'retweet_count', 'favorite_count', 'favorited',
           'retweeted', 'lang', 'possibly_sensitive', 'quoted_status_id',
           'quoted_status_id_str', 'extended_entities', 'quoted_status',
           'withheld_in_countries'],
          dtype='object')
    0
    RT @KWWLStormTrack7: We are more than a month into summer but the days are getting shorter. The sunrise is about 25 minutes later on July 3…
    Waterloo, Iowa
    


```python
# Define virality based on median retweet count
import numpy as np

median_retweets = all_tweets['retweet_count'].median()
print(median_retweets)
all_tweets['is_viral'] = np.where(all_tweets['retweet_count'] >= median_retweets, 1, 0)
print(all_tweets['is_viral'].value_counts())
```

    13.0
    is_viral
    1    5591
    0    5508
    Name: count, dtype: int64
    


```python
# Feature engineering for KNN
all_tweets['tweet_length'] = all_tweets.apply(lambda tweet: len(tweet['text']), axis=1)
all_tweets['followers_count'] = all_tweets['user'].apply(lambda tweet: tweet['followers_count'])
all_tweets['friends_count'] = all_tweets['user'].apply(lambda tweet: tweet['friends_count'])
all_tweets['verified'] = all_tweets['user'].apply(lambda tweet: 1 if tweet['verified'] == True else 0)
all_tweets['hashtags'] = all_tweets['text'].apply(lambda tweet: tweet.count("#"))
all_tweets['mentions'] = all_tweets['text'].apply(lambda tweet: tweet.count("@"))
```


```python
# Prepare data for KNN classification
from sklearn.preprocessing import scale

labels = all_tweets['is_viral']
data = all_tweets[['tweet_length','followers_count','friends_count', 'hashtags', 'mentions', 'verified']]
scaled_data = scale(data, axis=0)

print(scaled_data[0])
```

    [ 0.6164054  -0.02878298 -0.14483305 -0.32045057 -0.08781719 -0.12656924]
    


```python
# Split dataset for KNN
from sklearn.model_selection import train_test_split

train_data, test_data, train_labels, test_labels = train_test_split(scaled_data, labels, test_size = 0.2, random_state = 1)
```


```python
# Plot K selection
import matplotlib.pyplot as plt
from sklearn.neighbors import KNeighborsClassifier

scores = []
for k in range(1, 200):
    classifier = KNeighborsClassifier(n_neighbors = k)
    classifier.fit(train_data, train_labels)
    scores.append(classifier.score(test_data, test_labels))
    
plt.plot(range(1,200), scores)
plt.show()
```


    
![png](output_6_0.png)
    



```python
print([max(scores), range(1, 200)[scores.index(max(scores))]])
```

    [0.7594594594594595, 106]
    


```python
# Evaluate using cross-validation for chosen k
from sklearn.model_selection import cross_val_score

classifier = KNeighborsClassifier(n_neighbors = 50)
knn_cv_scores = cross_val_score(classifier, scaled_data, labels, cv=5)
print(f"KNN Cross-validation accuracy: {knn_cv_scores.mean():.4f}")
```

    KNN Cross-validation accuracy: 0.7460
    

Naive-Bayes to predict tweet location


```python
# Load tweet datasets for Naive Bayes classification
import pandas as pd

new_york_tweets = pd.read_json("new_york.json", lines=True)
print(len(new_york_tweets))
print(new_york_tweets.columns)
print(new_york_tweets.loc[12]["text"])
```

    4723
    Index(['created_at', 'id', 'id_str', 'text', 'display_text_range', 'source',
           'truncated', 'in_reply_to_status_id', 'in_reply_to_status_id_str',
           'in_reply_to_user_id', 'in_reply_to_user_id_str',
           'in_reply_to_screen_name', 'user', 'geo', 'coordinates', 'place',
           'contributors', 'is_quote_status', 'quote_count', 'reply_count',
           'retweet_count', 'favorite_count', 'entities', 'favorited', 'retweeted',
           'filter_level', 'lang', 'timestamp_ms', 'extended_tweet',
           'possibly_sensitive', 'quoted_status_id', 'quoted_status_id_str',
           'quoted_status', 'quoted_status_permalink', 'extended_entities',
           'withheld_in_countries'],
          dtype='object')
    Be best #ThursdayThoughts
    


```python
london_tweets = pd.read_json("london.json", lines=True)
paris_tweets = pd.read_json("paris.json", lines=True)
print(len(london_tweets))
print(len(paris_tweets))
```

    5341
    2510
    


```python
# Prepare text and labels for Naive Bayes
new_york_text = new_york_tweets["text"].tolist()
london_text = london_tweets["text"].tolist()
paris_text = paris_tweets["text"].tolist()

all_tweets = new_york_text + london_text + paris_text
labels = [0] * len(new_york_text) + [1] * len(london_text) + [2] * len(paris_text)
```


```python
# Split dataset for Naive Bayes
from sklearn.model_selection import train_test_split

train_data, test_data, train_labels, test_labels = train_test_split(all_tweets, labels, test_size = 0.2, random_state = 1)
print(len(train_data))
print(len(test_data))
```

    10059
    2515
    


```python
# Convert text to numerical format
from sklearn.feature_extraction.text import CountVectorizer

counter = CountVectorizer()
counter.fit(train_data)
train_counts = counter.transform(train_data)
test_counts = counter.transform(test_data)
```


```python
# Train Naive Bayes classifier
from sklearn.naive_bayes import MultinomialNB

classifier = MultinomialNB()
classifier.fit(train_counts, train_labels)
predictions = classifier.predict(test_counts)
```


```python
# Evaluate using cross-validation
from sklearn.model_selection import cross_val_score

nb_cv_scores = cross_val_score(classifier, train_counts, train_labels, cv=5)
print(f"Naive-Bayes Cross-validation accuracy: {nb_cv_scores.mean():.4f}")
```

    Naive-Bayes Cross-validation accuracy: 0.6828
    


```python
from sklearn.metrics import confusion_matrix
from sklearn.metrics import classification_report

print(confusion_matrix(test_labels, predictions))
print("Naive Bayes Classification Report:\n", classification_report(test_labels, predictions))
```

    [[541 404  28]
     [203 824  34]
     [ 38 103 340]]
    Naive Bayes Classification Report:
                   precision    recall  f1-score   support
    
               0       0.69      0.56      0.62       973
               1       0.62      0.78      0.69      1061
               2       0.85      0.71      0.77       481
    
        accuracy                           0.68      2515
       macro avg       0.72      0.68      0.69      2515
    weighted avg       0.69      0.68      0.68      2515
    
    


```python
# Confusion Matrix Visualization
plt.figure(figsize=(6, 6))
plt.imshow(confusion_matrix(test_labels, predictions), cmap='Blues', interpolation='nearest')
plt.colorbar()
plt.xlabel("Predicted Label")
plt.ylabel("True Label")
plt.title("Naive Bayes Confusion Matrix")
plt.show()
```


    
![png](output_18_0.png)
    

