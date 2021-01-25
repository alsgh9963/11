# Path-based reasoning approach for knowledge graph completion using CNN-BiLSTM with attention mechanism

# 1. Statistics of datasets used in this code
||#entities|#relations|#train|#dev|#test|#tasks|
|:-----------:|------------:|------------:|------------:|------------:|------------:|------------:|
|NELL-995|75,492|200|154,213|5,000|5,000|12|
|FB15K-237|14,541|237|272,115|17,535|20,466|10|
|Countries|272|2|1,158|68|72|2|
|Kinship|104|26|6,926|769|1,069|26|

# 2. Installing requirement packages

```bash
pip install -r requirements.txt
```

# 3. Reproducing results

## NELL-995

Data Pre-Processing :
```shell
bash make_story.sh --dataset NELL-995
```

Options of ``make_story.sh``:
```
useage: [--dataset] - Dataset 이름.
```   
-----------------------------------    

Train & Test :
```shell
python run_bert_triple_classifier.py 
--task_name kg
--do_train  
--do_eval 
--do_predict 
--data_dir ./data/WN11 
--bert_model bert-base-uncased 
--max_seq_length 20 
--train_batch_size 32 
--learning_rate 5e-5 
--num_train_epochs 3.0 
--output_dir ./output_WN11/  
--gradient_accumulation_steps 1 
--eval_batch_size 512
```

Result:
```shell
  MAP  : 0.894
  MRR  : 0.898
Hits@1 : 0.838
Hits@3 : 0.951
```
