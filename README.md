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
bash run_main.sh 
--dataset NELL-995
--LSTM_hidden_size 100
--CNN_num_filter 50
--CNN_pooling_size 2
--batch_size 128
--num_epochs 50
--learning_rate 0.001
--patience 30
--log_name NELL_log
```

Options of ``run_main.sh``:
```
useage: [--dataset] - Dataset 이름.
        [--LSTM_hidden_size] - LSTM hidden unit의 size.
        [--CNN_num_filter] - CNN Filter의 갯수.
        [--CNN_pooling_size] - Pooling layer의 size.
        [--batch_size] - Training 과정에서의 Batch size.
        [--num_epochs] - Training 횟수.
        [--learning_rate] - 학습률.
        [--patience] - Early stopping할 Epochs 수.
        [--log_name] - Log file의 이름.
```   
----------------------------------

Result:
```shell
  MAP  : 0.894
  MRR  : 0.898
Hits@1 : 0.838
Hits@3 : 0.951
```
