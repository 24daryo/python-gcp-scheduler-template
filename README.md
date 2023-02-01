# python-gcp-scheduler-template
Python + GCP(Functions, Pub/Sub, Scheduler)

## Cloud Function

### Deploy

#### オプション一覧

基本は`gcloud functions deploy YOUR_FUNCTION_NAME```でデプロイ

|prop|detail|
|--|--|
|--gen2 |第2世代にデプロイ。基本的には第2世代を利用|
|--region=YOUR_REGION|デプロイのリージョン。基本はasia-northeast1で東京を指定|
|--runtime=YOUR_RUNTIME|関数で利用する言語ランタイム。一覧は[こちら](https://cloud.google.com/functions/docs/concepts/execution-environment?hl=ja#runtimes)。Python3.11ならpython311を指定|
|--source=YOUR_SOURCE_LOCATION|関数のソースコードの場所を指定。3パターン存在。|
|--entry-point=YOUR_CODE_ENTRYPOINT||

#### 補足：--sourceのURIについて

1. Cloud Storageから指定するとき
  - gs:// で始まる Cloud Storage パスを指定
2. ローカルマシンからデプロイする場合
  - 実行ファイルのあるパスを指定
  - 例：`src/test/main.py`の場合 => --source=src/test
3. Cloud Source Repositoriesから指定するとき
  - https://source.developers.google.com/projects/PROJECT_ID/repos/REPOSITORY_NAME
    - PROJECT_ID : Google CloudのプロジェクトID
    - REPOSITORY_NAME : ソースリポジトリの名前
    
githubのこのテンプレートを利用する場合は`---source=./`

```console
gcloud functions deploy YOUR_FUNCTION_NAME \
[--gen2] \
--region=YOUR_REGION \
--runtime=YOUR_RUNTIME \
--source=YOUR_SOURCE_LOCATION \
--entry-point=YOUR_CODE_ENTRYPOINT \
TRIGGER_FLAGS
```


- YOUR_FUNCTION_NAME
  - デプロイされた関数の名前
