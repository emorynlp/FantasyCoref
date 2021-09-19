# FantasyCoref

*FantasyCoref* project presents a new corpus and annotation guideline for a novel coreference resolution task on fictional texts, and analyzes its unique characteristics.
*FantasyCoref* contains 211 stories of Grimms' Fairy Tales and 3 other fantasy literature annotated in the omniscient writer's point of view (OWV) to handle distinctive aspects in this genre.

This task is more challenging than general coreference resolution in two ways.
First, documents in our corpus are 2.5 times longer than the ones in OntoNotes, raising a new layer of difficulty in resolving long-distant referents.
Second, annotation of literary styles and concepts raise several issues which are not sufficiently addressed in the existing annotation guidelines. Hence, considerations on such issues and the concept of OWV are necessary to achieve high inter-annotator agreement (IAA) in coreference resolution of fictional texts.
Second, annotation of literary (fictional) concepts is more confusing than that of general objects, thus, is almost impossible to achieve high inter-annotator agreement (IAA) without borrowing the concept of OWV.

We carefully conduct annotation tasks in four stages to ensure the quality of our annotation. As a result, a high IAA score of 87% is achieved using the standard coreference evaluation metric.Finally, state-of-the-art coreference resolution approaches are evaluated on our corpus with and without fine-tuning. After fine-tuning, there was a 2.59\% and 3.06\% improvement over the model trained on the OntoNotes dataset. Also, we observe that the portion of errors specific to fictional texts declines after fine-tuning.


# Dataset
1. data source (https://www.gutenberg.org)
    * For GFT, each story is annotated from the beginning to the end. For AFT, only the beginning parts of the stories are annotated. (First 10,000 words for *The Story of Aladdin* and *The Story of Ali Baba and the Forty Thieves*, from chapter 1 to chapter 5 for *Alice's Adventures in Wonderland*)
    * GFT : Grimm's Fairy Tales
        * [Household Tales by Brothers Grimm by Jacob Grimm and Wilhelm Grimm](https://www.gutenberg.org/ebooks/5314)
    * AFT : Additional Fantasy Texts
        * [The Arabian Nights: Their Best-known Tales by Smith, Wiggin, and Parrish](https://www.gutenberg.org/ebooks/20916)
            * Among the stories in *The Arabian Nights*, *The Story of Aladdin*, *The Story of Ali Baba and the Forty Thieves* are annoated for the corpus. 
        * [Alice's Adventures in Wonderland by Lewis Carroll](https://www.gutenberg.org/ebooks/11)
2. data structure
    * **spliting train, dev, test set**
        * Development and test set are chosen from 211 stories (10 stories each) in GFT using stratified sampling method so that the train/dev/test set could have homogeneous distributions in terms of number of sentences, tokens, entities, mentions, and number of fantasy-specific issues(**Assymetry of Knowledge**, **Changes in Entities**, **Foretelling or Wishes**, **Lexical Variations**).
        * The rest of the stories (171 stories) are used as a train set to train our model.
        * Note that all stories in AFT are only used as a separate test set to evaluate the generalization ability of our model on additional fictional texts.
    * **partitioning documents**
        * In the case of the dev/test set, additional partitioned version is constructed to reduce the number of tokens to be similar to that of the OntoNotes dataset (467 tokens).
        * The partitioning process was done towards preserving the original entity chain.
Each story is partitioned by finding the case where the sum of the number of entities in each partition is minimum so that the original entity chains are not cut in the middle and thereby produce extra number of unique entities in each partition.
In addition, the stories were not partitioned in the middle of pair quotation marks to avoid starting or ending the partition in the middle of one's utterance.
<br>

|dir name|structure|explanation|
|------|---|---|
|GFT_split1|dev, test, train||
|GFT_split2|dev, test, train||
|AFT_split3|test||
|AFT_original|test||
    
3. data format

4. annotation guideline
    
    
# Statistics
1. overall statistics
2. statistics of splited dataset

# Citation
