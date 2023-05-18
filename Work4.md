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

<img width="434" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/fef324ce-d35f-4338-802f-8fe987bd766f">

# 3. テンプレートの導入
以下から、ARM テンプレートをデプロイして下さい。<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelAzureOpenAI%2Fmain%2FtemplateEnrichment.json)



