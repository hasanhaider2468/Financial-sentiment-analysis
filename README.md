# Financial-sentiment-analysis

Financial sentiment analysis is crucial for investors and businesses alike as it provides valuable insights into market trends and investor attitudes. By analyzing sentiments expressed in financial news, social media, and other sources, stakeholders can gauge the overall sentiment towards specific assets or markets. This information helps in making informed decisions regarding investment strategies, risk management, and market timing. Additionally, sentiment analysis enables the identification of emerging trends and sentiments that may impact financial markets, providing a competitive edge in a fast-paced and dynamic environment.

In this project, I seek to evaluate the sentiment analysis of several different texts regarding finance. I will be evaluating the impact of certain key terms of the overall polarity of sentences. Ideally figuring out what significant words in financial texts would intensify the polarity to be negative or positive and how sentiment analysis would be important in the financial realm.

# Data 
The data is a kaggle dataset containing 5842 entries of phrases, statements, articles, or any form of text regarding finance. Their are two columns which are the actual sentences and a sentiment associated with each one. https://www.kaggle.com/datasets/sbhatti/financial-sentiment-analysis

# Steps 

- Basic imports as well and uploading data into a dataframe.
- Sentence polarity determination:
    - Using the function "SentimentIntensityAnalyzer", the polarity scores for each sentence was determined.
    - Then, through merging dataframes, an overall dataframe was created which included information regarding the positive, negative, and neutral breakdowns of the sentence's polarity alongside the compound polarity, Sentence and pre-determined sentiment.
    
- Potential sentence subject recoginition:
    - By tokenizing each of these sentences and determining their part of speech through the function nltk.pos_tag(), I was able to determine all forms of nouns in each of these sentences.
    - By merging with previous dataframe, I now had information regarding the polarities, the actual sentence itself, and potential sentence subjects.
    ![Screenshot 2024-03-15 042609](https://github.com/hasanhaider2468/Financial-sentiment-analysis/assets/125958166/127428fe-7887-4485-8af2-564ec5fd91f2)

- Determination of Words with intense negative polarity
    - By finding all sentences with an overall compound polarity below -.4 
    - By splitting each sentence into its own token and determining the individual polarities of each term, I found the polarity of relatively intense negative words (words with a polarity of <= -.4)
    - This would then be added into its own sorted dataframe (smallest to largest negative polarity)
    ![Screenshot 2024-03-15 043127](https://github.com/hasanhaider2468/Financial-sentiment-analysis/assets/125958166/6ab9314f-79a1-4103-b60f-3b7b66c0a56c)

- Determination of Words with intense positive polarity
    - By finding all sentences with an overall compound polarity above .4 
    - By splitting each sentence into its own token and determining the individual polarities of each term, I found the polarity of relatively intense positive words (words with a polarity of >= .4)
    - This would then be added into its own sorted dataframe (smallest to largest positive polarity)
    ![Screenshot 2024-03-15 043419](https://github.com/hasanhaider2468/Financial-sentiment-analysis/assets/125958166/5aea2528-16e1-474a-84d6-531e224a84b1)

# Analysis and Result

I chose the value of -.4 and .4 as my filtering critera as I found this value satisifed two particular categories. The first was that this threshold ensured I did not exclusively retain words with extremely intense polarity. These words included words such as "kill", "cancer", and "disaster" for the negative polarities and words such as "best", "love", and "excellent" for the positive polarities. Although intense, these terms may not always help illustrate the proper image of the overall sentence polarity in a financial context. However, terms such as "decline", "crashes", and "boycotting" or terms such as "support", "approves", and "secured" (which were all terms with relatively lower polarity compared to terms such as cancer or best) would be more relavent in the financial world as meaningful terminology. Additionally, this filtering critera ensured I retained a sufficient amount of data. 

The way this could be utilized in a proper context is that by filtering through the dataframes using the potential subjects of the sentences, we can determine the general polarity of terms associated with that subject. In the financial realm, this could be looking at banks, stocks, investments, etc. and determining the overall trend associated with these subjects. As an example, we could look at a certain start-up company and examining what companies, research, or media are saying about this specific company. Suppose the overall polarity is negative which would mean there is a overall negative connotation associated with the company, meaning it may not be ideal to invest in this company.

