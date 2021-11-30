# 2021 TREC Podcasts Track

The Podcasts Track at the [Text Retrieval Conference (TREC)](https://trec.nist.gov) is intended to encourage research in podcast retrieval and access by researchers from the information retrieval, the NLP, and the speech analysis fields. The track which was first organised in 2020 continued with small modifications in 2021 will not run in 2022 but will explore a potential modified new launch in 2023.  In the meanwhile, the [CHIIR workshop on Audio Collection Human Interaction](https://speechretrievalworkshop.github.io/) welcomes participants with ideas about the use cases and usage situations of podcast material!


## Dataset

The core data for the challenge is the Spotify English-language Podcast Dataset, [available here](https://podcastsdataset.byspotify.com/) for non-commercial use.

## Tasks

The Podcasts Track has two challenge tasks: segment retrieval and podcast episode summarization.

### Task 1: Segment retrieval

Given a query, retrieve relevant two-minute segments from the data. A segment is a two-minute chunk starting on the minute; e.g. [0.0-119.9] seconds, [60-179.9] seconds, [120-239.9] seconds, etc. The two-minute segments are judged manually by NIST assessors for their relevance to the query, using both the transcript of the podcast as well as the corresponding audio segment.  Assessments were made on a graded scale of Perfect, Excellent, Good, Fair, Bad. (The Perfect score pertains only to queries with a given target item.)

In 2020 there were three types of queries: topical, known-item, and refinding queries. In 2021 the refinding queries and the known-item queries were combined, and add non-topical target notions, to get participants to find segments that are _entertaining_, _opinionated_, and contain _discussion_. 

* [2020 Participant Guidelines](participant-instructions-2020.md)  
* [2021 Participant Guidelines](participant-instructions-2021.md)  

#### Resources

* Search topics for the 2020 segment retrieval task
    * [train set (queries 1-8)](https://trecpodcasts.github.io/resources/podcasts_2020_topics_train.xml)
    * [test set for 2020 (queries 9-58)](https://trecpodcasts.github.io/resources/podcasts_2020_topics_test.xml)
    * [test set for 2021 (queries 59-108)](https://trecpodcasts.github.io/resources/podcasts_2021_topics_test.xml)
* Relevance assessments ("qrels")
    * [train set](https://trecpodcasts.github.io/resources/2020_train_qrels.list)
    * [2020 test set](https://trecpodcasts.github.io/resources/2020_test_qrels.list)
    * [2021 test set](https://trecpodcasts.github.io/resources/2021_test_qrels.list)
   
### Task 2: Summarization

Given a podcast episode, its audio, and its transcription, return a short text snippet capturing the most important information in the content. Returned summaries should be grammatical, standalone utterances of significantly shorter length than the input episode description. The quality of the summary is assessed manually by NIST assessors on a graded scale of Excellent, Good, Fair, Bad and via the standard Rouge metric compared to creator-provided descriptions of their episodes. 

In 2020, the objective for the task was "*to provide a short text summary that a user might read when deciding whether to listen to a podcast. The summary should accurately convey the content of the podcast, be human-readable, and be short enough to be quickly read on a smartphone screen.*" 

In 2021 the objective was very slightly reworded to give more guidance to participants as to what type of summary we are looking for and the participants were asked to submit an audio clip to give the listener a sense of what the episode sounds like. 

* [2020 Participant Guidelines](participant-instructions-2020.md)  
* [2021 Participant Guidelines](participant-instructions-2021.md) 

#### Resources

* Submitted summaries from the 2020 edition can be found in the data set directory. 

## Reports

An overview of the 2020 edition of the track is given in

* Rosie Jones, Ben Carterette, Ann Clifton, Maria Eskevich, Gareth J. F. Jones, Jussi Karlgren, Aasish Pappu, Sravana Reddy, and Yongze Yu. 2020. [*TREC 2020 Podcasts Track Overview.*](https://github.com/trecpodcasts/trecpodcasts.github.io/blob/gh-pages/documents/TREC_2020_Podcasts_Track__Tasks_overview.pdf) Proceedings from the 29th Text Retrieval Conference (TREC). NIST.

A first version of the 2021 edition of the track is given in

* Rosie Jones, Ben Carterette, Ann Clifton, Maria Eskevich, Gareth J. F. Jones, Jussi Karlgren, Aasish Pappu, Sravana Reddy, and Yongze Yu. 2020. [*TREC 2020 Podcasts Track Overview.*](https://github.com/trecpodcasts/trecpodcasts.github.io/blob/gh-pages/documents/TREC_2021_Podcasts_Track__Tasks_overview-NOTEBOOK.pdf) (Notebook version: final version to appear in the TREC proceedings in early 2022)

Reports from the individual participants can be found from the TREC website

* [TREC 2020 publications](https://trec.nist.gov/pubs/trec29/trec2020.html)

## Organisers

### 2020


* Ann Clifton, Spotify
* Sravana Reddy, Spotify
* Yongze Yu, Spotify
* Aasish Pappu, Spotify
* Jussi Karlgren, Spotify
* Ben Carterette, Spotify
* Jen McFadden, Spotify
* Gareth Jones, Dublin City University
* Maria Eskevich,  CLARIN ERIC
* Rosie Jones, Spotify


### 2021

* Ben Carterette, Spotify
* Ann Clifton, Spotify
* Maria Eskevich,  CLARIN ERIC
* Gareth F. Jones, Dublin City University
* Rosie Jones, Spotify
* Jussi Karlgren, Spotify
* Sravana Reddy, Spotify
* Md Iftekhar Tanveer, Spotify



