# 演習. Azure OpenAI ロジックアプリを用いて、メールによる応答を実践する
まずは Azure OpenAI の活用イメージを掴むため、Office 365 メールトリガーを用いた Azure OpenAI との入出力を試してみましょう。

# 1.テンプレートの概要
以下 ARM テンプレートを用いて、ロジックアプリを導入します。
- Office 365 環境のメールアドレスに対して、``OpenAI question`` タイトルでメールを受信すると、リクエストを Azure OpenAI に問い合わせを行い、返信を行います。
- 本演習より、ロジックアプリを用いた Azure OpenAI への入出力の設定方法を理解することが出来ます。
<img width="219" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/f4a7ec8e-84b1-4a7f-8bb4-db53ccda6b4b">

# 2. テンプレートの導入
以下より、ARM テンプレートを導入して下さい。
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fgithub.com%2Fformat81%2FAzureOpenAI-LogicApp%2Fblob%2Fmain%2Fazuredeploy.json)

# 3. 

# 謝辞
Special Thanks to 
https://github.com/format81/AzureOpenAI-LogicApp
