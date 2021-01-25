# Path-based reasoning approach for knowledge graph completion using CNN-BiLSTM with attention mechanism

# 1. Statistics of Datasets
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

```shell
python3 run_bert_relation_prediction.py 
--task_name kg  
--do_train  
--do_eval 
--do_predict 
--data_dir ./data/FB15K 
--bert_model bert-base-cased
--max_seq_length 25
--train_batch_size 32 
--learning_rate 5e-5 
--num_train_epochs 20.0 
--output_dir ./output_FB15K/  
--gradient_accumulation_steps 1 
--eval_batch_size 512
```

