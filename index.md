# 2021 TREC Podcasts Track

The Podcast Track at the [Text Retrieval Conference (TREC)](https://trec.nist.gov) is intended to encourage research in podcast retrieval and access by researchers from the information retrieval, the NLP, and the speech analysis fields. The track which was first organised in 2020 will continue with small modifications in 2021. 

## 2020 Edition

In 2020 the participants addressed two tasks: segment retrieval and podcast episode summarisation. An overview of the 2020 edition of the track is given in

Rosie Jones, Ben Carterette, Ann Clifton, Maria Eskevich, Gareth J. F. Jones, Jussi Karlgren, Aasish Pappu, Sravana Reddy, and Yongze Yu. 2020. [*TREC 2020 Podcasts Track Overview.*](https://github.com/trecpodcasts/trecpodcasts.github.io/blob/gh-pages/documents/TREC_2020_Podcasts_Track__Tasks_overview.pdf) Proceedings from the 29th Text Retrieval Conference (TREC). NIST.

### Task 1 in 2020: Segment retrieval

Given a query, retrieve relevant two-minute segments from the data. A segment is a two-minute chunk starting on the minute; e.g. [0.0-119.9] seconds, [60-199.9] seconds, [120-139.9] seconds, etc. The two-minute segments were judged manually by NIST assessors for their relevance to the query.  NIST assessors used both the transcript of the podcast (including text before and after the text of the two-segment, which could be used by them as context) as well as the corresponding audio segment.  Assessments were made on a graded scale of (Perfect, Excellent, Good, Fair, Bad).

### Task 2 in 2020: Summarisation

Given a podcast episode, its audio, and transcription, return a short text snippet capturing the most important information in the content. Returned summaries should be grammatical, standalone utterances of significantly shorter length than the input episode description. The user task was to provide a short text summary that a user might read when deciding whether to listen to a podcast. The summary should accurately convey the content of the podcast, be human-readable, and be short enough to be quickly read on a smartphone screen. 

## Dataset

The core data for the challenge is the Spotify English-language Podcast Dataset, 
[available here](https://podcastsdataset.byspotify.com/) for non-commercial use.

## Resources

- Search topics for the 2020 segment retrieval task [train set](https://trecpodcasts.github.io/resources/podcasts_2020_topics_train.xml) [test set](https://trecpodcasts.github.io/resources/podcasts_2020_topics_test.xml)
- Relevance assessments for the 2020 segment retrieval [train set](https://trecpodcasts.github.io/resources/2020_train_qrels.list) [test set](https://trecpodcasts.github.io/resources/2020_test_qrels.list)

## Organisers

Ben Carterette, Ann Clifton, Maria Eskevich, Gareth J.F. Jones, Rosie Jones, Jussi Karlgren, Sravana Reddy, Md Iftekhar Tanveer


