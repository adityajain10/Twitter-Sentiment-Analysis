# Twitter-Sentiment-Analysis
This script performs sentiment analysis of any topic by parsing the tweets fetched from Twitter using Python.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.
### Prerequisites

#### Tweepy
Tweepy is the python client for the official Twitter API.
Install it using following pip command:
```
pip install tweepy
```

#### TextBlob
Textblob is the python library for processing textual data.
Install it using following pip command:
```
pip install textblob
```

#### NLTK corpora
Corpora is a large and structured set of texts.
```
python -m textblob.download_corpora
```


### Installing

```
git clone https://github.com/adityajain10/Twitter-Sentiment-Analysis/
```

### Authentication

In order to fetch tweets through Twitter API, register an App through a twitter account. Follow these steps for the same:

⋅⋅1. Open this [URL](https://twitter.com/login?redirect_after_login=https%3A%2F%2Fdeveloper.twitter.com%2Fapps) and click the button: ‘Create New App’
⋅⋅2. Fill the application details. You can leave the callback url field empty.
⋅⋅3. Once the app is created, you will be redirected to the app page.
⋅⋅4. Open the ‘Keys and Access Tokens’ tab.
⋅⋅5. Copy ‘Consumer Key’, ‘Consumer Secret’, ‘Access token’ and ‘Access Token Secret’.

