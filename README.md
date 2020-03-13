# Twitter-Sentiment-Analysis
This script performs sentiment analysis of any topic by parsing the tweets fetched from Twitter using Python.

## Table of content

- [Development setup](#Development-setup)
    - [Prerequisites](#Prerequisites)
    - [Installation](#Installation)
    - [Authentication](#Authentication)
- [Sample Output](#Sample-Output)
- [How It Works](#How-It-Works)
- [Links](#links)

## Development setup

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


### Installation

```
git clone https://github.com/adityajain10/Twitter-Sentiment-Analysis/
```

### Authentication

In order to fetch tweets through Twitter API, register an App through a twitter account. Follow these steps for the same:

* Open this [URL](https://twitter.com/login?redirect_after_login=https%3A%2F%2Fdeveloper.twitter.com%2Fapps) and click the button: ‘Create New App’
* Fill the application details. You can leave the callback url field empty.
* Once the app is created, you will be redirected to the app page.
* Open the ‘Keys and Access Tokens’ tab.
* Copy ‘Consumer Key’, ‘Consumer Secret’, ‘Access token’ and ‘Access Token Secret’.

Positive tweets percentage: 22 %
Negative tweets percentage: 15 %

## Sample Output
```
Positive tweets:
RT @JohnGGalt: Amazing—after years of attacking Donald Trump the media managed
to turn #InaugurationDay into all about themselves.
#MakeAme…
RT @vooda1: CNN Declines to Air White House Press Conference Live YES! 
THANK YOU @CNN FOR NOT LEGITIMI…
RT @Muheeb_Shawwa: Donald J. Trump's speech sounded eerily familiar...
POTUS plans new deal for UK as Theresa May to be first foreign leader to meet new 
president since inauguration 
.@realdonaldtrump #Syria #Mexico #Russia & now #Afghanistan. 
Another #DearDonaldTrump Letter worth a read @AJEnglish 


Negative tweets:
RT @Slate: Donald Trump’s administration: “Government by the worst men.” 
RT @RVAwonk: Trump, Sean Spicer, et al. lie for a reason. 
Their lies are not just lies. Their lies are authoritarian propaganda.  
RT @KomptonMusic: Me: I hate corn 
Donald Trump: I hate corn too
Me: https://t.co/GPgy8R8HB5
It's ridiculous that people are more annoyed at this than Donald Trump's sexism.
RT @tony_broach: Chris Wallace on Fox news right now talking crap 
about Donald Trump news conference it seems he can't face the truth eithe…
RT @fravel: With False Claims, Donald Trump Attacks Media on Crowd Turnout 
Aziz Ansari Just Hit Donald Trump Hard In An Epic Saturday NIght Live Monologue
```

## How It Works
We follow these 3 major steps in the program:

* Authorize twitter API client.
* Make a GET request to Twitter API to fetch tweets for a particular query.
* Parse the tweets. Classify each tweet as positive, negative or neutral.


* First, we create a TwitterClient class. This class contains all the methods to interact with Twitter API and parsing tweets. We use __init__ function to handle the authentication of API client.

* In get_tweets function, we use:
```
fetched_tweets = self.api.search(q = query, count = count)
```
to call the Twitter API to fetch tweets.

* In get_tweet_sentiment, textblob module is used.
```
analysis = TextBlob(self.clean_tweet(tweet))
```
TextBlob is actually a high level library built over top of NLTK library. 
First we call clean_tweet method to remove links, special characters, etc. from the tweet using some simple regex.
Then, as we pass tweet to create a TextBlob object, following processing is done over text by textblob library:



⋅⋅* Tokenize the tweet ,i.e split words from body of text.
⋅⋅* Remove stopwords from the tokens.(stopwords are the commonly used words which are irrelevant in text analysis like I, am, you, are, etc.)
⋅⋅* Do POS( part of speech) tagging of the tokens and select only significant features/tokens like adjectives, adverbs, etc.
⋅⋅* Pass the tokens to a sentiment classifier which classifies the tweet sentiment as positive, negative or neutral by assigning it a polarity between -1.0 to 1.0 .

Here is how sentiment classifier is created:

⋅⋅* TextBlob uses a Movies Reviews dataset in which reviews have already been labelled as positive or negative.
⋅⋅* Positive and negative features are extracted from each positive and negative review respectively.
⋅⋅* Training data now consists of labelled positive and negative features. This data is trained on a Naive Bayes Classifier.

Then, we use sentiment.polarity method of TextBlob class to get the polarity of tweet between -1 to 1.
Then, we classify polarity as:

```
if analysis.sentiment.polarity > 0:
       return 'positive'
elif analysis.sentiment.polarity == 0:
       return 'neutral'
else:
       return 'negative'
```

* Finally, parsed tweets are returned. Then, we can do various type of statistical analysis on the tweets. For example, in above program, we tried to find the percentage of positive, negative and neutral tweets about a query.

## Links
* [Source code](https://github.com/adityajain10/Twitter-Sentiment-Analysis/blob/master/TwitterClient.py)
