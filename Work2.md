# 演習. Microsoft Sentinel のインシデントから Azure OpenAI に問い合わせをかける
> Microsoft Sentinel のインシデントトリガーによる Azure OpenAI 連携を実践してみましょう

Microsoft Sentinel のインシデント発生時に、Azure OpenAI に問い合わせを行い、分析ルールの日本語訳を行います。

# 実行イメージ
Sentinel のインシデントが検知すると、分析ルールの補足 (Description) を ChatGPT が翻訳するテンプレートになります。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/74a2ad6a-a4fc-4cb8-b448-fcd896e3597b)

# 事前準備
- 本演習で作成するリソース（例：ロジックアプリなど）のためのリソースグループを作成して下さい
　- 演習 1 と同じリソースグループでも OK です
  -　以下設定例です。リージョンは東日本を前提として下さい
    - リソースグループ名 ``rg-Sentinel-AzureOpenAI-Workshop``
    - リージョン ``Japan East``
  
<img width="620" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/72c9e870-063e-45b1-9028-2f4f9d952076">

# 1.テンプレートの概要
以下 ARM テンプレートを用いて、ロジックアプリを導入します。

- Microsoft Sentinel ではオートメーション機能を用いて、Logic Apps を通じて様々な自動化操作を行う機能を提供しています。 
- テンプレートを導入することで、インシデント発生時に Azure OpenAI に問い合わせを行い、prompt を用いて分析ルール補足分の翻訳を実行します。

<img width="1080" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/20d3dc5b-09ff-4106-a049-fcd3bde4f364">

# 2. テンプレートの導入
以下から、ARM テンプレートをデプロイして下さい。<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelAzureOpenAI%2Fmain%2Ftemplate.json)

# 3. 設定
演習 1 と同様にロジックアプリの内容を編集して下さい。
## 3.1 ロジックアプリ - マネージド ID に対するロールの付与
ロジックアプリから Microsoft Sentinel のインシデントを更新させるため、ロジックアプリのマネージド ID に対して、以下 2 つのロールを付与します。<BR>
（演習1とは異なり、マネージド ID による認証でよりセキュアな接続を行います）
- **Sentinel レスポンダー**
- **Cognitive Services OpenAI User**

[2023.5.18 Update] Azure OpenAI のリクエストに対しても、[マネージド ID 経由で「Cognitive Service OpenAI User」権限で接続が出来るようになりました！](https://zenn.dev/microsoft/articles/call-openai-from-logicapps-with-managedid)

<img width="826" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/aee56068-05b3-4455-a04c-f1595b5d29e8">

  
## 3.2 ロジックアプリ - RESTAPI の編集
展開されたロジックアプリの REST API は URL がサンプルになっています。
自テナントに合わせた設定に更新して下さい。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/91fa2cd9-0b50-4dbc-b87b-ceac609612a1)

|  Parameter  | Sample |
| ---- | ---- |
| https://your-resource-name.openai.azure.com | https://(自分のエンドポイント).openai.azure.com |
| deployment-id | モデル デプロイ名 |

## 3.3 Sentinel - プレイブックに対して「アクセスの許可」を設定する
展開されたロジックアプリに対して Microsoft Sentinel がアクセスできるように、「設定」よりプレイブックのアクセス許可を与えます。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/4d86732a-8013-4430-93f5-452f154491c4)

## 3.4 Sentinel - オートメーションルールでプレイブックを自動起動させる
最後に、インシデント発生時にプレイブックが起動するようにオートメーションルールを作成します。
もし、メール通知などのプレイブックを事前設定されている場合は、通知前に設定することで和訳された内容を通知することが出来るようになります。
<img width="372" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/8fee8add-b8c7-4fc2-9943-9389c4d30b38">

# 4. テスト
> テストしてみましょう！

設定が完了しましたら、Microsoft Sentinel に対してアラートを発砲してみましょう。
- [Microsoft Defender for Cloud のサンプルアラート ( Defender for Cloud のコネクターを事前に設定）](https://learn.microsoft.com/ja-jp/azure/defender-for-cloud/alert-validation#generate-sample-security-alerts)

# 5. 確認ポイント
> 確認してみましょう！

  - Sentinel 分析ルールの翻訳は、どのように行われましたか？
  - Azure OpenAI に対して、どのような prompt を送りましたか？
  - Sentinel インシデント更新はどのように行われましたか？
  - Azure OpenAI に対して、パラメータ設定はありましたか？

# 6. Next Action
> お疲れさまでした！

次の[振り返り](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work3.md)に移って下さい。 

