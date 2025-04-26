import nltk
from nltk.sentiment import SentimentIntensityAnalyzer

# Download the VADER lexicon
nltk.download('vader_lexicon')

# Initialize the Sentiment Intensity Analyzer
sia = SentimentIntensityAnalyzer()

# Function to analyze sentiment
def analyze_sentiment(text):
    sentiment_scores = sia.polarity_scores(text)
    compound_score = sentiment_scores['compound']
  # Determine sentiment category
if compound_score >= 0.05:
    sentiment = "Positive"
elif compound_score <= -0.05:
    sentiment = "Negative"
else:
    sentiment = "Neutral"

return sentiment, sentiment_scores  

# Example social media conversations
social_media_texts = [
    "I love this product! Best purchase ever!",
    "This is terrible. I regret buying it.",
    "It's okay, but nothing special.",
    "Absolutely amazing experience!"
]

# Analyze sentiment of each post
for text in social_media_texts:
    sentiment, scores = analyze_sentiment(text)
    print(f"Text: {text}\nSentiment: {sentiment}\nScores: {scores}\n")
