# NespressoMetropolisTrainingMatrixSummarization

> Kunal Jeshang, Total Quality Management Team Leader _(Project Timeline: April 2024 - May 2024)_

***Please note that even though the codebase of this project may be public, however, all internal Nestle Nespresso documents & generated data are not accessible even though they were imperative to completing the project. This is because these documents & generated data are meant for internal use only.***

## Data Extraction

## Text Summarization

## Evaluation

### Evaluation Metrics

|Metric|Description|
|--|--|
|Rouge|This metric measures the n-gram overlap between a generated summary and a reference text. In a sense, its evaluation is based on word-level similarity.|
|BERTScore|This metric measures the similarity between sentences on a semantic level. Specifically, it can handle ambiguity problems of words, synonyms, and antonyms. Therefore, it is excellent for evaluating the overall quality of summaries.|
|Meteor|This metric was designed to accomodate for translation or summarization errors, which includes word order problems, synonyms and ambiguities, and fluency of text.|

Despite evaluation metrics being utilized to assess and compare the quality and accuracy of the summarizations, it was not representative of the desired intent of the project which was to create a simple, short, and concise summary of what was discussed in the Employee Memo. Therefore, manually scanning each summary based on summarization technique and crosschecking the summary to the reference text (i.e., Employee Memo) was far more logical in determining an optimal summary.

## Next Steps

After performing all of the prior steps, the next portion of the project was to read through the summaries based on type & technique, whilst also considering the evaluation metric score, but weighing more importance to comparing it with the reference text (i.e., Employee Memo). This is performed whilst simultaneously editing the selected summary so that is understandable if an employee of Nespresso Metrotown were to read it.

The primary determinants for selecting a summary are the following.
1. Length of Summary
2. Conciseness 
3. Evaluation Metric Score
    * A moderate evaluation metric score is considered for shorter sections of the reference text.
    * A higher evaluation metric score is conisdered for longer sections of the reference text.

In constructing the final summaries, I at times mixed and matched portions from different summaries to be incorporated together. Due to the varying quality of the summaries, I decided to create a summary document that may contain the some of the following sections.
* Short Summary
* Long Sumary
* Objective &ndash; This is a summary that is very short in length, and is included in the event that a longer summary that is selected is sufficient in terms of detail and length.
* Images &ndash; This is due to some textual content in the reference text being in an image format. Thus, the textual content was not retrieved during the "Data Extraction" phase of the project.

A common aspect of constructing the final summary documents was to manually edit the generated summaries as not all of the text is accurate in terms of readability, conciseness, and grammar. There are some instances where sentences are cutoff and the gaps must be filled.