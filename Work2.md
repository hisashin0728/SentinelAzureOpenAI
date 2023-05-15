# 演習. Microsoft Sentinel のインシデントから Azure OpenAI に問い合わせをかける
Microsoft Sentinel のインシデント発生時に、Azure OpenAI に問い合わせを行い、分析ルールの日本語訳を行ってみましょう。

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

# 3. 設定準備
## 3.1 Azure Open AI
