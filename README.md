# はじめに
Microsoft Sentinel / Azure Open AI 演習のレポジトリです。

# 演習の目的
- Microsoft Sentinel から Azure OpenAI を活用する環境を作成する
- 本演習を通じて、ロジックアプリと Azure OpenAI のモデルを理解する / Prompt の活用を考える

# 前提条件
- Microsoft Sentinel の環境を自テナントに有すること
- Azure OpenAI が利用可能であること (※ 2023.5.15 現在、Azure では事前申請が必要です)
  -   https://customervoice.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR7en2Ais5pxKtso_Pz4b1_xUOFA5Qk1UWDRBMjg0WFhPMkIzTzhKQ1dWNyQlQCN0PWcu
- Microsoft Sentinel に対して、何らかの分析ルールによるアラート発砲が可能であること
  -   本演習では Microsoft Defender for Cloud とデータコネクタを接続し、Microsoft Defender for Cloud のサンプルアラートによる効果を想定しています。

# 演習内容
以下の順番で演習を実践して下さい。
- 事前準備 Azure OpenAI サービスの作成
- 演習1. Azure OpenAI ロジックアプリを用いて、メールによる応答を実践する
- [演習2. Microsoft Sentinel のインシデントトリガーを用いて、ロジックアプリを用いて Azure OpenAI に分析ルールの翻訳を実行させる](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work2.md)
- 演習3. Microsoft Sentinel のインシデント情報から Azure OpenAI への問い合わせをカスタマイズする
