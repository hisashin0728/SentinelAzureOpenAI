# 演習. Azure OpenAI ロジックアプリを用いて、メールによる応答を実践する
まずは Azure OpenAI の活用イメージを掴むため、Office 365 メールトリガーを用いた Azure OpenAI との入出力を試してみましょう。

# 1.テンプレートの概要
以下 ARM テンプレートを用いて、ロジックアプリを導入します。

- Microsoft Sentinel ではオートメーション機能を用いて、Logic Apps を通じて様々な自動化操作を行う機能を提供しています。 
- テンプレートを導入することで、インシデント発生時に Azure OpenAI に問い合わせを行い、prompt を用いて分析ルール補足分の翻訳を実行します。

# 2. テンプレートの導入
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelAzureOpenAI%2Fblob%2Fmain%2Ftemplate%2Ftemplate.json)

# 3. 
