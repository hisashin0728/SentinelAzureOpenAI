# FAQ
## Q. ロジックアプリに Azure OpenAI の API キーを埋め込むのはセキュアでは無いので、どうしたら良いでしょうか？
- Azure OpenAI の API キーを格納する場所として、Azure KeyVault を活用ください。
- 本ワークショップでは簡素化するため、ロジックアプリ内のコード上に埋め込んでいますが、実装レベルにおいては Azure KeyVault のシークレット情報として格納することを推奨します。

## Q. Azure OpenAI と OpenAI は何が違うのでしょうか？
- Azure リソースから閉域網によるアクセスが出来る、Azure AD 認証が使える、Azure サポートプラン、Azure 課金などの違いがあります。
- OpenAI社はOpenAIも運営していますが、Azure OpenAIとは何点か違いがあります。Azure OpenAIは、DALL-EやOpenAI GPT-3といったモデルを基にした高度な言語AIを提供しています。
- Azureのセキュリティ面においての機能を活用でき、本番環境利用に向いています。対して本家のOpenAIは最新モデルが次々にでるため、これまでにない機能を提供していることが特徴です。
- 様々なサイトで比較・紹介がされていますので、ご確認下さい。

https://qiita.com/akiraokusawa/items/14c6008ac01855490e88
https://zenn.dev/microsoft/articles/e0419765f7079a

## Q. Azure OpenAI のデータ、プライバシー、セキュリティはどのようなものか？
- [公式サイト](https://learn.microsoft.com/ja-jp/legal/cognitive-services/openai/data-privacy?context=%2Fazure%2Fcognitive-services%2Fopenai%2Fcontext%2Fcontext)をご確認下さい。
https://learn.microsoft.com/ja-jp/legal/cognitive-services/openai/data-privacy?context=%2Fazure%2Fcognitive-services%2Fopenai%2Fcontext%2Fcontext


