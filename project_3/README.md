![SQ](https://dynaimage.cdn.cnn.com/cnn/q_auto,w_1070,c_fill,g_auto,h_602,ar_16:9/http%3A%2F%2Fcdn.cnn.com%2Fcnnnext%2Fdam%2Fassets%2F210101120248-4-singapore-airlines.jpg) 
# Project 3: Web APIs & NLP

### Contents:
- [Problem Statement](#Problem-Statement)
- [Datasets](#Datasets) 
- [Data Dictionary](#Data-Dictionary)
- [Brief Summary of Analysis](#Brief-Summary-of-Analysis)
- [Packages](#Packages)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Limitations](#Limitations)

### Problem Statement
With the rise of chatbots across different online platforms to answer to customers' queries, there is a need for the queries to be directed to the correct channel or customer service support so that they can be resolved timely. With technology being so readily available nowadays, the volume of such queries through chatbots or even emails can be overwhelming and thus, challenging to be directed manually. Moreover, some queries might not be phrased in a concise manner with the use of keywords generally used by the companies, causing a miscommunication.

We are a team of data scientists working for an airline company seeking to build a machine learning algorithm to direct incoming queries to the right channel. The company has a lot of queries particularly on its membership programme (Krisflyer) and services (inflight catering, amentities and lounges). As such, we will be scraping some text data from an online forum which focuses on our airline company, and use it to train our machine to classify any new queries to the correct category.

---

### Datasets
The datasets used in this classification project are saved in the [`datasets`](./datasets/) folder.

Under the [`webscraped_data`](./datasets/webscraped_data/) folder, there are four datasets scraped from the forum dedicated to Singapore Airlines called [SQTalk](http://www.sqtalk.com/forum/).
* [`krisflyer.csv`](./datasets/webscraped_data/krisflyer.csv): this data contains topics and posts related to earning miles, redeeming miles and status in Singapore Airlines' frequent flyer programmes
* [`lounges.csv`](./datasets/webscraped_data/lounges.csv/): this data contains topics and posts related to airport lounges one can access when flying with Singapore Airlines
* [`amenity.csv`](./datasets/webscraped_data/amenity.csv/): this data contains topics and posts related to the amenity kits onboard Singapore Airlines
* [`catering.csv`](./datasets/webscraped_data/catering.csv/): this data contains topics and posts related to the menus onboard Singapore Airlines

Under the main [`datasets`](./datasets/) folder, there is a combined dataset. As this is a binary classification project, the forum category of posts under amenity, catering and lounges are grouped under 'amenity_catering_lounges'.
* [`sq_forums.csv`](./datasets/sq_forums.csv/): this data contains the combined data from the four aforementioned datasets on which the machine learning algorithm will be trained

---

### Data Dictionary
|Feature|Type|Description|
|:---|:---|:---| 
|title|string|topic of the post|
|link|string|url link of the post|
|reply|string|response to the topic|
|forum|string|forum category from which the post came from - either 'amenity_catering_lounges' or 'krisflyer'

---

### Brief Summary of Analysis
Under the [`codes`](./codes/) folder for this project, the code notebooks are named in numerical order.
- 00_webscrape folder: the folder contains the code notebooks used to scrape the text data from the target forum
- 01_baseline_model: a baseline classification model is fitted to the sq_forums.csv dataset and evaluated
- 02_model_tuning: different vectorizers and classifiers were fitted to find the best machine learning algorithm
- 03_gridsearch: GridSearch was done to further improve the metrics
- 04_zero_shot_classification: a pretrained model was used and evaluated, with the output saved under the [`output`](./codes/output/) folder
- 05_data_aug: data augmentation was implemented to further improve the metrics, with the output saved under the [`output`](./codes/output/) folder
- 06_lemming_and_conclusions: lemmatization was done in an attempt to further improve the metrics, and conclusions were made

---

### Packages
Packages was downloaded to implement data augmenation and the downloaded files have been saved under the [`packages`](./packages/] folder.

---

### Conclusions and Recommendations
- The objective of this project is to build a machine learning algorithm for an airline company to direct incoming queries to the right channel, namely the membership programme (Krisflyer) and services (inflight catering, amentities and lounges). 

1. Firstly, webscraping was done from an online forum dedicated to the airline company since queries were posted there especially when customers could not reach a customer support agent.

2. A baseline model using CountVectorizer (transformer) and Multinomial Naive Bayes (estimator) was then fitted and evaluated using the following metrics.

|**Metrics**|**MultinomialNB()**|
|:---|:---|
|train_score|0.858|
|test_score|0.844|
|sensitivity|0.986|
|precision|0.801|
|f1 score|0.884|
|specificity|0.626|
|roc auc|0.806|

>A model accuracy of more than 80% is great. Furthermore, as the accuracy score of the train dataset is close to and higher than that of the test dataset, there is no evidence of an overfit. Since the objective is to classify a reply to the correct forum category, the cost of false positives (model predicts a reply to be under 'krisflyer' category, when it is actually not) is the same as the cost of false negatives (model predicts a reply to be under 'amenity_catering_lounges' category, when it is actually not) - a dissatisfied costumer. As such, `accuracy` is a suitable metric. However, due to imbalanced nature of the target variable, the `accuracy` metric is not suitable.
> The other metrics including f1 score, specificity and roc/auc score were then optimised.

3. Model tuning was done by fitting different vectorizers and classifiers to find the best model yielding the highest metrics through GridSearch. 

|**Metrics**|**MultinomialNB() (baseline)**|**TfidfVectorizer with LinearSVC (with GridSearch4)**|**Zero Shot Classification**|
|:---|:---|:---|:---|
|train_score|0.858|0.959|-|
|test_score|0.844|0.922|0.570|
|sensitivity|0.986|0.924|0.407|
|precision|0.801|0.946|0.775|
|f1 score|0.884|0.935|0.533|
|specificity|0.626|0.919|0.819|
|roc auc|0.806|0.922|0.613|

> Overall, the model with TfidfVectorizer with LinearSVC (with GridSearch4) stands out across different metrics.

4. Data augmentation was done to remedy the problem of the imbalanced dataset so that the `accuracy` metric can be used as well.
> Compared to the model with an imbalanced target variable, the model with a balanced dataset has a higher accuracy score, with the vectorizer and estimator kept constant.

|**Metrics**|**Model with an imbalanced dataset**|**Model with a balanced dataset**|
|:---|:---|:---|
|train_score|0.887|0.909|
|test_score (accuracy score)|0.873|0.893|

5. Again, GridSearch was done to find the best model yielding the highest metrics.
> Comparing the best models with TfidfVectorizer and LinearSVC with an imbalanced and balanced dataset, the `accuracy` scores are better with the balanced dataset as summarised below.

|**Metrics**|**Model with an imbalanced dataset**|**Model with a balanced dataset**|
|:---|:---|:---|
|train_score|0.959|0.962|
|test_score (accuracy score)|0.922|0.923|

6. Lemmatization was done in an attempt to further improve the accuracy score on the balanced dataset but the model performed worse.
> Thus, the model with lemmatization was not optimised.

|**Metrics**|**Model without lemmatization**|**Model with lemmatization**|
|:---|:---|:---|
|train_score|0.909|0.907|
|test_score|0.893|0.889|

- The best model is therefore one with TfidfVectorizer and LinearSVC with a balanced dataset, based on the `accuracy` metric.

- Moving forward, the airline company can use this model to classify new queries to the correct channel on the chatbot or to the relevant customer support agent.
- The project can also be further extended to a multiclass classification model if the airline company wants to direct the query to a more specific channel.
- Sentiment analysis can also be conducted using the text data scraped to help the airline company identify its strengths and weaknesses, so that appropriate intervention steps can be implemented to improve its reputation.

---

### Limitations
- As the text data was scraped from a forum mainly contributed by Singapore residents, there is the presence of 'Singlish' in the corpus and not being removed through 'English' stopwords removal. However, this is addressed through GridSearch if 'Singlish' is very much prevalent. 
- Under the 'Catering' fourm, the posts are mainly informational instead of queries, thus the machine learning algorithm might not be able to classify questions related to catering well.