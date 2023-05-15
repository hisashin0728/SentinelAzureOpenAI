# 演習. Microsoft Sentinel のインシデントから Azure OpenAI に問い合わせをかける
Microsoft Sentinel のインシデント発生時に、Azure OpenAI に問い合わせを行い、分析ルールの日本語訳を行ってみましょう。

# 1.テンプレートの概要
以下 ARM テンプレートを用いて、ロジックアプリを導入します。

- Microsoft Sentinel ではオートメーション機能を用いて、Logic Apps を通じて様々な自動化操作を行う機能を提供しています。 
- テンプレートを導入することで、インシデント発生時に Azure OpenAI に問い合わせを行い、prompt を用いて分析ルール補足分の翻訳を実行します。

# 2. テンプレートの導入
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelAzureOpenAI%2Fblob%2Fmain%2Ftemplate%2Ftemplate.json)

# 3. 
