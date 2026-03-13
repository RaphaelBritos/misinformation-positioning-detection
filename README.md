# misinformation-positioning-detection

Overview

This repository contains the code and methodology for detecting misinformation in tweets. The approach leverages verified news from fact-checking agencies as seeds and propagates labels to unlabeled tweets based on TF-IDF text similarity. The project was developed as part of the PDPD (Pesquisando desde o Primeiro Dia) undergraduate research program.

Methodology

The methodology follows several key steps:

1. Data Collection

Tweets were collected from Twitter (X) using the Twitter API v2.

Focused on posts related to the 2022 Brazilian elections, including terms such as ‘urna’, ‘urnas’, ‘eleição’, ‘voto impresso’, and ‘auditável’.

Retweets without comments were prioritized to analyze direct dissemination of content.

2. Preprocessing

Data was cleaned to remove noise, duplicates, irrelevant content, links, emojis, hashtags, and reserved words.

Texts were tokenized and normalized for analysis, with stopwords and very short words removed.

Duplicate tweets were removed to ensure dataset quality.

3. Identification of Verified Misinformation

Posts verified by fact-checking agencies (Lupa, Estadão Verifica, Fatos ou Fakes, Aos Fatos) were selected.

Keywords from these posts were extracted to build a dictionary of disinformation terms.

Each tweet was manually reviewed and labeled as either containing disinformation or not.

4. TF-IDF and Label Propagation

A TF-IDF matrix was computed for both labeled and unlabeled tweets.

For each unlabeled tweet, the cosine similarity to labeled tweets was calculated.

Tweets with similarity above a threshold (t = 0.9) were automatically assigned the label of the most similar verified tweet.

Tweets below the threshold were marked as -1 (unlabeled).

5. Analysis of Dissemination Patterns

Users with high retweet activity were identified as influential in spreading misinformation.

Clustering and topic modeling (using BERTopic, UMAP, HDBSCAN) were applied to detect groups of users with similar content sharing behaviors.

Keywords and frequent terms were analyzed to characterize the content shared within each cluster.

Features

Seed-based detection: Uses verified news as initial seeds to identify misinformation.

Automatic labeling: Propagates labels to similar tweets using TF-IDF and cosine similarity.

Influence analysis: Identifies users contributing most to disinformation dissemination.

Topic modeling: Highlights clusters and prevalent topics within tweet data.
