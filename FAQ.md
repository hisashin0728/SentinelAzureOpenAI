# FAQ
> 想定される FAQ 情報を以下まとめています。ご参考として下さい。

## Q. 実際に本演習を自社の本番環境に適用して試すことは可能でしょうか？
- 可能ですが、オープンソース扱いとなります。自社環境でご評価の上、ご検討下さい。
- 自社本番環境に導入する場合は、API キーの保護や Azure OpenAI の監査ログの有効化、課金監視なども合わせてご検討下さい。

## Q. ロジックアプリに Azure OpenAI の API キーを埋め込むのとマネージド ID を用いるのはどちらが推奨でしょうか？
- セキュリティの観点から、マネージド ID によるロジックアプリ側からの接続方式を推奨します。
- Azure OpenAI の接続のメリットになります。

## Q. たまにロジックアプリから Azure OpenAI に対してリクエストが失敗します。
- モデルで許可されている Prompt の最大リクエストサイズに引っ掛かっている可能性があります。prompt で依頼する内容を調整して量を減らすなどの工夫をしてみて下さい。
- 各モデルで許可されている最大リクエストトークン量は[公式サイト](https://learn.microsoft.com/en-us/azure/cognitive-services/openai/concepts/models#model-summary-table-and-region-availability)をご参照下さい。

```
{
  "error": {
    "message": "This model's maximum context length is 4097 tokens, however you requested 4158 tokens (1158 in your prompt; 3000 for the completion). Please reduce your prompt; or completion length.",
    "type": "invalid_request_error",
    "param": null,
    "code": null
  }
}
```

## Q. このような Azure OpenAI を活用した Microsoft Sentinel 活用を実施する場合、費用はどれぐらいかかりますか？
- Azure OpenAI の[価格表](https://azure.microsoft.com/ja-jp/pricing/details/cognitive-services/openai-service/#pricing)を参考として下さい。
  - 利用するモデル、prompt の量によって課金がかかります。
  - 2023.5 現在、```Text-Davinci``` モデルを用いた場合は $0.02 / 1,000 トークンになります。($0.1 / 5,000 トークン)

## Q. Azure OpenAI と OpenAI は何が違うのでしょうか？
- Azure リソースから閉域網によるアクセスが出来る、Azure AD 認証が使える、Azure サポートプラン、Azure 課金などの違いがあります。
- OpenAI 社は OpenAI を運営していますが、Azure OpenAI とは何点か違いがあります。
  - Azure OpenAI は、DALL-E や OpenAI GPT-3 といったモデルを基にした高度な言語 AI を提供しています。
  - Azure のセキュリティ面においての機能を活用でき、本番環境利用に向いています。
  - 対して本家の OpenAI は最新モデルが次々にでるため、これまでにない機能を提供していることが特徴です。
  - 様々なサイトで比較・紹介がされていますので、ご確認下さい。

https://qiita.com/akiraokusawa/items/14c6008ac01855490e88
https://zenn.dev/microsoft/articles/e0419765f7079a

## Q. Azure OpenAI のデータ、プライバシー、セキュリティはどのようなものか？
- [公式サイト](https://learn.microsoft.com/ja-jp/legal/cognitive-services/openai/data-privacy?context=%2Fazure%2Fcognitive-services%2Fopenai%2Fcontext%2Fcontext)をご確認下さい。
  - https://learn.microsoft.com/ja-jp/legal/cognitive-services/openai/data-privacy?context=%2Fazure%2Fcognitive-services%2Fopenai%2Fcontext%2Fcontext

## Q. IP アドレスや URL を ChatGPT に聞くことで、脅威インテリジェンス情報の置き換えになりますか？
- ChatGPT/GPT では脅威インテリジェンス情報をデータベースとして有している訳では無いため、prompt で聞いても脅威判定の応答は行われません。
- <img width="543" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/02c72102-b61e-482c-bff7-48a304686b11">

## Q. 画像モデルを用いた実践はありませんか？
- ```Dall-E``` モデルの活用は今後検討予定です。
- ニーズがあればワークショップを検討しますので、活用シナリオなどを添えて Issues に記録頂ければ幸いです。
