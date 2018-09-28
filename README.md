# AWS_Elasticsearch_Python_Interface

# 基於Python Elasticsearch Client 與 aws-requests-auth，以Sign4簽署協議進行AWS Elasticsearch數據操作


##前置作業：
```text
$ pip install aws-requests-auth
$ pip install elasticsearch
```

##批次上傳
#上傳資料格式
| _index | _type | _id | 欄名1 | 欄名2 | 欄名3 | 欄名... |
| --- | --- | --- | --- | --- | --- | --- |
| Taiwan | Tutorial | 1 | abc | def | ghi | jkl |
| Taiwan | Tutorial | 2 | mno | pqr | stu | vwx |





Python Elasticsearch Client 
資料來源：https://elasticsearch-py.readthedocs.io/en/master/ 

aws-requests-auth
資料來源：https://github.com/DavidMuller/aws-requests-auth 
