### K-Nearest Neighbours and Naive Bayes Classification for Tweet Analysis

This project aimed to classify tweet virality and predict tweet location using machine learning techniques. K-Nearest Neighbours (KNN) was implemented to determine whether a tweet was viral based on features such as length, hashtags, and user verification status. Additionally, a Naive Bayes classifier was employed to predict the origin of tweets based on word content. The models were both cross-validated to score them.

---

### Data Preparation and Preprocessing

#### K-Nearest Neighbours for Tweet Virality
The random tweets dataset contained a collection of tweets with metadata such as retweet count, text content, user details, and engagement metrics. To define virality, the median retweet count was used as a threshold: tweets with retweets above the median were classified as viral (1), while others were not (0).
Feature engineering was performed to extract seemingly relevant attributes:

-**Tweet length**: Character count of the tweet text.
-**Follower count**: Number of followers of the tweet author.
-**Friend count**: Number of accounts the user follows that mutually follows them back.
-**Verified status**: Boolean of account verification.
-**Hashtag and mention count**: Number of hashtags (#) and mentions (@) in the tweet.

Data was scaled using standard normalization techniques to improve model convergence and performance.

#### Naive Bayes for Tweet Location Prediction
The location datasets included tweets from three cities: New York, London, and Paris. The text content was extracted and labeled numerically according to location.
The dataset was split into training and testing sets, and CountVectorizer was used to convert text data into numerical format suitable for the Naive Bayes classifier.

---

### Model Design and Architecture

#### K-Nearest Neighbours
KNN classification was applied to the processed dataset. K-Nearest Neighbours (KNN)
KNN is a supervised learning algorithm used for classification and regression. It operates on the principle that data points with similar features are likely to belong to the same category. Given a new data point, the algorithm:
Computes the distance between the new point and all training points using a distance metric (e.g., Euclidean distance).
Selects the K nearest points.
Assigns the majority class among the selected points to the new data point.
KNN is a non-parametric model, meaning it does not make strong assumptions about the data distribution. However, it is sensitive to the choice of K and feature scaling, making optimization crucial.
The choice of K (number of neighbors) was optimized by iterating over values from 1 to 200 and plotting accuracy scores. The best-performing K was selected based on the elbow method where K = 50 was where the curve began to plateau.

#### Naive Bayes
A multinomial Naive Bayes classifier was used to predict tweet location. Naive Bayes is a probabilistic classifier based on Bayes' Theorem. The "naive" assumption assumes independence among features, simplifying calculations. Despite this simplification, Naive Bayes performs well for text classification tasks due to the relatively independent nature of words in a document.

---

### Training and Evaluation

#### K-Nearest Neighbours
The dataset was divided into an 80-20 training-test split to ensure robust evaluation of the model. Various values of K were tested to optimize performance, with K = 106 yielding the highest accuracy of approximately 75.9%. K = 50 was instead used in the model for which a 5-fold cross-validation technique was employed to further validate model reliability, producing an average accuracy of 74.6%. 

#### Naive Bayes
The Naive Bayes classifier was trained using a similar 80-20 split, which resulted in a cross-validated accuracy of 68.2%. Performance evaluation was conducted using a confusion matrix, revealing notable misclassifications, particularly between tweets from New York and London. The classification report further provided insights into key performance metrics such as precision, recall, and F1 scores, offering a comprehensive view of the model's strengths and weaknesses.

---

### Challenges and Solutions

- **Feature selection for KNN**: Some features contributed more to virality prediction. Experimentation with feature combinations improved model performance.
- **Overfitting in KNN**: A high number of neighbors led to excessive smoothing, while too few resulted in noise sensitivity. The optimal K balanced generalization and accuracy.

---

### Future Directions

Enhancing prediction accuracy can be achieved by incorporating sentiment analysis and topic modeling. These techniques refine classifications by recognising the emotional tone and subject matter within the text.

Deep learning models like Long Short-Term Memory (LSTM) networks offer another avenue for improving classification performance. LSTMs are particularly suited for text data due to their ability to recognize long-range dependencies, making them effective in capturing the sequential nature of tweet content.
Expanding the dataset with tweets from additional locations can improve model generalizability. A more diverse dataset reduces biases and enhances prediction reliability across different regions.


