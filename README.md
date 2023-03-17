# Youtube_Category_Predictor
Is it possible to build an accurate model to predict/autogenerate category tags based on sparse user data? 

CSV files are located here https://drive.google.com/file/d/1w-S_nxqNxHIAbKK-B5_1R9bagUSoFufV/view?usp=sharing

# Failure as an investment in future success

Going into this project I read numerous methods that would probably render better results. It is however a very real and practical problem websites face or have faced. It was not my goal to definitively prove my hypothesis, but to explore the various weaknesses in the models so that I might better understand how they works and what the strengths and weaknesses are when approaching problems in the future. Often times in education on topics the ideal solutions are focused on answers handed over rather than the building up of options from a historical perspective. Following a path that winds through past failures is where many of the successes in ML have are found and without that I believe people loose perspective and intuition. This is undoubtedly a naive attempt at a complex problem. However, I acquired a far better understanding of NLP, Precision, Recall, F1, AUC/ROC evaluation metrics, and confusion matrices.

# Hypothesis

Google goes to great lengths to properly categorize Youtube videos correctly. Their algorithm uses a myriad of data and sentiment anaylisis techniques drawing upon the deep well of various information and other products they have in their wheel house. Since the barrier of entry has lowered into ML, it was my hypothesis that it may be possible to develop a method that may work as well with far less data neccesary solely relying on limited user generated data and powerful open source sklearn libraries.

This whitepaper describes how Google uses there data to accomplish similar tasks on Youtube: https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/41156.pdf written by Vinvent Simone of Gogle Paris.

# Results

The features kept in the models only accounted for user generated information at the time of video submission. These were 7 features ['channel_title', 'comments_disabled', 'ratings_disabled', 'category_names', 'title', 'description', 'tags']. By devining custom tags from the description that encompassed topic specific words from a bank as well as utilizing topic analysis via LDA I was able to reach promising AUC scores with Random Forest (72.5%) and a One vs All Linear Support Vector Machine. The LSVM resulted in an average AUC for each class of 80%!.
Where to go from here?

It would be advantageous to also further extened a word bank for each category denoting various labels as well as analyzing the thumbnail and video in a CNN. Although the results show it is possible categorize the videos with a fair degree of accuracy and precision the recall faltered below what I believe a production ready model would need.

# Content

This dataset includes several months (and counting) of data on daily trending YouTube videos. Data is included for the US, GB, CA (USA, Great Britain, Canada, respectively), with up to 200 listed trending videos per day. I chose to use only the English primary language sets due to UTF-8 parsing restrictions from the other languages.

Each region’s data is in a separate file. Data includes the video title, channel title, publish time, tags, views, likes and dislikes, description, and comment count.

The data also includes a category_id field, which varies between regions. To retrieve the categories for a specific video, find it in the associated JSON. One such file is included for each of the five regions in the dataset.

For more information on specific columns in the dataset refer to the column metadata. This dataset of the trending videos can be found at https://www.kaggle.com/datasnaek/youtube-new furnished by https://mitchelljolly.com/.
