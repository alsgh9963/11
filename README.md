# Path-based reasoning approach for knowledge graph completion using CNN-BiLSTM with attention mechanism

The code has been tested running under Python 3.6.5

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

### Data Pre-Processing :
```shell
bash make_story.sh --dataset <DATASETS>
```
     
### Options of ``make_story.sh``:
```
useage: [--dataset] - Dataset 이름 (NELL-995, FB15K-237, Countries, Kinship)
```   
-----------------------------------    

### Training and Testing :
```shell
bash run_main.sh 
--dataset <DATASETS>
--LSTM_hidden_size 100
--CNN_num_filter 50
--CNN_pooling_size 2
--batch_size 128
--num_epochs 50
--learning_rate 0.001
--patience 30
--log_name NELL_log
```

### Options of ``run_main.sh``:
```
useage: [--dataset] - Dataset 이름 (NELL-995, FB15K-237, Countries, Kinship)
        [--LSTM_hidden_size] - LSTM hidden unit의 size.
        [--CNN_num_filter] - CNN Filter의 갯수.
        [--CNN_pooling_size] - Pooling size.
        [--batch_size] - Training 과정에서의 Batch size.
        [--num_epochs] - Training 횟수.
        [--learning_rate] - 학습률.
        [--patience] - Early stopping할 Epochs 수.
        [--log_name] - Log file의 이름.
```   
----------------------------------

### Result:
||MAP|MRR|Hits@1|Hits@3|
|:-----------:|------------:|------------:|------------:|
|NELL-995|0.894|0.898|0.838|0.951|
|FB15K-237|0.652|0.660|0.544|0.708|
|Countries|0.947|0.947|0.916|0.986|
|Kinship|0.946|0.952|0.918|0.984|

# 4. Format of the dataset

``data/<DATASETS>/paths/<Relation>`` : Path Ranking Algorithm을 통해 추출된 Paths   
``data/<DATASETS>/tasks/<Relation>/graph.txt`` : Knowledge Graphs   
``data/<DATASETS>/tasks/<Relation>/train.pairs`` : Correct, Corrupt Train Data   
``data/<DATASETS>/tasks/<Relation>/train_pos`` : Correct Train Data   
``data/<DATASETS>/tasks/<Relation>/test.pairs`` : Correct, Corrupt Test Data   
``data/<DATASETS>/tasks/<Relation>/sort_test.pairs`` : 정렬된 Test Data   


