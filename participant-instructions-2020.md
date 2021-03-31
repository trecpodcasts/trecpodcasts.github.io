# TREC 2020 Podcasts Track Guidelines
Guidelines V1.1, Aug 5th, 2020

## Coordinators

Ann Clifton
Sravana Reddy
Jussi Karlgren
Yongze Yu
Aasish Pappu
Ben Carterette
Jen McFadden
Gareth Jones
Maria Eskevich 
Rosie Jones

## Motivation

Podcasts are a rapidly growing medium for news, commentary, entertainment, and learning.  Some podcast shows release new episodes on a regular schedule (daily, weekly, etc); others irregularly.  Some podcast shows feature short episodes of 5 minutes or less touching on one or two topics; others may release 3+ hour long episodes touching on a wide range of topics.  Some are structured as news delivery, some as conversations, some as storytelling.
High-quality search of the actual content of podcast episodes is currently not possible.  Existing podcast search engines index what metadata fields they find for the podcast as well as textual descriptions of the show and each episode. These descriptions often fail to cover the salient aspects of the content of the episode.  Podcast search is further limited by the availability of transcripts and the cost of automatic speech recognition.
This track will provide tasks, data, and evaluation measures for building next-generation search engines and summarization methodologies for podcasts of all types.
### Task 1: Fixed-length Segment Retrieval 
Given an arbitrary query (a phrase, sentence or set of words), retrieve relevant two-minute segments from the data. A segment is a two-minute chunk starting on the minute; e.g. [0.0-119.9] seconds, [60-199.9] seconds, [120-139.9] seconds, etc.
#### Topics for Task 1
Topics will consist of a topic number, keyword query, and a description of the user’s information need.  For example:
<topic>
<num>1</num>
<query>Higgs boson</query>
<description>I’m looking for news and discussion about the discovery of the Higgs boson. When was it discovered? How? Who was involved? What are the implications of the discovery for physics?</description>
</topic>
#### Assessment and Evaluation: Task 1

Two-minute length segments will be judged by NIST assessors for their relevance to the topic description.  NIST assessors will have access to both the ASR transcript (including text before and after the text of the two-segment, which can be used as context) as well as the corresponding audio segment.  Assessments will be made on the PEGFB graded scale (Perfect, Excellent, Good, Fair, Bad) as approximately follows:
* Perfect (4): this grade is used only for "known item" and "refinding" topic types.  It reflects the segment that is the earliest entry point into the one episode that the user is seeking.
* Excellent (3): the segment conveys highly relevant information, is an ideal entry point for a human listener, and is fully on topic.  An example would be a segment that begins at or very close to the start of a discussion on the topic, immediately signalling relevance and context to the user.
* Good (2): the segment conveys highly-to-somewhat relevant information, is a good entry point for a human listener, and is fully to mostly on topic.  An example would be a segment that is a few minutes “off” in terms of position, so that while it is relevant to the user’s information need, they might have preferred to start two minutes earlier or later.
* Fair (1): the segment conveys somewhat relevant information, but is a sub-par entry point for a human listener and may not be fully on topic.  Examples would be segments that switch from non-relevant to relevant (so that the listener is not able to immediately understand the relevance of the segment), segments that start well into a discussion without providing enough context for understanding, etc.
* Bad (0): the segment is not relevant.

The primary metric for evaluation will be mean nDCG, with normalization based on an ideal ranking of all relevant segments.  Note that a single episode may contribute one or more relevant segments, some of which may be overlapping, but these will be treated as independent items for the purpose of nDCG computation.  We expect to assess the relevance of a pool of the top 5-10 segments for each topic, depending on the number of participating teams and systems.

We plan to experiment with other metrics as well, e.g. metrics based on aggregating relevant segments within episodes, overlapping relevant segments, etc., but none of these will be used as primary metrics for reporting results.

Submission format: ad hoc podcast segment retrieval

Submissions for the ad hoc retrieval task should be in standard TREC 6-column format.

TOPICID   Q0   EPISODEID_OFFSET   RANK   SCORE   RUNID

TOPIC is the unique topic number.  A submission should include at least one result for every topic in the test set.
Q0 contains the static string “Q0”.  No information is contained in this column.
The EPISODEID_OFFSET column is the unique identifier for the retrieved segment.  It must consist of an episode URI (unique identifier) concatenated with an offset in seconds to the start of the segment, separated by an underscore character “_”.  The offset must be a multiple of 60 with one decimal place, e.g. “120.0”.  Each entry in this column must be unique to the topic ID.
RANK is the rank at which the segment has been retrieved.
SCORE is the system score for the segment.
RUNID is a unique identifier for the participant and submitted run.

Participants may submit up to 5 runs, each a separate 6-column file consisting of ranked results for all topics in the test set.  Participants are asked to return a ranked list of at most 1,000 segments for each topic. 

Example submission

1  Q0  spotify:episode:000A9sRBYdVh66csG2qEdj_120.0  1  67.2  myrun1
1  Q0  spotify:episode:3ZUU9IO0V8kaZaUPD6qqDY_540.0  2  65.8  myrun1
…
1  Q0  spotify:episode:3ZUU9IO0V8kaZaUPD6qqDY_360.0  1000  12.2  myrun1
2  Q0  spotify:episode:000HP8n3hNIfglT2wSI2cA_60.0  1  87.8  myrun1
… 

## Task 2: Summarization

Given a podcast episode, its audio, and transcription, return a short text snippet capturing the most important information in the content. Returned summaries should be grammatical, standalone utterances of significantly shorter length than the input episode description. 

The user task is to provide a short text summary that the user might read when deciding whether to listen to a podcast. Thus the summary should accurately convey the content of the podcast, and be short enough to quickly read on a smartphone screen. It should also be human-readable. 

### Evaluation Set for Summarization
The evaluation set will be created from a set of 500 held-out episodes which will be used to test the summarization systems. These episodes will be held out from the initial data release in April, and will be provided later in the task. 

Labeled summaries will be created for these episodes in two ways:

#### Golden set pool 1

Creator-provided podcast episode descriptions will be judged by assessors who have read the entire transcript. The judgements will be on an EGFB (Excellent, Good, Fair, Bad) scale  as approximately follows:
* Excellent: the summary accurately conveys all the most important attributes of the episode, which could include topical content, genre, and participants.  It contains almost no redundant material which isn’t needed when deciding whether to listen.
* Good: the summary conveys most of the most important attributes and gives the reader a reasonable sense of what the episode contains. Does not need to be fully coherent or well edited. It contains little redundant material which isn’t needed when deciding whether to listen.
* Fair: the summary conveys some attributes of the content but gives the reader an imperfect or incomplete sense of what the episode contains.  It may contain some redundant material which isn’t needed when deciding whether to listen.
* Bad: the summary does not convey any of the most important content items of the episode or gives the reader an incorrect sense of what the episode contains. It may contain a lot of redundant information that isn’t needed when deciding whether to listen to the episode.

The pool will be filtered down to the subset that have been judged to be excellent. Evaluation on this subset of the labels is analogous to predicting the creator-provided episode description, in the subset of episodes where the description is high quality.

#### Golden set pool 2

Automatically-generated summaries produced by participants for a same set of podcasts. They will be given relevance assessments (on an EFGB scale) by assessors. The pool will be filtered down to the subset that have been judged to be excellent (on an EGFB scale).

The test set will be selected to have qualified descriptions which will be used as the standard to which the submitted summaries will be compared. Submitted summaries will be judged on a four-step scale (EGFB) intended for a listener to be able to make a decision whether to listen to a podcast or not, conveying a gist of what the user should expect to hear listening to the podcast. This first year, they will not be expected to include assessment for style, format, or other aesthetic or non-topical qualities.

### Examples of creator-provided episode summaries: 
“Amongst the smoldering rubble of a prediction gone wrong, Mike and his guests talk about the Trump upset, how it happened , how it was missed by nearly everyone and what the future of the GOP will be under President Donald J Trump. With special guests David Hill and Bill Kristol”

“Substance Abuse Speaker Tony Hoffman shows how Clear vision sets the course, Real Action Multiplies Potential, and Belief in one's gifts can lead to redemption and a Championship Life! In this Episode you will learn: Why it is important to Just SAY NO! The difference between Micro and Macro Habits How to put a plan in ACTION Why it is important to have CLARITY on what you want  Why it is not really all about YOU!"

### Task input for Task 2 - podcast episode summarization
The input is a podcast episode - participants may use the provided transcript or the raw audio, not including information in the RSS headers. Information in the RSS header for the episode should not be considered. A test set of 500 episodes in the same format as the main data set will be provided in June 2020. We will provide RSS headers, audio files, and transcripts in the same format as in the collection provided in April 2020.

### Assessment and evaluation Task 2 - podcast episode summarization
Returned summaries should be grammatical, standalone utterances of significantly shorter length than the input episode. NIST assessors will assess the submitted summaries using the above EGFB scale for conveying gist of what the user should expect to hear listening to the podcast: the use case we have in mind is that of a potential listener exploring the podcast catalog to find episodes of interest. This first year, the assessors will not directly take readability or other aesthetic qualities of the summary into account; neither will they score the summaries for brevity. 

We expect the description of the use case, possible extensions or specifications of it, and attendant refinements to the assessment procedure to be a topic of discussion at the TREC session in November. 

The test set will be selected to have useful episode descriptions provided by episode creators. We will compare the submitted summaries to those episode descriptions. This first year we will experiment with several additional evaluation metrics, intending to explore the possibility of moving to fully automatic evaluation in coming years. We expect this also to be a topic of discussion at the TREC session in November. 

Primary metric for podcast episode summarization: ROUGE. We will use standard flavors of ROUGE, including unigram and bigram ROUGE-F. We plan to experiment with other metrics, including an embedding based metric and a reference-free metric. In a secondary evaluation emulating the experience on a mobile phone screen, we will limit the evaluation to the first 200 characters of the system-provided summary.
### Submission format: summarization task

A run will comprise exactly one file per summary, where the name of each summary file is the ID of the episode it is intended to represent, with the suffix “_summary.txt” appended. Please include a file for a summary, even if your system happens to produce no output for that episode. Each file will be read and assessed as a plain text file, so no special characters or markups are allowed. Organise the summary files in a directory structure identical to the one the test files were given in, with a top level directory whose name should be the concatenation of the Team ID and a number (1 to N) for the run. (For example, if the Team ID is "SYSX'' then the directory name for the first run should be "SYSX1".) Please package the directory in a tarfile and gzip the tarfile before submitting it to NIST.

## Dataset

Info about the podcast dataset can be found in the README associated with this track.

## Timeline
Document collection released
April 16th, 2020
Guidelines released
May 14th, 2020
Sample topics and qrels released
May 22nd, 2020
Test topics and episodes to summarize released
June 12th, 2020
Runs due
Thursday, Sept 3, 2020
Results released to participants
Early October, 2020


Note: Participants must register to submit.  The dissemination form must be returned to submit runs.

## TREC Podcasts 2020 Track Organizers


Ann Clifton, Spotify
Sravana Reddy, Spotify
Yongze Yu, Spotify
Aasish Pappu, Spotify
Jussi Karlgren, Spotify
Ben Carterette, Spotify
Jen McFadden, Spotify
Gareth Jones, Dublin City University
Maria Eskevich,  CLARIN ERIC
Rosie Jones, Spotify


