# 応用編
本パートでは Microsoft Sentinel の Azure OpenAI の活用ストーリーをカスタマイズで考えてみましょう。

# ユースケースアイデア
## ユースケース 1 - MITRE 戦術の概要を説明してもらう
分析ルールに含まれる MITRE 戦術について、補足情報としてコメントに付与するなどが考えられます。
```
MITRE 戦術 ###[ "LateralMovement", "Execution" ]### について、100 文字以内で解説してほしい。
```
<img width="697" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/6e1ccaba-7d4f-4aec-8219-16e0e29a5416">

## ユースケース 2 - ハンティングするための KQL を生成させる
分析ルール名や補足内容、ChatGPT の一次応答を用いて、インシデントを判定するための KQL を生成させます。
```
Microsoft Sentinel で脅威を調査するための KQL を提案してほしい

###
あなたのAzureストレージアカウント「Sample-Storage」に実行可能ファイルを異常な方法でアップロードした人がいます。 この警告はADLS Gen2トランザクションによって引き起こされました。
###
```
<img width="698" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/b5bd198f-5d6c-41c5-8c22-a47acb566bd3">

