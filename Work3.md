# 振り返り
演習 1、および演習 2 を通じて、ロジックアプリを通じて Azure OpenAI の GPT/ChatGPT に問い合わせをかけられることが理解できたと思います。
あらためて、Azure OpenAI について振り返ってみましょう。

# Azure OpenAI のモデル
モデルデプロイで設定した Azure OpenAI のモデルは様々なモデルが提供されていますが、2023.5 現在 Azure OpenAI のモデルと用途は以下のような違いがあります。

|  GPT model  | 概要 |
| ---- | ---- |
| GPT-3.5  | - 米国東部、西ヨーロッパで利用可能<BR>- 推論時間や性能を最適化するためのケース別モデル<BR>- 幅広いユースケースに対応 |
| ChatGPT<BR>(preview) | - ほとんどのユースケースでファーストチョイス<BR>- Azure OpenAI Service で最も経済的なモデル<BR>- チャットだけでなく、すべてのワークロードに対応|
| GPT4<BR>(preview) |- 問題解決能力、推論能力の向上<BR>- 繰り返しの洗練(コードエラーの修正、ストーリーを繰り返し考える)<BR>- トークン制限の増加（長いコンテンツに効果的）|

情報元：
https://www.youtube.com/watch?v=tFgqdHKsOME

<img width="798" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/3a47d0fb-5124-4c3d-a4cf-e2194c30db33">

# Azure OpenAI の使い方
Azure OpenAI のプレイグラウンドを用いて、幾つかのモデル活用パターンを考えてみましょう。
https://oai.azure.com/portal/playground
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/28fd2466-be5d-4b14-94f3-c31a8c348dfa)

## 1. 基礎：要約 (Summarization)
GPT に対してコンテキストを要約依頼する例です。
インストラクションとコンテキストは ```###``` や ```"""``` を使って分離することを覚えましょう。

```
下記のテキストを一文で説明してください。

テキスト: """日本は前半、クロアチアにボールを保持されて押し込まれましたが、ゴールキーパーの権田修一選手がシュートを防ぐなどしてしのぎ、前半43分には、右サイドのコーナーキックから短いパスを受けた堂安律選手がクロスボールを入れて、最後は前田大然選手が左足で押し込み、日本が先制しました。後半は、10分にクロアチアのクロスボールからイバン・ペリシッチ選手にヘディングでシュートを決められ同点とされて、試合は1対1のまま今大会初めての延長戦に入り、試合は最終的にペナルティーキック戦に入りました。
日本は先攻となりましたが、1人目の南野拓実選手と2人目の三笘選手が連続で相手のゴールキーパーにシュートを防がれました。そして日本が1対2で迎えた4人目でキャプテンの吉田麻也選手も決められず、最後はクロアチアの4人目に決められてペナルティーキック戦で1対3で敗れました。"""
```

## 2. 基礎：質問応答 (Question-Answering)
コンテキストを使って業界独自の文書や企業内 FAQ など、OpenAI GPT 知らないさまざまな文書も対象にすることが出来ます。

```
以下のテキストを使って下記の質問に答えてください。もし答えがない場合には、「私は知らない」と答えてください。

コンテキスト: """Surface Book が空の状態から完全に充電されるまで、2 ～ 4 時間かかります。Surface Book を充電しながらゲームやビデオ ストリーミングのような電力消費の多い活動に Surface を使用している場合、さらに時間がかかる可能性があります。電源アダプターに付いている USB ポートを使って、Surface Book の充電中にスマートフォンなどの他のデバイスを充電することもできます。電源アダプターの USB ポートは充電専用であり、データ転送用ではありません。"""

質問: Surface Book の充電時間を節約するにはどうするか。
```

<img width="700" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/2d8cce9f-7c04-400d-b158-4e37029774d7">

## 3. 基礎：分類 (Classification)
インテント分類など、カスタムな分類にも対応出来ます。

```
テキストを不満、普通、満足の感情に分類してください。
テキスト: 食事はまあまあでした。
```

<img width="488" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/a81c66de-e7e6-41fa-8a8e-4f3715f849c5">

## 4. 基礎：テキスト挿入 (Insertion)
プロンプトとプレフィックスプロンプトの間にテキストを挿入させる活用事例です。

```
今日のセミナーの目次です。

1. OpenAI紹介
[ここに挿入してください]
2. OpenAIの仕組み
3. OpenAIの利用方法
4. OpenAIの導入手順
5. OpenAIの導入メリット
6. OpenAIの導入デメリット
7. OpenAIの事例
8. OpenAIを活用したAI開発
9. OpenAIの未来展望
10. まとめ
```

<img width="689" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/bbe61c7f-5c82-4bf7-8112-3484a72c1f7d">

