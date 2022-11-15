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

# How to Run
Most of the code is based on https://github.com/yjang43/pushingonreadability_transformers

1. Go to pushingonreadability_transformers-master folder

2. Create 5-Fold of a dataset for training.
```bash
python kfold.py --corpus_path mainland.csv --corpus_name mainland
```
- Stratified folds of data will save under file name _"data/mainland.{k}.{type}.csv"_.
_k_ means _k_-th of the K-Fold and _type_ is either train, valid, or test.


3. Fine-tune on dataset with pretrained model.
```bash
python train.py --corpus_name mainland --model chinese-macbert-large --learning_rate 2e-5
```

4. Collect output probability with a trained model.

```bash
python inference.py --checkpoint_path checkpoint/mainland.chinese-macbert-large.0.14 --data_path data/mainland.0.test.csv
```

5. Collect features and combine with output probability.

6. Go to pushingonreadability_traditional_ML-master folder.

7. Create result folder and put the combination of output probability and features file into the folder. 
    For example: mainland.0.train.combined.csv,mainland.0.test.combined.csv
    
8. Fed into Classifiers
```bash
python nonneural-classification.py -r
```
- -r means random forest classifier<br>
- -s means SVM<br>
- -g means XGB<br>

## References
Pushing on Text Readability Assessment: A Transformer Meets Handcrafted Linguistic Features<br>
https://aclanthology.org/2021.emnlp-main.834v2.pdf

Tools:<br>
https://github.com/brucewlee/pushingonreadability_traditional_ML<br>
https://github.com/yjang43/pushingonreadability_transformers<br>

Most of our code are modifed from the above tools<br>
