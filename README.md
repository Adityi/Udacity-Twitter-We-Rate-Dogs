# Udacity-Twitter-We-Rate-Dogs
GATHER:
The data gathering was done from twitter_archive_enhanced.csv, from twitter api (I could not make
account, there was some network problem in my area and code could not be received to confirm phone
number) and from tab separated file image_predictions.tsv. The data gathering was
very challenging for me, but with the help of stckover flow and tutorials of
Udacity, I did it successfully.
ASSESS:
The assessment of data was done individually in three dataframes: df_twitter,
df_api and df_img. First lets discuss about df_twitter:
It was divided into two, quality issues and tidiness issues.
QUALITY ISSUES:
• in_reply_to_status_id count is positive, we need to deal with original tweets only.
• When checked through sample, it was found that the stages of dogs were mentioned in text,
but were missing from classification column.
• As per standard, rating_denominator should be 10, but when checked through
rating_denominator.value_counts, few rows have values not equal to 10.
• Few rows have numerator values very high, like 165/144 etc.
• There are many missing values.
• The dtype of time is string, should be changed to timestamp.
• The name and stage column have few values as None, hence isnull shows 0 null values.
• tweet_id is a integer, should be converted to object (string).

TIDYNESS ISSUES:
• The 4 category of the dogs should be in one column only, not 4 columns.
• Join df_api and df_twitter.
For df_img:
QUALITY ISSUES:
• The breeds of the dogs should be same case (either upper or all lower)
• Tweet_id to be converted to string.
• The columns names to be updated for better description
I could not find any tidiness issue in this dataframe.
For df_api: Nothing to change, just join it in df_twitter (tidiness issue).
CLEAN:
First a copy of all dataframes was created (to be on safe side, so that the original df is available).
Df_twitter and Df_api : Few columns in this df had missing dog_stage values, but when checked in text,
they were present. So using regular expressions, the various dog stages were extracted from the text,and then a common name was given according to category (Doggo, dogGo, Doggos etc as doggo only).
After this stage, df_twitter and df_api was combined based on tweet_id values.
After this the data type of relevant columns was changed, the rating_denominator value was set to 10
for those rows which had wrong values (other than 10).
All columns with in_reply_to_status_id not null were deleted.
The name and dog sates were changed from None to NULL.
The rating numerator values were extracted from text, still there were few ambiguous values which
were than considered as outliers.
The table was melted so that the 4 columns of 4 different categories can come in one column only.
Df_img: All dogs breed values were changed to lowercase, and columns names were updated.
