# Sentiment Analysis of Yelp Reviews (Scraped)
<div align="right"><i>Year: 2021</i></div>
<img src="https://user-images.githubusercontent.com/32619706/159832978-6a29e029-822f-4319-b89e-eb03e3854376.png">
Performed sentiment analysis of reviews extracted through scraping Yelp for a sample of restaurants in Toronto.


## Data Collection & Objective
Though we could think of using Yelp's Fusion API for the review text, it comes with a significant limitation for a data-hungry model to reach its peak potential: it only displays the first one or two sentences of a review, truncating the rest with an ellipsis at the end. Possibly, the way Yelp intended the API to be used was for the application developer to use the included reviews[x].url field to redirect the end-user to a web page containing the rest of the review. 

<img src="https://user-images.githubusercontent.com/32619706/159834570-73017895-fc85-402c-9a96-68728456030e.png">

Thus, we will crawl the rest of the Yelp website with the help of BeautifulSoup to amass the best training data set for our task that we can. The scope of the project is not to model an advanced classifier, but purely to use it as a litmus test for the quality of the data set extracted through on a simple model, such as Naive Bayes. The goal is to extract as large and as rich a training set for this simple model as we can.

## Data Pre-Processing
The input the model is a list of tuples, with the first element of each representing a natural-language review of a restaurant, and the second element representing the sentiment of the review, i.e., either 'positive' or 'negative', which is inferred by the star rating returned by the API for that review. Sample shown below; note that the reviews have been truncated for display purposes.

<img src="https://user-images.githubusercontent.com/32619706/159835126-c6e03d6d-2e04-4f75-95cf-cb40e258e3ec.png">

## Results
Though a single API request fetches a maximum of 50 reviews, we were able to use pagination with HTML parser to have a larger training dataset. Through this, even the simple Naive Bayes Classifier gave an accuracy of 97.28%, which served well enough as a proof-of-concept in our case.
