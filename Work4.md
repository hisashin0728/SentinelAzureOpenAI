# 応用編
> ここからは Microsoft Sentinel のインシデントを更に活用するための Azure OpenAI 活用を考えてみましょう

本パートでは Microsoft Sentinel の Azure OpenAI の更なる活用ストーリーを実践してみるパートになります。

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

# 3. テンプレートの導入
以下から、ARM テンプレートをデプロイして下さい。<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelAzureOpenAI%2Fmain%2FtemplateEnrichment.json)

# 3. 設定
これまでの演習と同様に、[ロジックアプリの内容を編集して下さい。](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work2.md#3-%E8%A8%AD%E5%AE%9A)
 - Azure OpenAI RESTAPI URIの編集
 - ロジックアプリ / マネージド ID の「**Sentinel レスポンダー**」、「**Cognitive Services OpenAI User**」ロールの付与
 - Microsoft Sentinel ロジックアプリ実行権限設定
 - Microsoft Sentinel オートメーションルールの作成

# 4. テスト
> サンプルアラートを発砲してみましょう。ChatGPT/GPT3 を用いることで、どのような情報が付与されましたか？

テンプレートによって実現できたこと
 - **ルール説明の自動和訳**
  - ![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/a47781f4-9cc0-45d3-b531-26211e89b6d5)
 - **タグ情報の追加**
  - ![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/7ffc7844-2471-47ff-9572-a0e1a82dd5ce)
 - **インシデントのサマリー要約**
  - ![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/f15064d4-847f-4940-ae90-29274f96773c)
 - **インシデントタスクに KQL の提案**
  - <img width="316" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/c44c5510-4f77-49fe-9331-6e6abb0e6095">

# 5. 他にどのようなアイデアがありますか？
> デプロイされているテンプレートをカスタマイズして、自分なりの AI 活用を考えてみて下さい。

# 6. お疲れさまでした！これにて終了になります。
> ここまでお疲れさまでした。作成したリソースグループを削除してクリーンナップして下さい。

質問事項などを [FAQ](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/FAQ.md) にまとめています。合わせてご参照下さい。
ご意見などございましたら、[Discussion](https://github.com/hisashin0728/SentinelAzureOpenAI/discussions) にてご連絡下さい。

  
  



