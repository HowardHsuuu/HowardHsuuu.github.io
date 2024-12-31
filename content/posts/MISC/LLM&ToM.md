---
title: "[LR]  Unveiling Theory of Mind in Large Language Models"
date: 2024-09-23T19:24:43+08:00
draft: false
---

Paper Info
> arXiv:2309.01660  
> Title: Unveiling Theory of Mind in Large Language Models: A Parallel to Single Neurons in the Human Brain  
> Author: Mohsen Jamali and Ziv M. Williams and Jing Cai  

## Prior Knowledge
### Theory of Mind (ToM)
A complex cognitive capacity related to our conscious mind and mental state that allows us to infer another's beliefs and perspective. Through ToM, human can create intricate mental representations of other agents and realize that others may have beliefs that's different from our own or the objective reality.
### True- and False-belief Task
* True-belief task: assesses whether someone understands that some other people's believes is correctly aligned with reality.
* False-belief task: assesses whether someone understands that some other people's believes is **not** correctly aligned with reality. (ex: belief diverges from reality after a change to the environment that one did not witness.)
* A critical test for ToM is the false belief task.
* Both tasks are evaluated by providing the participant a scenario and asking the participant "fact questions" and "belief questions", which are about the reality and the belief of some character in the scenario respectively.
* These tasks are designed to test if the individual can attribute mental states (including potentially false beliefs) to others in general.
### ToM in the human brain
> Human brain imaging studies have provided substantial evidence for the brain network that supports our ToM ability, including the temporalparietal junction, superior temporal sulcus and the dorsal medial prefrontal cortex (dmPFC)

> Research have identified single neurons in the dorsal medial prefrontal cortex that exhibit selective modulations for true- versus false-belief trials during the period of questions, suggesting a particular role for processing others' beliefs and potentially subserving ToM ability. (reference1)

> These neurons displayed a consistent difference in their firing rates when the other's beliefs were true compared to when the other's beliefs were false. These neurons therefore reliably changed their activities in relation to the other's beliefs despite variations in the specific statements and scenarios within each trial type, providing evidence for the specific tuning of human neurons to ToM computations.
### Some Premises
LLM is proven to exhibit a certain level of ToM. (The January 2022 version of GPT3 (davinci-002) has a performance comparable with that of seven-year-old children, while the November 2022 version (davinci-003) has a performance comparable with that of nine-year-old children.)

---

## Goal
To draw, with the inspiration of dmPFC, a parallel between the reaction of LLM and the human brain when tested with ToM.
## Method
The LLMs evaluated (open-source models): Falcon (1b, 7b, 40b), LLaMa (3b, 7b, 13b, 30b, 33b), Pythia (3b, 7b, 12b), GPT-2 (medium, large, xl)
1. Obtain the activities of 'artificial neurons' in LLMs via hidden embeddings (output of transformer modules) from all layers as well as the input to the first transformer module.
2. Establish a meaningful comparison with human neurons via ToM task materials for LLM closely aligned to the one they tested on humans:
   - Trials grouped into pairs of true and false belief trials
   - Belief questions following the statement
   - 76 trials in total, with statement lengths ranging from 81 to 191 words (average 125 words)
3. Input the model with the concatenation of the statement and the question as one batch and examine the embeddings from the tokens within the questions:
   - Use Mann Whitney U test to identify significant differences in values between true- and false-belief trials
   - Perform control experiments by randomly permuting words in statements
   - Conduct decoding analysis using logistic regression with L2 regularization to predict trial types from embeddings
## Results
1. LLM Performance:
   - Larger models (>12b parameters) performed significantly better, especially for false-belief trials (with average accuracy of 68%)
   - Smaller models (<7b parameters) showed accuracies at or below chance level on false-belief trials
2. Embedding Responsiveness:
   - Large models (>12b parameters) showed an average of 3.9% of embeddings responding to ToM tasks (This dropped to 0.6% for smaller models).
   - Falcon 40b model showed the highest percentage (6.3%) of responsive embeddings in layer 25
3. Decoding Accuracy:
   - Large models (>12b parameters) showed an average of 75% decoding accuracy
   - Falcon-40b model showed the highest decoding accuracy of 81%
   - Smaller models (<7b parameters) had an average decoding accuracy of 67%
## Conclusion
### Parallel 1 - Selective response to true- or false-belief trials
The presence of embeddings that displayed modulations related to the ToM content (absent in smaller models, which have difficulties with false-belief trials) in multiple large models indicates that hidden embeddings facilitate the models' ToM performance. Also, ToM trial types can be robustly decoded from the population of artificial neurons (embeddings), indicating a consistent encoding of ToM features by the embeddings.

Both systems (Human Brain and LLM) contain neurons that directly respond to the perspective of others. A substantial proportion of artificial neurons responds selectively to true- or false-belief trials, mirroring prefrontal neurons in humans exhibiting changes in firing rates for different trial types.
### Parallel 2 - Distribution of ToM-responding neurons
* LLM layers with high percentages of ToM responding embeddings showed a peak in the middle and high layers and almost zero in the input layers constantly (neither confined to one layer nor randomly distributed). 
* Similar distributed areas can be identified in the human brain as the frontal, temporal and parietal cortices are regarded as regions for high-level cognitive processing. (ToM-related activity within lower input processing areas such as occipital lobe is minimal) 
* Also, they observed the artificial layers exhibiting ToM responses were located in contiguous layers, which is analogous to the highly interconnected structure of ToM brain areas.
### Other conclusions
* LLM had higher accuracies when tested with facts and beliefs in true-belief trials compared to false-belief trials. (larger models did better, especially for false-belief trials)
* As the size of the models increase, the decoding accuracies, the percentages of significant neurons and ToM performances all increased.
## Limitations
1. The study was limited to open-source LLMs. Future research could examine higher-performing, proprietary models like GPT-4.
2. The methods excluded embeddings that were selective to both true- and false-belief trials, focusing only on those selective to one type. This could be expanded in future studies.
3. While the parallels between LLMs and human brains are striking, the underlying mechanisms of ToM in LLMs are still not fully understood and require further investigation.
4. The study doesn't address how LLMs develop ToM capabilities without direct social interaction or any special training, unlike humans. This could be an interesting area for future research. (suggests that ToM might be an emergent property of advanced language processing systems.)

---

## Reference
* The paper: https://arxiv.org/abs/2309.01660
* Some of the papers cited in this paper
	1. https://www.nature.com/articles/s41586-021-03184-0
	2. https://arxiv.org/vc/arxiv/papers/2302/2302.02083v1.pdf
* This Note is written with the assistance of Generative AI and quotes from the original paper