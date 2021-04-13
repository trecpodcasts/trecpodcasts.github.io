# TREC 2021 Podcasts Track Guidelines
Guidelines V2.0, March 31, 2021

## Task 1: Fixed-length Segment Retrieval 

Given a retrieval topic (a phrase, sentence or set of words) and a set of ranking criteria, retrieve and rank relevant two-minute segments from the data. 

### Topics for the Fixed-length Segment Retrieval Task

Topics will consist of a topic number, keyword query, a query type, and a description of the user’s information need.  For example:

<topic>
<num>3</num>
<query>black hole image</query>
<type>topical</type>
<description>In May 2019 astronomers released the first-ever picture of a black hole. I would like to hear some conversations and educational discussion about the science of astronomy, black holes, and of the picture itself.</description>
</topic>

Query type in 2021 will be either "topical" or "known-item". Participants will be asked to submit ranked lists of segments from the data. A segment is a two-minute chunk starting on the minute; e.g. [0.0-119.9] seconds, [60-199.9] seconds, [120-139.9] seconds, etc.

### Ranking criteria

*  Adhoc topical retrieval: the segment is topically relevant to the topic description. 

*  Entertaining: the segment is topically relevant to the topic description AND the topic is presented in a way which the speakers intend to be amusing and entertaining to the listener, rather than informative or evaluative. 

*  Subjective: the segment is topically relevant to the topic description AND the speaker or speakers explicitly and clearly express a polar opinion about the query topic, so that the approval or disapproval of the speaker is evident in the segment.

*  Discussion: the segment is topically relevant to the topic description AND includes more than one speaker participating with non-trivial topical contribution (e.g. mere grunts, expressions of agreement, or discourse management cues ("go on", "right", "well, I don't know ..." etc) are not sufficient). 

### Assessment for the Fixed-length Segment Retrieval Task

The submitted two-minute length segments will be judged by NIST assessors for their topical relevance to the topic description and their adherence to the reranking criteria.  NIST assessors will have access to both the text transcript of the episode (including text before and after the text of the two-segment, which can be used as context) as well as the corresponding audio segment.  

For the adhoc submission, the assessments will be made on the PEGFB graded scale (Perfect, Excellent, Good, Fair, Bad) as follows:

* Perfect (4): this grade is used only for "known item" queries.  It reflects the segment that is the earliest entry point into the one episode that the user is seeking.
* Excellent (3): the segment conveys highly relevant information, is an ideal entry point for a human listener, and is fully on topic.  An example would be a segment that begins at or very close to the start of a discussion on the topic, immediately signalling relevance and context to the user.
* Good (2): the segment conveys highly-to-somewhat relevant information, is a good entry point for a human listener, and is fully to mostly on topic.  An example would be a segment that is a few minutes “off” in terms of position, so that while it is relevant to the user’s information need, they might have preferred to start two minutes earlier or later.
* Fair (1): the segment conveys somewhat relevant information, but is a sub-par entry point for a human listener and may not be fully on topic.  Examples would be segments that switch from non-relevant to relevant (so that the listener is not able to immediately understand the relevance of the segment), segments that start well into a discussion without providing enough context for understanding, etc.
* Bad (0): the segment is not relevant.

For the three other criteria, the assessments will be made on a three grade scale as follows:
* Adhering (3): The segment is clearly intended to be entertaining, the segment is subjective; the segment contains multi-party discussion.
* Partial (1): The segment may be intended to be entertaining or the participants react with appreciation or glee which may or may not be due to entertainment value of statements in the segment; the segment contains subjective or evaluative language but its target topic may be unclearly delimited or due to some previously mentioned discourse topic; there are more than one participant and they contribute to the conversation but it remains unclear if they contribute to the topic or some other topic. 
* Non-adhering (0): The segment is not intended to be entertaining nor is interpreted as such by its participants; the segment does not express the speaker attitude vis-a-vis the topic; the segment does not involve multiple participants or only one speaker contributes to the topic. 

### Evaluation Metric for the Fixed-length Segment Retrieval Task

The primary metrics for evaluation will be nDCG at a cutoff of 30 documents, precision at 10, and nDCG over the entire ranked list. A single episode may contribute one or more relevant segments, some of which may be overlapping, but these will be treated as independent items for the purpose of nDCG computation.  We expect to assess at a pool depth of 10, meaning the top 10 segments for each ranked list. 

### Submission Format for the Fixed-length Segment Retrieval Task

Submissions for the ad hoc retrieval task should be in standard whitespace-delimited TREC 6-column format.

```
TOPICID   Q0   EPISODEID_OFFSET   RANK   SCORE   RUNID
```

`TOPIC` is the unique topic number.  A submission should include at least one result for every topic in the test set.
`Q0` contains the static string “Q0”.  No information is contained in this column.
The `EPISODEID_OFFSET` column is the unique identifier for the retrieved segment.  It must consist of an episode URI (unique identifier) concatenated with an offset in seconds to the start of the segment, separated by an underscore character “_”.  The offset must be a multiple of 60 with one decimal place, e.g. “120.0”.  Each entry in this column must be unique to the topic ID.
`RANK` is the rank at which the segment has been retrieved.
`SCORE` is the system score for the segment.
`RUNID` is a unique identifier for the participant and submitted run.

Participants may submit up to 4 runs. Each run should consist of four separate 6-column files consisting of ranked results for all topics in the test set, one file per ranking criterion. Participants are asked to return a ranked list of at most 1,000 segments for each topic. The RUNID identifier should begin with one of ADHOC, ENTERTAIN, SUBJECTIVE, DISCUSSION to indicate which criterion is used for ranking. 

Example submission

```
9 Q0 spotify:episode:3ZUU9IO0V8kaZaUPD6qqDY_360.0 1 121.2 ADHOC-myrun1
9 Q0 spotify:episode:000HP8n3hNIfglT2wSI2cA_60.0 2 87.8 ADHOC-myrun1
...
```

```
9 Q0 spotify:episode:0CDSmklC42307Ktg86ER7Y_840.0 1 87.98 SUBJECTIVE-myrun1
9 Q0 spotify:episode:000A9sRBYdVh66csG2qEdj_120.0 2 67.2 SUBJECTIVE-myrun1
...
```

```
9 Q0 spotify:episode:6O8djf3RL94yNfaoWqvk3r_840.0 1 4.82 ENTERTAIN-myrun1
9 Q0 spotify:episode:6v0auT8BbeXzMTmg9FjyDB_1980.0 2 1.17 ENTERTAIN-myrun1
...
```

```
9 Q0 spotify:episode:0bI9g00ZrF5VczfdkWds7a_2280.0 1 82.0 DISCUSSION-myrun1
9 Q0 spotify:episode:000HP8n3hNIfglT2wSI2cA_480.0 2 31.4 DISCUSSION-myrun1
...
```


### Timeline for segment retrieval task

* Document collection released: April 16th, 2020
* Sample topics and qrels released: March 31, 2021
* 2021 guidelines released: April 14th, 2021
* Test topics released: TBD
* Runs due: TBD (aiming for July 1, 2021)
* Results released to participants: Early October, 2021


## Task 2: Summarization

Coming soon!


### Timeline for summarization task

* Document collection released: April 16th, 2020
* 2021 guidelines released: April 14th, 2021
* Test episodes to summarize released: TBD
* Runs due: TBD
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
