{\rtf1\ansi\ansicpg1252\cocoartf1671\cocoasubrtf500
{\fonttbl\f0\fswiss\fcharset0 Helvetica;\f1\fmodern\fcharset0 Courier;}
{\colortbl;\red255\green255\blue255;\red0\green0\blue0;}
{\*\expandedcolortbl;;\cssrgb\c0\c0\c0;}
\paperw11900\paperh16840\margl1440\margr1440\vieww17940\viewh10320\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 I completed this project as part of my MSc requirements\
\pard\pardeftab720\sl280\partightenfactor0

\f1 \cf2 \expnd0\expndtw0\kerning0
------------------------------------------
\f0 \cf0 \kerning1\expnd0\expndtw0 \
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0
\cf0 \
*Problem exposition, motivation and understanding*\
\pard\pardeftab720\sl280\partightenfactor0

\f1 \cf2 \expnd0\expndtw0\kerning0
------------------------------------------
\f0 \cf0 \kerning1\expnd0\expndtw0 \
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0
\cf0 \
Over the last few years, the music industry has been dominated by digital streaming services, which produce vast amounts of data on listeners and their preferences. This has required major players in the industry to adopt a data driven approach to content delivery in order to stay competitive. Warner Music Group is looking to leverage its rich database to better understand the factors that have the most significant impact on the success of a new artist. This will allow them to optimise the allocation of resources when signing and promoting new artists.\
\
For this case study, I used a Spotify dataset to predict the success of artists. In particular, I wanted to understand the role of Spotify playlists on the performance of artists. This is informed by Warner Music Group\'92s findings that certain playlists have more of an influence on the popularity, stream count and future success of an artist than others. \
\
The hypothesis is that if Warner Music Group can predict which artists would appear on certain playlists that greatly influence popularity, stream count and future success of an artist *before* they actually appear on such playlists, they would be in an advantageous competitive position by signing such artists before Warner Music Group\'92s competitors do\
\
*Approach and Insights*\
\pard\pardeftab720\sl280\partightenfactor0

\f1 \cf2 \expnd0\expndtw0\kerning0
------------------------------------------
\f0 \cf0 \kerning1\expnd0\expndtw0 \
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0
\cf0 \
This project is framed as a supervised learning, classification task. The dependent variable is binary and showcases whether or not an artists appears on one or more key playlists. The independent variables and features include age of streamers, geography of streamers, source of streamers, stream count and so on.\
\
For visualisation, I created a multitude of graphs to get a better feel of the data. These graphs were mostly categorical in essence, as this was the nature of the pre-engineered dataset. I found, among other insights, the slight skew in terms of age for customers and the interesting omission of the most played playlists from the 4 target playlists. There was also a seasonal and weekly component to what songs/genres, and by extension what artists, were popular.\
\
The majority of the analysis related to feature engineering, since the raw data and features were not suited to ML algorithms. Features were divided into Artist, Playlist and User levels. In the first category, I created a measure of how passionate an artist's fans were through the measure of repeated streams, called 'Passion Score'. A similar feature was created for the second category. For the final category, I built a gender and age level audience profile per artist, to see if demographics had any major effect on predicting success.\
\
Next I prepared the data to be fed into an algorithm. Key tasks completed here included splitting the data, checking for correlations, executing PCA, filling missing values wand dealing with class balance. PCA was executed on region codes to incorporate a geographical aspect into predicting success and to extract the most important data from 600+ region codes. The first such principal component turned out to be the most powerful predictive feature. \
\
Additionally, class balance initially proved to be an issue, since there were many more unsuccessful cases than successful ones in our data, especially after the training-test split. To overcome this, I oversampled the successful cases (in only training set) and included the necessary caveats that this oversampling entailed.\
\
A search for the best-performing model followed, followed by extensive evaluation. Decision Trees and Random Forests were found to be the best performing in terms of cross-validation scores. I choose the latter in tuning hyperparameters via grid search, and ended with a cross-validation score of 97%. Further attempts to using ensemble methods with my model (which by itself, of course, is an ensemble method) with AdaBoost yielded large decreases in performance, so such methods were not considered going forward.\
\
*Results*\
\pard\pardeftab720\sl280\partightenfactor0

\f1 \cf2 \expnd0\expndtw0\kerning0
------------------------------------------
\f0 \cf0 \kerning1\expnd0\expndtw0 \
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0
\cf0 \
Testing my model on the hold-out set resulted in an accuracy of 87%, which is good but not great, as it can still lead to WarnerMusic missing out on potentially successful artists. I believe the reason why the model cannot break the 90% barrier is the very small hold-out set size, with even fewer successful cases. My Confusion Matrix seems to confirm this. Oversampling was not executed on this hold-out set. Using ROC, the area under the curve is 78%, while the most important features are geographical (first principal component), number of unique streamers per artist and % of youth streamers. Thus, if an artist is popular among a multitude of young streamers, they are more likely to be successful.\
\
\
*How to run this project*\
\pard\pardeftab720\sl280\partightenfactor0

\f1 \cf2 \expnd0\expndtw0\kerning0
------------------------------------------\
\
- Download the Jupyter notebook\
- Download the data files named cleaned_data.csv, newartists2015onwards.csv and playlists_ids_and_titles.csv\
- Ensure you import all the required modules. The code for this is already present in the Notebook but a full list of the imports can be found in the requirements.txt file\
- Change paths to load the data from your local machine once you have downloaded the data files mentioned in point 2\
- Run the whole Jupyter Notebook
\f0 \cf0 \kerning1\expnd0\expndtw0 \
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0
\cf0 \
\
\
}