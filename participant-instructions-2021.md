# TREC 2021 Podcasts Track Guidelines
Guidelines V2.9, September 1, 2021

<span style="color:red"> The latest change is to make more explicit the format for an "Episode URI"</span>


## Task 1: Fixed-length Segment Retrieval 

Given a retrieval topic (a phrase, sentence or set of words) and a set of ranking criteria, retrieve and rank relevant two-minute segments from the data. A segment is a two-minute chunk starting on the minute; e.g. [0.0-119.9] seconds, [60-179.9] seconds, [120-239.9] seconds, etc. The lists of segments are to be submitted in four separately ranked lists. 


### Topics for the Fixed-length Segment Retrieval Task

Topics consist of a topic number, keyword query, a query type, and a description of the user’s information need. The query types in 2021 are "topical" and "known-item". 

The test topics for 2021 are found on the active participants' <a href="https://trec.nist.gov/act_part/tracks/podcast/podcasts_2021_topics_test.xml">site at NIST</a>. You need to <a href="">register for the track</a> to be able to access them.

### Topical queries

40 of the 50 segment retrieval queries are of this type.

```
<topic>
<num>3</num>
<query>black hole image</query>
<type>topical</type>
<description>In May 2019 astronomers released the first-ever picture of a black hole. I would like to hear some conversations and educational discussion about the science of astronomy, black holes, and of the picture itself.</description>
</topic>
```

#### Ranking criteria for topical queries

For topical queries, as in 2020, participants are asked to submit a ranked list of topically relevant segments for each query topic. In addition, this year we ask for three reranked lists of those same topically relevant segments. This means that for each query topic we expect four segment lists. For some queries the reranking may have little effect, which we look forward to studying after submissions are in. 

*  Adhoc topical retrieval: the segment is topically relevant to the topic description. 

*  Entertaining: the segment is topically relevant to the topic description AND the topic is presented in a way which the speakers intend to be amusing and entertaining to the listener, rather than informative or evaluative. 

*  Subjective: the segment is topically relevant to the topic description AND the speaker or speakers explicitly and clearly express a polar opinion about the query topic, so that the approval or disapproval of the speaker is evident in the segment.

*  Discussion: the segment is topically relevant to the topic description AND includes more than one speaker participating with non-trivial topical contribution (e.g. mere grunts, expressions of agreement, or discourse management cues ("go on", "right", "well, I don't know ..." etc) are not sufficient). 


#### Assessment of topical queries in the fixed-length segment retrieval task

The submitted two-minute length segments will be judged by NIST assessors for their topical relevance to the topic description and each relevant topic will also be assess for their adherence to the reranking criteria.  NIST assessors will have access to both the text transcript of the episode (including text before and after the text of the two-segment, which can be used as context) as well as the corresponding audio segment.  

For the adhoc submission, the assessments will be made on the PEGFB graded scale (Perfect, Excellent, Good, Fair, Bad) as follows:

* Excellent (3): the segment conveys highly relevant information, is an ideal entry point for a human listener, and is fully on topic.  An example would be a segment that begins at or very close to the start of a discussion on the topic, immediately signalling relevance and context to the user.
* Good (2): the segment conveys highly-to-somewhat relevant information, is a good entry point for a human listener, and is fully to mostly on topic.  An example would be a segment that is a few minutes “off” in terms of position, so that while it is relevant to the user’s information need, they might have preferred to start two minutes earlier or later.
* Fair (1): the segment conveys somewhat relevant information, but is a sub-par entry point for a human listener and may not be fully on topic.  Examples would be segments that switch from non-relevant to relevant (so that the listener is not able to immediately understand the relevance of the segment), segments that start well into a discussion without providing enough context for understanding, etc.
* Bad (0): the segment is not relevant.

For the three other criteria, the assessments will be made on a three grade scale as follows:
* Adhering (3): The segment is clearly intended to be entertaining, the segment is subjective; the segment contains multi-party discussion.
* Partial (1): The segment may be intended to be entertaining or the participants react with appreciation or glee which may or may not be due to entertainment value of statements in the segment; the segment contains subjective or evaluative language but its target topic may be unclearly delimited or due to some previously mentioned discourse topic; there are more than one participant and they contribute to the conversation but it remains unclear if they contribute to the topic or some other topic. 
* Non-adhering (0): The segment is not intended to be entertaining nor is interpreted as such by its participants; the segment does not express the speaker attitude vis-a-vis the topic; the segment does not involve multiple participants or only one speaker contributes to the topic. 


### Known-item queries

```
<topic>
<num>54</num>
<query>bias in college admissions</query>
<type>known item</type>
<description>I read an article that mentioned a podcast about bias in college admissions.  I would like to listen to it but I don’t know the name of the show.</description>
</topic>
```

#### Assessment of known-item queries in the fixed-length segment retrieval task

* Perfect (4): the segment is the intended item
* Bad (0): the segment is not intended item



### Evaluation Metric for fixed-length segment retrieval task

The primary metrics for evaluation will be nDCG at a cutoff of 30 documents, precision at 10, and nDCG over the entire ranked list. A single episode may contribute one or more relevant segments, some of which may be overlapping, but these will be treated as independent items for the purpose of nDCG computation.  We expect to assess at a pool depth of 10, meaning the top 10 segments for each ranked list. 

### Submission Format for the fixed-length segment retrieval task

Submissions for the ad hoc retrieval task should be in standard whitespace-delimited TREC 6-column format. 

<span style="color:red"> ***Note: the submission format has been changed in V2.5 of these instructions.***</span>


```
TOPICID   QTYPE   EPISODEID_OFFSET   RANK   SCORE   RUNID
```

* `TOPIC` is the unique topic number.  A submission should include at least one result for every topic in the test set.
* `QTYPE` distinguishes the four ranking criteria and should be one of "QR" (for the topical relevance ranking), "QE" (for the "entertaining" ranking), "QS" (for the "subjective" ranking), "QD" (for the "discussion" ranking). <i>This task marks the first time to our knowledge that this field is used functionally in a TREC track. </i>
* The `EPISODEID_OFFSET` column is the unique identifier for the retrieved segment.  It must consist of an episode URI (unique identifier) concatenated with an offset in seconds to the start of the segment, separated by an underscore character “_”.  The episode URI format is "spotify:episode:" followed by a 22-character string of letters and digits. The offset must be a multiple of 60 with one decimal place, e.g. “120.0”.  Each entry in this column must be unique to the topic ID.
* `RANK` is the rank at which the segment has been retrieved.
* `SCORE` is the system score for the segment.
* `RUNID` is a unique identifier for the participant and submitted run.



Participants may submit up to 4 runs. Each run should consist of a 6-column file consisting of ranked results for all topics in the test set of *at most* 1,000 segments for each topic. The QTYPE field is used to distinguish the various ranking criteria for each topic. 

Known-item topics are only to be submitted with the QR ranking, since the various reranking criteria are not applicable to them. The `RANK` field is not must be an ascending integer starting from 1, restarting for each ranking criterion. Note that the assessment will be made from the top of the ranked list to the pool depth which will be determined after submissions are in but is almost certain to be less than 100 and likely to be less than 50. 

Example submission

```
9 QR spotify:episode:3ZUU9IO0V8kaZaUPD6qqDY_360.0 1 121.2 myrun1
9 QR spotify:episode:000HP8n3hNIfglT2wSI2cA_60.0 2 87.8 myrun1
...
```

```
9 QS spotify:episode:0CDSmklC42307Ktg86ER7Y_840.0 1 87.98 myrun1
9 QS spotify:episode:000A9sRBYdVh66csG2qEdj_120.0 2 67.2 myrun1
...
```

```
9 QD spotify:episode:6O8djf3RL94yNfaoWqvk3r_840.0 1 4.82 myrun1
9 QD spotify:episode:6v0auT8BbeXzMTmg9FjyDB_1980.0 2 1.17 myrun1
...
```

```
9 QE spotify:episode:0bI9g00ZrF5VczfdkWds7a_2280.0 1 82.0 myrun1
9 QE spotify:episode:000HP8n3hNIfglT2wSI2cA_480.0 2 31.4 myrun1
...
```


### Timeline for segment retrieval task

* Document collection released: April 16th, 2020
* Sample topics and qrels released: March 31, 2021
* 2021 guidelines released: April 14th, 2021
* Test topics released: <strike>June 2021</strike> July 1, 2021
* Runs due: September 3, 2021
* Results released to participants: Early October, 2021


## Task 2: Summarization

The user task is to provide a short description of the podcast episode to *help the user decide whether to listen to a podcast*. This user task is the background for both the assessment of the text snippet and the audio clip.

Given a podcast episode, its audio, and transcription, return
* *a short text snippet* capturing the most important information in the content, in grammatical standalone utterances of significantly shorter length than the input episode description;
* *an audio file* of up to one minute duration selected from the podcast to give the user a sense of what the podcast sounds like. Limitations on the format of the audio file are yet to be determined. 

### Assessment criteria for the summarization task

The assessment and scoring of the text snippet will be done similarly as last year, on the EGFB (Excellent, Good, Fair, Bad) scale  as approximately follows:
* Excellent: the summary accurately conveys all the most important attributes of the episode, which could include topical content, genre, and participants.  It contains almost no redundant material which isn’t needed when deciding whether to listen.
* Good: the summary conveys most of the most important attributes and gives the reader a reasonable sense of what the episode contains. Does not need to be fully coherent or well edited. It contains little redundant material which isn’t needed when deciding whether to listen.
* Fair: the summary conveys some attributes of the content but gives the reader an imperfect or incomplete sense of what the episode contains.  It may contain some redundant material which isn’t needed when deciding whether to listen.
* Bad: the summary does not convey any of the most important content items of the episode or gives the reader an incorrect sense of what the episode contains. It may contain a lot of redundant information that isn’t needed when deciding whether to listen to the episode.

The audio clips will be assessed by a yes/no-question: 

* Does the clip give a sense of what the podcast sounds like, (as far as you can tell from listening to it)?


### Evaluation Set for Summarization
The evaluation set will be created from a set of 500 held-out episodes which will be used to test the summarization systems. These test episodes will be provided later in the task. 

### Submission Format for the summarization task

A run will comprise exactly two files per summary, where the name of each summary file is the ID of the episode it is intended to represent, with the suffix “_summary.txt” appended to the text summary file and "_clips.ogg" appended to the audio file. Please include files for a summary, even if your system happens to produce no output for that episode. Each text summary file will be read and assessed as a plain text file, so no special characters or markups are allowed. The audio file is expected in an OGG container with most reasonable listenable audio formats acceptable. The summary files should be delivered in a directory  whose name should be the concatenation of the Team ID and a number (1 to N) for the run. (For example, if the Team ID is "SYSX'' then the directory name for the first run should be "SYSX1".) Please package the directory in a tarfile and gzip the tarfile before submitting it to NIST. 

### Timeline for summarization task

* Document collection released: April 16th, 2020
* 2021 guidelines released: April 14th, 2021
* Test episodes to summarize released early August, 2021
* Runs due: September 3, 2021
* Results released to participants: Early October, 2021


## TREC Podcasts 2021 Track Organizers

* Ben Carterette, Spotify
* Ann Clifton, Spotify
* Maria Eskevich,  CLARIN ERIC
* Gareth F. Jones, Dublin City University
* Rosie Jones, Spotify
* Jussi Karlgren, Spotify
* Sravana Reddy, Spotify
* Md Iftekhar Tanveer, Spotify
