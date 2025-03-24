# Project Proposal for CounterSpeech Modeling

**Authors**:  
- Anant Kumar Kaushal  
  anant22067@iiitd.ac.in

- Anikait Agrawal  
  anikait22072@iiitd.ac.in

- Ansh Varshney  
  ansh22083@iiitd.ac.in

---

## Introduction
Online hate speech poses serious social and psychological threats, often escalating tensions within communities.  
*Counterspeech*—a positive, corrective response to hateful content—has been shown to help mitigate harm but is challenging to generate at scale. While many approaches produce *generic* replies, the need for **intent-specific counterspeech** (e.g., *informative*, *denouncing*, *questioning*, *positive*, *humorous*) is crucial for aligning responses with context and audience expectations.

## Related Work
Research on hateful content has examined counterspeech generation from various angles. For example, efforts to collect richer data for multilingual counterspeech were described in a multi-target approach that leverages *human-in-the-loop* mechanisms [[Ref1]](https://link.springer.com/chapter/10.1007/978-3-030-75762-5_55). Additionally, the *METEOR* metric was introduced to improve correlation with human judgments in machine translation tasks, influencing how we might evaluate text generation [[Ref2]](https://aclanthology.org/W05-0909/). Recent developments in *intent-conditioned counterspeech* introduce novel architectures for learning separate representations of style and content; this helps achieve better performance and more precise control in responses [[Ref3]](https://arxiv.org/pdf/2305.13776).

## Methodology
We propose to fine-tune a **sequence-to-sequence model** (e.g., BART), conditioning on both the **hate speech** and its desired **intent label** (from five categories). Specifically, we concatenate:  
intent: [INTENT] + hate_speech [HATE_SPEECH}

as input, prompting the model to generate the corresponding *counterspeech*.

## Dataset, Setup, and Observations
We use a dataset [[Ref3]](https://arxiv.org/pdf/2305.13776) of 6,831 counterspeeches across five intents (*informative*, *denouncing*, *question*, *positive*, *humour*). Key steps include:

1. **Data Splits:** Train (70%), Validation (15%), Test (15%).  
2. **Pre-processing:** We cleaned the dataset by removing null values and verified balanced class distribution through exploratory data analysis.  
3. **Evaluation:** We measure BLEU and BERTScore, finding BLEU ≈ 0.02 and BERTScore ≈ 0.87 on the validation set.

## Conclusion and Future Work
While our model yields a high BERTScore (~0.87) but low BLEU (~0.02), it indicates good semantic alignment but limited token-level overlap. To address this, we propose a two-stage architecture:

1. A **lexical reconstruction module** that encourages token-level fidelity.  
2. A **style-conditional cross-encoder** to maintain semantic coherence.

Incorporating external knowledge bases and reinforcement learning for style fidelity can further refine counterspeech generation.

---

## How to Run the Code

Since the repository currently has only a baseline code and an EDA code, just download both these files separately and run on Google Colab or any other local python environment.
