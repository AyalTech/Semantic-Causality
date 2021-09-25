# Semantic_causality

## Haddad Ayale & Agliz Yasmine

The purpose of this project is to facilitate the extraction of relevant information from large corpus of biomedical documents. The kind of information we seek is the causalities between the most relevant terms of a certain disease. We worked on the five following diseases:
- Hay fever 
- Kidney calculi 
- Age-related Macular Degeneration 
- Migraine 
- Otitis.

### Co-clustering
We applied a co-clustering algorithm on the adjacency matrix of PubMed5. As a result, we got a matrix with 5 sub-matrices, each one corresponds to a specific disease.

In order to retrieve the most relevant terms from a corpus of documents of a disease. We used two different approaches. The first one is the word’s frequency and the second one is the NPMI score. The first approach gave some satisfying results. However, we noticed some frequent words which are not significant according to the disease. The first results led us to the conclusion that a high frequency does not imply a word’s importance in the topic. The NPMI score on the other hand gave better results in terms of extracting the most significant words.

### Embeddings & Grap
Once we get the most significant words, we try to display them in the most informative way which is the graph. Indeed, a non-directed graph allows us to represent the most significant words and the links between them. The link between two words is determined by their similarity, and for this we chose the cosine similarity. To represent the words, we used 5 different embeddings, each embedding was learned from a different corpus using different algorithm.

The embeddings with the best results are the one with the medical background. The last step of this project was the causal graph. The causal graph is used to represent the causal link between the significant words of the disease. After some experiments, we noticed that in order to have causality links between the words we had to fulfil two conditions. The first one is that the dimension of the vectors should be large. The second condition is that, the embeddings should have an important medical background. Therefore, we used the embeddings with the most medical background such as the embeddings from PMC and the embeddings from Wikipedia. Thus, we merged all the embeddings except the embeddings learned from Gigaword which is a corpus of newspaper articles with no medical background. Using the
merged embeddings, we obtain a causal graph with many causal links between the words. These links translate medical causality which can easily be interpreted by a professional.

In this project, we used available embeddings on the internet. These embeddings were 200 and 300-dimensional vectors. These dimensions may not be optimal. For future improvements, we can generate embeddings with the same algorithm and the same dataset for learning but with different dimensions. Indeed, the dimension of the embeddings will commensurate with their effectiveness in providing medical information. We can adjust the dimensions of the embeddings according to their evaluation score which is Spearman correlation.

At last, we used the package Palmetto to calculate the NPMI score between the words. Palmetto uses Wikipedia as an input dataset to compute the co-occurrence between the words. It would be interesting to see the difference if we use another tool which uses a medical dataset as an input.
