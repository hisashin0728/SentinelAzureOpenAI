# 演習. Azure OpenAI ロジックアプリを用いて、メールによる応答を実践する
まずは Azure OpenAI の活用イメージを掴むため、Office 365 メールトリガーを用いた Azure OpenAI との入出力を試してみましょう。

# 実行イメージ
メールアドレスに問い合わせを行うと、Azure OpenAI が回答してくれる bot サービスの作成します。
- メール送信<BR>
  <img width="300" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/d3dbb99a-1689-455e-98ca-6372bb3477c4"><BR>
- メール受信<BR>
  <img width="560" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/024802d3-351b-478c-97d8-f6f39f2f0f6e">

# 事前準備
- 自テナント内でメール受信可能なアカウントを 1 つ作成して下さい。
  - 本ワークショップでは ``openai@[テナント名].onmicrosoft.com`` としています。

# 1.テンプレートの概要
以下 ARM テンプレートを用いて、ロジックアプリを導入します。
- Office 365 環境のメールアドレスに対して、``OpenAI question`` タイトルでメールを受信すると、リクエストを Azure OpenAI に問い合わせを行い、返信を行います。
- 本演習より、ロジックアプリを用いた Azure OpenAI への入出力の設定方法を理解することが出来ます。
<img width="219" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/f4a7ec8e-84b1-4a7f-8bb4-db53ccda6b4b">

# 2. テンプレートの導入
以下 GitHub レポジトリの ARM テンプレートを導入して下さい。

https://github.com/format81/AzureOpenAI-LogicApp

# 3. 設定方法
展開されたロジックアプリを起動するに際して、幾つか設定が必要になります。
## 3.1 API 認証 (Office 365 コネクタ) の設定
ロジックアプリでは Office 365 のメールアドレスに対して API 認証が必要になります。
API 接続の編集から、「承認する」を押してメール受信するアドレスで認証して下さい（本例では ``openai@[テナント名].onmicrosoft.com`` で認証します）
<img width="427" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/978a67e1-ee65-4780-86d5-c53e8276923a">

## 3.2 ロジックアプリ内の編集
### 3.2.1 Azure OpenAI API キーの登録

  
# 謝辞
Special Thanks to 
https://github.com/format81/AzureOpenAI-LogicApp
