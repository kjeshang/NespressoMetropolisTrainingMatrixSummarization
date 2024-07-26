# NespressoMetropolisTrainingMatrixSummarization

> Kunal Jeshang, Total Quality Management Team Leader _(Project Timeline: April 2024 - July 2024)_

***Please note that even though the codebase of this project may be public, however, all internal Nestle Nespresso documents & generated data are not accessible even though they were imperative to completing the project. This is because these documents & generated data are meant for internal use only.***

## Table of Contents

1. [Introduction](#Introduction)
2. [Data Extraction](#Data-Extraction)
3. [Text Summarization](#Text-Summarization)
4. [Evaluation](#Evaluation)
5. [Next Steps](#Next-Steps)
6. [References](#References)

## Introduction

As the Total Quality Management (TQM) Team Leader, it is my job to emphasize health and safety to the rest of the staff, as well as find alignment with Nestle's health & safety guidelines with daily operations. Adherence to some of these guidelines and related tasks is paramount to be a successful in the eyes of the corporate team. One of these tasks involve receiving annual training regarding security, health, safety, and sustainability.  Historically, this training involved employees reading an Employee Memo document, which is long in length. The Employee Memo document contains multiple sections. After reading the document, the employee would then have to take a quiz.

It came to light that after explaining that training would have to be conducted this year, some members of staff were not keen to read so many pages in quick succession. Furthermore, reading many pages of text over a longer duration is detrimental to knowlegde retention. Thus, I opted create a project that aims to summarize the important aspects from each section of the Employee memo document (i.e., reference text). The best way to make this project idea become a reality was to utilize Python programming, along with machine learning & natural language processing libraries.

## Data Extraction

The first step of this project involves reading in the file path of the reference text and required Python libraries. The textual content of each section (i.e., start page to end page of given section) in the reference text page-by-page. The extracted text is saved in a Pandas dataframe and exported into an Excel workbook, which will serve as a raw dataset for future stage/s of the project.

Below is a tabular breakdown of the raw dataset.

|Column|Data Type|Description|
|--|--|--|
|Section|Object|Section in reference text (i.e., Employee Memo)|
|Start Page|Integer|First page of respective section|
|End Page|Integer|Last page of respective section|
|Extracted Text|Object|Textual content retrieved from the section (i.e., from given start page to end page)|

## Text Summarization

### Summarization Type & Techniques

There are two methods of text summarization; extractive and abstractive. The extractive summarization method summarizes the text by choosing a subset of sentences from the text that hold the most importance. The abstractive summarization method aims to understand the core context of the text, and then construct new text based on the understanding (saxena).

Below is a tabular breakdown of the various techniques that is used to construct summaries.

|Summarization Type|Technique|Explanation|
|--|--|--|
|Extractive|Textrank|Similar to Lexrank, it uses graph-based algorithms to identify key sentences based on their connectivity within the document.|
|Extractive|BERT|_Bidirectional Encoder Representations from Transformers_; Utilizes deep learning and transformers to understand the context and semantics of words and sentences.|
|Extractive|Lexrank|Focuses on analyzing relationships between sentences using graph-based algorithms, particularly leveraging cosine similarity.|
|Extractive|Luhn|Based on term frequency and sentence length, it identifies key sentences by looking at the occurrence of important words.|
|Extractive|LSA|_Latent Semantic Analysis_; Uses singular value decomposition (SVD) to analyze relationships between terms and documents in a vector space.|
|Abstractive|BART|This technique combines auto-regressive and auto-encoder architectures for sequence-to-sequence tasks like summarization and generation.|
|Abstractive|T5|This technique focuses on a text-to-text approach with a fill-in-the-blank pre-training objective.|

### Summarization Implementation

Below is a step-by-step breakdown of how the summarization of the extracted text took place via the aforementioned methods and techniques.
1. Import the necessary packages and raw dataset
2. Import training data models for _BERT_, _BART_, and _T5_, which are considered constant variables.
3. Instantiate other constant variables that consists of lists containing summarization methods and techniques.
4. Define constant functions that will be applied reptitively.
    * Define function that processes the given extracted text that removes redundant words that exist prevelantly in the reference text, and accomodates for new line spaces if specified.
    * Define function that is used to perform extractive summarization using a given a processed text and specified summarization technique, along with some other parameters.
    * Define function that is used to perform abstractive summarization using a given processed text and a specifified summarization technique, along with some other parameters.
    Define function that applies the previous functions sequentially through the raw dataset, and as per the summarization method list and technique list. The function also saves the summaries to a dataframe.
5. Apply the functions explained in the previous step, and export dataframe containing summarized data to an Excel  workbook.

Below is a tabular breakdown of the summary dataset.

|Column|Data Type|Description|
|--|--|--|
|Section|Object|Section in reference text (i.e., Employee Memo)|
|Summarization|Object|This is either _Extractive_ or _Abstractive_ summarization method.|
|Technique|Object|Summarization technique applied to generate the summary (i.e., Textrank, LSA, T5, etc.)|
|Summarized Text|Object|Text after summarization technique is applied.|

## Evaluation

### Evaluation Metrics

Below is a tabular breakdown of the evaluation metrics used to determine whether a summary was optimal or not. In a sense, the metrics below are basically making a comparison between the summary text and reference text.

|Metric|Description|
|--|--|
|Rouge|This metric measures the n-gram overlap between a generated summary and a reference text. In a sense, its evaluation is based on word-level similarity.|
|BERTScore|This metric measures the similarity between sentences on a semantic level. Specifically, it can handle ambiguity problems of words, synonyms, and antonyms. Therefore, it is excellent for evaluating the overall quality of summaries.|
|Meteor|This metric was designed to accomodate for translation or summarization errors, which includes word order problems, synonyms and ambiguities, and fluency of text.|

The range for the Rouge F1 Score, BERT F1 Scores, and METEOR Score is between 0 and 1. The closer the score is to 1, the more similar the summarized text is to the reference text.

### Evaluation Implementation

Below is a step-by-step breakdown of how all of the generated summaries were evaluated.
1. Import the necessary packages, as well as the raw dataset & summary dataset.
2.  Instantiate any constant variables necessary.
3.  Define constant functions that will be applied repetitively.
    * Define function that calculates Rouge score based on given raw text and summary text, and then returns a dataframe showing scores.
    Define function that calculates BERT score based on given raw text and summary text, and then returns a dataframe showing scores.
    Define function that calculates METEOR score based on given raw text and summary text, and then returns a dataframe showing scores.
    Define function that applies all of the aforementioned functions sequentially based on given raw data, summary data, and selected evaluation metric. The function also saves the summaries to a dataframe.
4. Apply the functions explained in the previous step. Export dataframe containing evaluated data to an Excel workbook, whereby each sheet is dedicated to a specific evaluation metric. 

Below is a tabular breakdown for the Rouge sheet in the evaluated dataset.

|Column|Data Type|
|--|--|
|Section|Object|
|Summarization|Object|
|Technique|Object|
|Summarized Text|Object|
|rouge-1 Recall|Float|
|rouge-1 Precision|Float|
|rouge-1 F1 Score|Float|
|rouge-2 Recall|Float|
|rouge-2 Precision|Float|
|rouge-2 F1 Score|Float|
|rouge-l Recall|Float|
|rouge-l Precision|Float|
|rouge-l F1 Score|Float|

Below is a tabular breakdown for the BERT sheet in the evaluated dataset.

|Column|Data Type|
|--|--|
|Section|Object|
|Summarization|Object|
|Technique|Object|
|Summarized Text|Object|
|BERT Recall|Float|
|BERT Precision|Float|
|BERT F1 Score|Float|

Below is a tabular breakdown for the METEOR sheet in the evaluated dataset.

|Column|Data Type|
|--|--|
|Section|Object|
|Summarization|Object|
|Technique|Object|
|Summarized Text|Object|
|METEOR Score|Float|

### Takeaway

Despite evaluation metrics being utilized to assess and compare the quality and accuracy of the summarizations, it was not representative of the desired intent of the project which was to create a simple, short, and concise summary of what was discussed in the Employee Memo. Therefore, manually scanning each summary based on summarization technique and crosschecking the summary to the reference text (i.e., Employee Memo) was far more logical in determining an optimal summary.  

## Next Steps

### Manual Adjustment

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

A common aspect of constructing the final summary documents was to manually edit the generated summaries as not all of the text is accurate in terms of readability, conciseness, and grammar. There are some instances where sentences are cutoff and the gaps must be filled. The summaries were edited within markdown files using Microsoft Visual Studio Code, and then exported to PDF documents once editing was completed.

### Fine Tuning
I asked fellow team leaders to read the summaries and take the training matrix quiz. Based on their performance, I further adjusted the summaries by incorporating additional snippets of knowledge that would best reflect content of the Training Matrix quiz. That way the remaining members of the team could be better prepared to take the quiz after reading the summaries. Below is a breakdown of the drafts and descriptive aspects.
* **First Draft** &mdash; Raw summaries generated by the Python code
* **Second Draft** &mdash; Raw summaries that were manually edited to adjust for grammatical errors, run-on sentences, and lack of coherence. The Team Leaders read this draft of summaries to prepare for their quizzes.
* **Third Draft** &mdash; Summaries that were adjusted based on the quiz performance of the Team Leaders. The remaining members of the team read this draft of summaries to prepare for their quizzes.

### Results
After every member of the team read the final versions of the summaries and took the Training Matrix quiz, the scores were compiled along with additional collected metrics. Below is a generic table summarizing the performance of the team. In my perspective, the performance was positive. Please note that I was the Team Leader that created the summaries and facilitated the quizzes, I excluded my test scores from the results analysis. Therefore, an analysis of the remaining <u>20 employees</u> was performed.

||Numerical Score|Percentage Scores|
|--|--|--|
|Mean|20.25/25|81.00%|
|Minimum|15/25|60.00%|
|Maximum|25/25|100.00%|

For further analysis of the test results, please [Click Here](https://github.com/kjeshang/NespressoMetropolisTrainingMatrixSummarization/blob/main/4_ResultsAnalysis.ipynb).

## References

[Text Summarization in Python using Extractive method (including end-to-end implementation)](https://medium.com/analytics-vidhya/text-summarization-in-python-using-extractive-method-including-end-to-end-implementation-2688b3fd1c8c) &dash; sawan saxena (_The Medium_)

[Metrics for evaluating summarization of texts performed by Transformers: how to evaluate the quality of summaries](https://fabianofalcao.medium.com/metrics-for-evaluating-summarization-of-texts-performed-by-transformers-how-to-evaluate-the-b3ce68a309c3) &dash; Fabiano Falcão (_The Medium_)

[Online Markdown Editor](https://pandao.github.io/editor.md/en.html) - Editor.md
