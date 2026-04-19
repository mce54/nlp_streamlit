import streamlit as st
import nltk
from nltk.stem.wordnet import WordNetLemmatizer
from textblob import TextBlob
import re

nltk.download('wordnet')
nltk.download('omw-1.4')

lemmatizer = WordNetLemmatizer()

def clean_text(text):
    text = text.lower()
    text = re.sub(r'[^a-zA-Z\s]', '', text)
    words = text.split()
    words = [lemmatizer.lemmatize(word) for word in words]
    return " ".join(words)

def predict_sentiment(text):
    cleaned = clean_text(text)
    analysis = TextBlob(cleaned)
    polarity = analysis.sentiment.polarity

    if polarity > 0:
        return "Positive", polarity
    elif polarity < 0:
        return "Negative", polarity
    else:
        return "Neutral", polarity

st.title("NLP Sentiment Analysis App")

user_input = st.text_area("Enter your text here:")

if st.button("Analyze Sentiment"):
    sentiment, score = predict_sentiment(user_input)

    st.write("Sentiment:", sentiment)
    st.write("Polarity Score:", score)

    
#2

st.title("NLP Sentiment Analysis App")

st.subheader("Enter text below for sentiment analysis")

user_input = st.text_area("Type your text here:")

if st.button("Analyze"):
    sentiment, polarity = predict_sentiment(user_input)

    st.subheader("Results")
    st.write("Sentiment:", sentiment)
    st.write("Polarity:", polarity)

 #3A
def clean_text(text):
    # Keeping only Text and digits
    text = re.sub(r"[^A-Za-z0-9]", " ", text)

    # Removes Whitespaces
    text = re.sub(r"\'s", " ", text)

    # Removing Links if any
    text = re.sub(r"http\S+", " link ", text)

    # Removes Punctuations and Numbers
    text = re.sub(r"\b\d+(?:\.\d+)?\s+", "", text)

    # Splitting Text
    text = text.split()

    # Lemmatizer
    lemmatizer = WordNetLemmatizer()
    lemmatized_words = [lemmatizer.lemmatize(word) for word in text]

    text = " ".join(lemmatized_words)

    return text

if st.button("Analyze", key="analyze_button"):
    cleaned_text = clean_text(user_input)
    blob = TextBlob(cleaned_text)
    result = blob.sentiment.polarity

    if result > 0:
        custom_emoji = ":blush:"
        st.success("Positive sentiment {}".format(custom_emoji))
    elif result < 0:
        custom_emoji = ":disappointed:"
        st.warning("Negative sentiment {}".format(custom_emoji))
    else:
        custom_emoji = ":confused:"
        st.info("Neutral sentiment {}".format(custom_emoji))

    st.success("Polarity Score is: {}".format(result))
