
### Russian Bots (and a little bit of data science)

Maybe I spend a little too much time on Youtube and social media in general. And the desparate situation in Ukraine made me watch a lot of content related to the invasion of Ukraine: the Tucker-Putin-Interview, The Lex-Fridman-Tucker-Interview, reports from the front lines etc...

And then I noticed that a a lot of comments are Pro-Putin, Pro-War and desparately want Ukraine to lose and this didn't match the sentiment I get in day-to-day interaction with real people. And a lot of these comments were posted by usernames with four digits at the end.

So I thought, maybe I am biased or paranoid, and of course, a lot of people have four digits at the end of their username, representing important dates in their lives. Then I stumbled on this reddit post:

https://www.reddit.com/r/YUROP/comments/1b29m0g/prorussia_bots_always_end_with_4_digits_on_youtube/

Guess I'm not alone with that weird suspicion. But there's only one way to find out...

1. download the comments from Youtube using the Youtube Data API

2. analyze the data

Since I got the idea literally three hours ago and I am not an expert in NLP in general and sentiment classification in particular, and don't have access to a Transformer that could summarize the texts for me (maybe the content policies of GPT4 are also not that pleased if I ask them about bots and the war), I just used `spacy` (some NLP python package) to extract all adjectives and then computed the mean distance to the word in question (the target word could be "Russia" or "Ukraine" etc.)

The source data was collected using `comment-extraction.ipynb`. The urls of the Youtube videos and the resulting json files are available as well. The method and the results can be found in `data-analysis.iypnb`.
My results are based on 2122 potential bot comments (emphasis on the word **potential**, not everyone with their year of birth at the end of their username is a Russian bot)

**NOTE**: Take the results with a big grain of salt since my naive method doesn't consider context. For example, the sentence "Biden is not competent" would list "competent" as a word that is super close to "Biden" and that, of course, is misleading.

Do whatever you want with the findings and feel free to apply some more sophisticated techniques on your own :)# RussianBotsHypothesis
