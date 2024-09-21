#documents
## Goal of the Thesis
<mark style="background: #FFF3A3A6;">Time: 30 seconds</mark>
- Comparative study between traditional search methods (Google Search) and conversational AI models (ChatGPT).
- Focus on children as primary targets.
- Aims to draw a comparative analysis between Google Search and ChatGPT.
- *Are the new conversational AI models better for children to interact with, or do the traditional search engine still hold an edge over the new technology.*
## Data Collection
<mark style="background: #FFF3A3A6;">Time: 30 seconds</mark>
- Using existing data collected from children
- Getting 1 result for ChatGPT
- Getting 5 results from Google

## Data Analysis
<mark style="background: #FFF3A3A6;">Time: 120 seconds</mark>
- ### Query Length Analysis
	- Compare the length of responses between Google Search and ChatGPT.
	- ChatGPT lengths vary much more based on the questions which are being asked.
	- Google lengths are more consistent showing that they are having consistent query lengths.
	- ChatGPT:
		- Max = 1321
		- Low = 81
		- Average = 343
	- Google:
		- Max = 162
		- Low = 132
		- Average = 151
- ### Named Entity Analysis (NER)
- ![[../../Attachments/Pasted image 20230630090946.png|750]]
	- Natural Language Processing Technique which involves identifying and classifying named entitles in text into different predefined categories.
	- Google had a higher average number of entities per search.
	- Top 5 entities were similar in both of them
	- `spacy`
- ### Sentiment Analysis
	- Looking at what sentiment does Google and ChatGPT results give.
	- Very similar results between each other.
	- Mostly all the results from ChatGPT and Google Search come in Neutral Sentiment
	- Rarely they have a considerable Negative or Neutral Sentiment, but that is more extreme in case of Google as compare to ChatGPT.
	- `nltk.sentiment`
- ### Similarity Analysis
	- **Cosine Similarity**
		- Spread out
		- Calculates the cosine of the angle between two vectors.
	- **Jaccard Similarity**
		- Sensitive to length of the response
		- Measures the proportion of common elements between two sets compared to the total number of distinct elements in both sets.
	- **Euclidean Similarity**
		- Sensitive to the outliers
		- measures the distance between two points in Euclidean space.
	- **Pearson Correlation**
		- Most spread out
		- Used `scipy.stats`

## Machine Learning Model
<mark style="background: #FFF3A3A6;">Time: 30 seconds</mark>
- Logistic Regression
- *Precision:* Ratio of true positives to the total number of predicted positives.
- *Recall:* Ratio of true positives to the total number of actual positives.
- *F1-Score:* Harmonic mean of precision and recall.
- *Support:* Number of occurrences of each class in the true labels.

## Conclusion & Results
<mark style="background: #FFF3A3A6;">Time: 45 seconds</mark>