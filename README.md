# Robustness of Hybrid Models in Cross-domain Readability Assessment

## Abstract
Recent studies in automatic readability assessment have shown that hybrid models --- models that leverage both linguistically motivated features and neural models --- can outperform neural models.  However, most evaluations on hybrid models have been based on in-domain data in English. This paper provides further evidence on the contribution of linguistic features by reporting the first direct comparison between hybrid, neural and linguistic models on cross-domain data.  In experiments on a Chinese dataset, the hybrid model outperforms the neural model on both in-domain and cross-domain data.  Importantly, the hybrid model exhibits much smaller performance degradation in the cross-domain setting, suggesting that the linguistic features are more robust and can better capture salient indicators of text difficulty. 

## Tools
scikit-learn==0.24.1<br>
torch==1.11.0<br>
transformers==4.5.0<br>

## Pretrained Model
MacBERT: https://huggingface.co/hfl/chinese-macbert-large<br>
BERT: https://huggingface.co/bert-base-chinese<br>
BERT-wwm: https://huggingface.co/hfl/chinese-bert-wwm<br>
RoBERTa: https://huggingface.co/hfl/chinese-roberta-wwm-ext<br>

We use the learning rate of 2e-5 for all pretrained Model

## References
Pushing on Text Readability Assessment: A Transformer Meets Handcrafted Linguistic Features<br>
https://aclanthology.org/2021.emnlp-main.834v2.pdf

Most of our code are modifed from this paper<br>
Tools:<br>
https://github.com/brucewlee/pushingonreadability_traditional_ML<br>
https://github.com/yjang43/pushingonreadability_transformers<br>
