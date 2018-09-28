# 基於Python Elasticsearch Client 與 aws-requests-auth，以Sign4簽署協議進行AWS Elasticsearch數據操作

## 目的：
有鑒於目前對於AWS Elasticsearch的中文資源相當稀少，因此分享個人對於AWS Elasticsearch&Kibana的完整建置教學。

## 前置作業：
```text
$ git clone https://github.com/TIS-JOEY/AWS_Elasticsearch_aws-requests-auth_Python_Interface.git
$ pip install aws-requests-auth
$ pip install elasticsearch
```

## 批次上傳
### 上傳資料格式
| _index | _type | _id | 欄名1 | 欄名2 | 欄名3 | 欄名... |
| --- | --- | --- | --- | --- | --- | --- |
| Taiwan | Tutorial | 1 | abc | def | ghi | jkl |
| Taiwan | Tutorial | 2 | mno | pqr | stu | vwx |

前三欄為固定格式，Elasticsearch中的_index等同於RDBMS的Database，_type等同於RDBMS的Table，而_id就等於id，其餘則依你的需求進行欄位上傳。
Elasticsearch的分散式儲存系統也是採Nosql格式儲存(以JSON格式)，因此每筆資料的欄位可彈性調整，並不用像RDBMS需先預定義好欄位且不得更動。
> AWS_Elasticsearch_bulkUpload.py所能讀取的資料格式為xlsx檔。



### 批次資料上傳說明
IAM user的access key id與IAM user的secret access key的取得教學，可至下方傳送門查看
* [AWS IAM 建置教學](aws-iam-jian-zhi-jiao-xue.md)

欲寫入id之起始位置代表的是你希望從哪一個id號開始寫入，因為AWS Elasticsearch中若在同一個index和type時，id是獨一無二的，若AWS Elasticsearch發現id號衝突時，會直接進行覆蓋(更新)。

```text
import AWS_Elasticsearch_bulkUpload

awses = AWS_Elasticsearch_bulkUpload.AWSes(access_key = 'IAM user的 access key id',
				  secret_access_key = 'IAM user的secrect access key',
				  host = 'AWS Elasticsearch domain',
				  region = 'AWS設置地區')

awses.login()
awses.create_bulk('欲上傳原始檔目錄位置(須為xlsx檔格式)','暫存檔目錄位置(須為json檔格式)','(欲寫入id之起始位置)')
```




有關於AWS Elasticsearch與Kibana建置與連結可至以下傳送門查看
* [AWS_Elasticsearch-Kibana_建置教學](https://github.com/TIS-JOEY/AWS_Elasticsearch-Kibana_Setup_Tutorial)







資料來源：

Python Elasticsearch Client ：https://elasticsearch-py.readthedocs.io/en/master/ 

aws-requests-auth：https://github.com/DavidMuller/aws-requests-auth 
