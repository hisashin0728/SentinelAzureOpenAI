# 演習. Microsoft Sentinel のインシデントから Azure OpenAI に問い合わせをかける
Microsoft Sentinel のインシデント発生時に、Azure OpenAI に問い合わせを行い、分析ルールの日本語訳を行います。

# 実行イメージ
Sentinel のインシデントが検知すると、分析ルールの補足 (Description) を ChatGPT が翻訳するテンプレートになります。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/74a2ad6a-a4fc-4cb8-b448-fcd896e3597b)

# 1.テンプレートの概要
以下 ARM テンプレートを用いて、ロジックアプリを導入します。

- Microsoft Sentinel ではオートメーション機能を用いて、Logic Apps を通じて様々な自動化操作を行う機能を提供しています。 
- テンプレートを導入することで、インシデント発生時に Azure OpenAI に問い合わせを行い、prompt を用いて分析ルール補足分の翻訳を実行します。

<img width="1080" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/20d3dc5b-09ff-4106-a049-fcd3bde4f364">

# 2. テンプレートの導入
以下から、ARM テンプレートをデプロイして下さい。<BR>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelAzureOpenAI%2Fmain%2Ftemplate.json)

# 3. 設定
演習 1 と同様にロジックアプリの内容を編集して下さい。
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

# 4. テスト
設定が完了しましたら、Microsoft Sentinel に対してアラートを発砲してみましょう。
- [Microsoft Defender for Cloud のサンプルアラート ( Defender for Cloud のコネクターを事前に設定）](https://learn.microsoft.com/ja-jp/azure/defender-for-cloud/alert-validation#generate-sample-security-alerts)

# 5. 確認ポイント
  - Sentinel 分析ルールの翻訳は、どのように行われましたか？
  - Azure OpenAI に対して、どのような prompt を送りましたか？
  - Sentinel インシデント更新はどのように行われましたか？
  - Azure OpenAI に対して、パラメータ設定はありましたか？
