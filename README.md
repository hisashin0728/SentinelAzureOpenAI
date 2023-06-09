# はじめに
> Microsoft Sentinel / Azure Open AI 演習のレポジトリです。

Microsoft Sentinel のインシデント作成をトリガーに Azure OpenAI GPT/ChatGPT を用いた活用を体験いただくレポジトリになります。
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/96135a01-3aff-471a-8a37-0c373fd50db4)

# 演習の目的
> 本演習の目的は Microsoft Sentinel のインシデントを Azure OpenAI を用いて活用するためのトレーニングコンテンツです。

- Microsoft Sentinel から Azure OpenAI を活用する環境を作成する
- 本演習を通じて、ロジックアプリと Azure OpenAI のモデルを理解する / Prompt の活用を考える

# 前提条件
> 前提条件を以下に示します。演習によるリソース作成、利用分は有償になります。

- Microsoft Sentinel の環境を自テナントに有すること
- Azure OpenAI が利用可能であること **(※ 2023.5.15 現在、Azure では事前申請が必要です)**
  -   https://customervoice.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR7en2Ais5pxKtso_Pz4b1_xUOFA5Qk1UWDRBMjg0WFhPMkIzTzhKQ1dWNyQlQCN0PWcu
- Microsoft Sentinel に対して、何らかの分析ルールによるアラート発砲が可能であること
  -   本演習では Microsoft Defender for Cloud とデータコネクタを接続し、Microsoft Defender for Cloud のサンプルアラートによる効果を想定しています。

# 演習内容
> ワークショップのコンテンツはこちらです。

以下の順番で演習を実践して下さい。
- [事前準備 Azure OpenAI サービスの作成](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/preconfiguration.md)
- [演習1. Azure OpenAI ロジックアプリを用いて、メールによる応答を実践する](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work1.md)
- [演習2. Microsoft Sentinel のインシデントトリガーを用いて、ロジックアプリを用いて Azure OpenAI に分析ルールの翻訳を実行させる](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work2.md)
- [振り返り Azure OpenAI の prompt 活用を考える](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work3.md)
- [演習3. [応用] Microsoft Sentinel のインシデント情報から Azure OpenAI への問い合わせをカスタマイズする](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work4.md)
- [FAQ](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/FAQ.md)

# 免責事項
> 本レポジトリの演習は課金が発生します。

- 本レポジトリの演習によって発生するコストについては、利用するユーザーが責任を負います。
- 本レポジトリの演習によって作成される環境から出力される内容について、作成者は責任を負いません。
- 本レポジトリはオープンソースです。 
