# 応用編
> ここからは Microsoft Sentinel のインシデントを更に活用するための Azure OpenAI 活用を考えてみましょう
本パートでは Microsoft Sentinel の Azure OpenAI の活用ストーリーをカスタマイズで考えてみましょう。

# 1. ユースケースアイデア
> Microsoft Sentinel のインシデント情報から、セキュリティオペレーターが活用するための様々なアイデア

## ユースケース 1 - MITRE 戦術の概要を説明してもらう
分析ルールに含まれる MITRE 戦術について、補足情報としてコメントに付与するなどが考えられます。
```
MITRE 戦術 ###[ "LateralMovement", "Execution" ]### について、100 文字以内で解説してほしい。
```
<img width="697" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/6e1ccaba-7d4f-4aec-8219-16e0e29a5416">

## ユースケース 2 - インシデントタイトルとインシデント補足から、要約をまとめさせる
インシデント情報を ChatGPT にまとめて送り、インシデント要約をまとめさせるアイデアです。
```
私はセキュリティアナリストです。
セキュリティインシデントの内容を1000文字以内で概要にまとめてほしい。

### [インシデントタイトル], [インシデントの説明], [インシデントのエンティティ] ###
```

## ユースケース 3 - ハンティングするための KQL を生成させる
分析ルール名や補足内容、ChatGPT の一次応答を用いて、インシデントを判定するための KQL を生成させます。
```
Microsoft Sentinel で脅威を調査するための KQL を提案してほしい

###
あなたのAzureストレージアカウント「Sample-Storage」に実行可能ファイルを異常な方法でアップロードした人がいます。 この警告はADLS Gen2トランザクションによって引き起こされました。
###
```
<img width="698" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/b5bd198f-5d6c-41c5-8c22-a47acb566bd3">

# 2. 演習 インシンデント情報を用いて、Azure OpenAI に様々なリクエストをかけてみる
> 様々なユースケースを用いて、Azure OpenAI にリクエストをかけてみましょう

インシデント情報から、ロジックアプリを用いて Azure OpenAI の ChatGPT/GPT3 に以下のリクエストをかけるテンプレートを試してみましょう。
- インシデントの要約
- インシデント補足情報の日本語化
- インシデント

# 3. 設定
これまでの演習と同様に、ロジックアプリの内容を編集して下さい。
## 3.1 ロジックアプリ - Sentinel レスポンダーロールの付与
ロジックアプリから Microsoft Sentinel のインシデントを更新させるため、ロジックアプリのマネージド ID に対して、「Sentinel レスポンダー」ロールの付与を行ってください。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/0be09f07-f4de-46b9-89c8-c1710fbda62a)
  
## 3.2 ロジックアプリ - API キーの付与
本ロジックアプリでは Azure OpenAI の API キーを登録する必要があります。
- Azure OpenAI の API キーを確認
<img width="837" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/84b99d6d-8f4b-4b55-82e0-54e9272e93c0">

- ロジックアプリ内に Azure OpenAI のキーを設定する
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/9382ed31-7de0-4f16-a606-55e65f03bfdf)

## 3.3 ロジックアプリ - RESTAPI の編集
展開されたロジックアプリの REST API は URL がサンプルになっています。
自テナントに合わせた設定に更新して下さい。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/91fa2cd9-0b50-4dbc-b87b-ceac609612a1)

|  Parameter  | Sample |
| ---- | ---- |
| https://your-resource-name.openai.azure.com | https://(自分のエンドポイント).openai.azure.com |
| deployment-id | モデル デプロイ名 |

## 3.4 Sentinel - プレイブックに対して「アクセスの許可」を設定する
展開されたロジックアプリに対して Microsoft Sentinel がアクセスできるように、「設定」よりプレイブックのアクセス許可を与えます。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/4d86732a-8013-4430-93f5-452f154491c4)

## 3.5 Sentinel - オートメーションルールでプレイブックを自動起動させる
最後に、インシデント発生時にプレイブックが起動するようにオートメーションルールを作成します。
もし、メール通知などのプレイブックを事前設定されている場合は、通知前に設定することで和訳された内容を通知することが出来るようになります。
<img width="372" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/8fee8add-b8c7-4fc2-9943-9389c4d30b38">


<img width="434" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/fef324ce-d35f-4338-802f-8fe987bd766f">

# 3. テンプレートの導入
以下から、ARM テンプレートをデプロイして下さい。<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelAzureOpenAI%2Fmain%2FtemplateEnrichment.json)



