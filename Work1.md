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
本ロジックアプリでは Azure OpenAI の API キーを登録する必要があります。
- Azure OpenAI の API キーを確認
<img width="837" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/84b99d6d-8f4b-4b55-82e0-54e9272e93c0">
- ロジックアプリ内に Azure OpenAI のキーを設定する
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/9382ed31-7de0-4f16-a606-55e65f03bfdf)

### 3.2.2 ロジックアプリの RESTAPI に対して、自テナント内の情報にカスタマイズする
展開されたロジックアプリの REST API は URL がサンプルになっています。
自テナントに合わせた設定に更新して下さい。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/91fa2cd9-0b50-4dbc-b87b-ceac609612a1)

|  Parameter  | Sample |
| ---- | ---- |
| https://your-resource-name.openai.azure.com | https://(自分のエンドポイント).openai.azure.com |
| deployment-id | モデル デプロイ名 |

### 3.2.3 返信先のメールアドレスに認証する
最後のロジックアプリのステップは返信先のメールアドレスになります。
メールの送信者（差出人）に対して Azure OpenAI から得られた ``text`` を返しています。  
<img width="525" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/42c05c55-e8b3-48c6-a996-29ba8b6e9c25">

# 4. テスト
設定したメールアドレス対して Title:「OpenAI question」でテストしてみましょう。<BR>
<img width="299" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/5e1fdd8b-7095-4228-9775-b8a1ba4b3326">

# 5. 確認ポイント
  - ロジックアプリから Azure OpenAI へはどのような RESTAPI での通信が行われたでしょうか？
  - ロジックアプリから Azure OpenAI にチャットする内容はどのような内容で問い合わせが行われましたか？
  - Azure OpenAI に対して、パラメータ設定はありましたか？
