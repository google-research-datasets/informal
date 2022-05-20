
# Description

InFormal is a formality style transfer dataset for four Indic Languages. The dataset is made up of a pair of sentences and a corresponding gold label identifying the more formal as well as semantic similarity. This dataset can be used as an evaluation set for style transfer tasks in Indic Languages.

InFormal contains sentence pairs from 4 Indic Languages - Hindi, Telugu, Kannada and Bengali. The annotator is asked to choose the more formal sentence and rate the semantic similarity between the pair on a 3 point scale. This dataset is intended to be used as a test set and is part of the evaluation suite proposed in the paper.  

# Data Collection:

## Steps:
We use the Samanantar dataset to get the source sentences for each language. We then style transfer a set of sentences using our style transfer model with best output diversity. (UR-INDIC + BT in paper). 
We then asked three crowdworkers to 
Label the more formal sentence in each pair
Mention how semantically similar the two sentences are

We used TaskMate for our data collection, where we hired native speakers who had a 90% approval rating on the platform. We paid our crowdworkers $0.05 per pair.  Each pair was assigned three annotators. 

## Data Statistics: 

InFormal test set contains approx 1000 pairs of sentences for each of the four Indic Languages. Exact numbers can be found below.

Hindi 1000 

Telugu 1010

Kannada 1023

Bengali 1008


## Data Format:

Paths:
Files: {lang}_annotations.jsonl (lang = hi, te, kn, bn)


Format:
{lang}_annotations.jsonl: 
Each line of the dataset corresponds to a sentence pair, semantic similarity score using LABSE and all three human annotations for similarity and formality.  

Keys:
“candidate_0”: First candidate for formality comparison [text]

“candidate_1”: Second candidate for formality comparison [text]

“labse”: Semantic similarity score between two candidate sentences using LABSE 

“annotations”: The set of human annotations. Field contains a list of 3 human annotations with each annotation consisting of following fields:
“semantic_similarity”: Human (gold) annotation for semantic similarity on three point scale. This field will have one of the following values: Approximately Same Meaning (1), Slight Difference in Meaning (0.5), Different Meaning (0).  Values in the braces indicate the numeric equivalent used for each annotation in order to calculate numerical similarity scores. 
“formal_sent”: This field will indicate the more formal sentence among the two candidates. This field will have one of the following values: candidate_0, candidate_1, Equal. 
Data Sample: 
```
{
    'candidate_0': 'लगता है डैडी तुमसे प्यार नहीं करते।',
    'candidate_1': 'पिताजी आपको नहीं चाहते।',
    'labse': 0.6575319170951843,
    'annotations': [
        {
            'semantic_similarity': 'Approximately Same Meaning',
            'formal_sent': 'candidate_1'
        },
        {
            'semantic_similarity': 'Slight Difference in Meaning',
            'formal_sent': 'candidate_1'
        },
        {
            'semantic_similarity': 'Approximately Same Meaning',
            'formal_sent': 'candidate_1'
        }
    ]
}
```
