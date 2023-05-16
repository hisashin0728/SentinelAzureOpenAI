# 事前準備
本演習を開始する前に、Azure OpenAI サービスを有効化する必要があります。
以下手順を参考に Azure OpenAI サービスを設定して下さい。

# 1. Azure OpenAI サービスの有効化
- Forms による審査が完了すると、対象のサブスクリプションに Azure OpenAI サービスを有効化することが出来ます。
- リソースグループ、リージョン、Azure OpenAI サービスの登録名称、価格レベルを設定して下さい。
  -   価格レベルは 2023.5 現在、```Standard S0``` のみとなります。
  -   ネットワーク設定はロジックアプリからの接続を演習で用いますので、「インターネットを含むすべてのネットワークがこのリソースにアクセスできます。」を選択してください。
-  リソースの作成は**約 7 分**ほどかかります。
<img width="424" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/8f0cd258-9e18-451a-89e3-b97b0f3ab415">

# 2. エンドポイントと API キーの確認
- サービス有効化が確認出来ましたら、エンドポイントと API キーを確認してください。
- エンドポイント
  - ![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/1c2e9a92-18cc-4b34-ab3a-273421537288)
- API Key
  - <img width="516" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/267a5d9f-4d3c-4f30-9283-e77233810950">

# 3. モデルのデプロイ
Azure OpenAI で用いるモデルを登録します。
「モデルデプロイ」-> 「モデル名」から、モデルを作成して下さい。
<img width="930" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/91b49758-4a63-48f3-a941-2f8e21f538db">

- 各モデルの違いは[公式ドキュメント](https://learn.microsoft.com/ja-jp/azure/cognitive-services/openai/concepts/models)をご参照下さい。
- 本演習では、最も良い結果が得られる Davinci を選定して下さい。
  -   ``text-davinci-003``
  -   ``gpt35-turbo``

# Next Action
モデルデプロイが完了しましたら、[演習 1](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work1.md) に移って下さい。
