# 1. 振り返り
> これまでの演習で実践できたこと

演習を通じて、ロジックアプリを通じて Azure OpenAI の GPT/ChatGPT に問い合わせを行えることが理解できましたでしょうか？
あらためて、Azure OpenAI について振り返ってみましょう。

# 2. Azure OpenAI のモデル
> Azure OpenAI で定義したモデルを理解する

モデルデプロイで設定した Azure OpenAI のモデルは様々なモデルが提供されていますが、2023.5 現在 Azure OpenAI のモデルと用途は以下のような違いがあります。

|  GPT model  | 概要 |
| ---- | ---- |
| GPT-3.5  | - 米国東部、西ヨーロッパで利用可能<BR>- 推論時間や性能を最適化するためのケース別モデル<BR>- 幅広いユースケースに対応 |
| ChatGPT<BR>(preview) | - ほとんどのユースケースでファーストチョイス<BR>- Azure OpenAI Service で最も経済的なモデル<BR>- チャットだけでなく、すべてのワークロードに対応|
| GPT4<BR>(preview) |- 問題解決能力、推論能力の向上<BR>- 繰り返しの洗練(コードエラーの修正、ストーリーを繰り返し考える)<BR>- トークン制限の増加（長いコンテンツに効果的）|

情報元：
https://www.youtube.com/watch?v=tFgqdHKsOME

<img width="798" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/3a47d0fb-5124-4c3d-a4cf-e2194c30db33">

# 3. 何をやっているのか
> 演習で何が出来たのか理解できましたでしょうか？

このワークショップでは、ロジックアプリを用いて Azure OpenAI の GPT/ChatGPT に対して prompt による会話を行いました。
AI を活用するに際して、期待する答えをどのように導き出すか、prompt の依頼方法が重要となります。<BR>
<img width="739" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/dbfb73c3-ac92-44c8-b52a-42ec9bf4a9d9">

# 4. Azure OpenAI の使い方
> Azure OpenAI の prompt を用いた活用例を考える

Azure OpenAI のプレイグラウンドを用いて、幾つかのモデル活用パターンを考えてみましょう。<BR>
https://oai.azure.com/portal/playground
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/28fd2466-be5d-4b14-94f3-c31a8c348dfa)

## 4.1 基礎：要約 (Summarization)
GPT に対してコンテキストを要約依頼する例です。
インストラクションとコンテキストは ```###``` や ```"""``` を使って分離することを覚えましょう。

```
下記のテキストを一文で説明してください。

テキスト: """日本は前半、クロアチアにボールを保持されて押し込まれましたが、ゴールキーパーの権田修一選手がシュートを防ぐなどしてしのぎ、前半43分には、右サイドのコーナーキックから短いパスを受けた堂安律選手がクロスボールを入れて、最後は前田大然選手が左足で押し込み、日本が先制しました。後半は、10分にクロアチアのクロスボールからイバン・ペリシッチ選手にヘディングでシュートを決められ同点とされて、試合は1対1のまま今大会初めての延長戦に入り、試合は最終的にペナルティーキック戦に入りました。
日本は先攻となりましたが、1人目の南野拓実選手と2人目の三笘選手が連続で相手のゴールキーパーにシュートを防がれました。そして日本が1対2で迎えた4人目でキャプテンの吉田麻也選手も決められず、最後はクロアチアの4人目に決められてペナルティーキック戦で1対3で敗れました。"""
```

## 4.2 基礎：質問応答 (Question-Answering)
コンテキストを使って業界独自の文書や企業内 FAQ など、OpenAI GPT 知らないさまざまな文書も対象にすることが出来ます。

```
以下のテキストを使って下記の質問に答えてください。もし答えがない場合には、「私は知らない」と答えてください。

コンテキスト: """Surface Book が空の状態から完全に充電されるまで、2 ～ 4 時間かかります。Surface Book を充電しながらゲームやビデオ ストリーミングのような電力消費の多い活動に Surface を使用している場合、さらに時間がかかる可能性があります。電源アダプターに付いている USB ポートを使って、Surface Book の充電中にスマートフォンなどの他のデバイスを充電することもできます。電源アダプターの USB ポートは充電専用であり、データ転送用ではありません。"""

質問: Surface Book の充電時間を節約するにはどうするか。
```

<img width="700" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/2d8cce9f-7c04-400d-b158-4e37029774d7">

## 4.3 基礎：分類 (Classification)
インテント分類など、カスタムな分類にも対応出来ます。

```
テキストを不満、普通、満足の感情に分類してください。
テキスト: 食事はまあまあでした。
```

<img width="488" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/a81c66de-e7e6-41fa-8a8e-4f3715f849c5">

## 4.4 基礎：テキスト挿入 (Insertion)
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

他にも、prompt の活用例は様々な手法が紹介されています。ご興味がある方は、公式サイト[プロンプト エンジニアリングの手法](https://learn.microsoft.com/ja-jp/azure/cognitive-services/openai/concepts/advanced-prompt-engineering?pivots=programming-language-chat-completions)を参照下さい。

  
# 5. ChatGPT (gpt-3.5-turbo/GPT4) 以降の role パラメータの設定
> ChatGPT3.5/GPT4 を用いる場合は、rule を設定しましょう

Chat GPT (gpt-3.5-turbo/GPT4) 以降から、メッセージオブジェクトに role (役割) を設定し、目的に応じたリクエストを設定することが出来ます。<BR>
- [ChatGPT および GPT-4 モデルの操作方法の説明](https://learn.microsoft.com/ja-jp/azure/cognitive-services/openai/how-to/chatgpt?pivots=programming-language-chat-completions)

期待した応答に近づけるように、``system`` / ``assistant`` / ``user`` の各項目に設定値を渡して、リクエストを送ることが出来ます。 

```json
[
  {
    "role": "system",
    "content": "あなたはセキュリティアナリストです。"
  },
  {
    "role": "user",
    "content": "文章を日本語で100文字以内で解説して下さい。"
  },
  {
    "role": "assistant",
    "content": "This detection looks for the steps required to conduct a UAC bypass using Fodhelper.exe. By default this detection looks for the setting of the required registry keys and the invoking of the process within 1 hour - this can be tweaked as required."
  }
]
```

| パラメータ | 意味 |
| ---- | ---- |
| system | system メッセージでは、ChatGPTに与える役を設定するために使用します。|
| assistant | 以前の応答を保存するのに役立ちます。文章要約や翻訳を行う際の対象となるテキストをここのメッセージに設定します。また、望ましい動作の例や回答の選択肢を示す使い方も可能です。|
| user | ユーザーがChatGPTに提供したいテキストを含めるために使用されます。これにより、ChatGPTはユーザーの要求に応じた回答を提供することができます。|

上記 JSON prompt を ChatGPT 3.5 (gpt-3.5-turbo) にリクエストしたサンプル例です。

```
この検出は、Fodhelper.exeを使用したUACバイパスを実行するために必要な手順を検出します。
  デフォルトでは、必要なレジストリキーの設定と、1時間以内にプロセスを呼び出すことを検出します。必要に応じて調整できます。
```

<p>

# 6. パラメータチューニング
> Azure OpenAI でリクエストするパラメータを理解しましょう
今回の演習では、RESTAPI で Azure OpenAI に問い合わせを行う際に幾つかのパラメータを適用しました。
これらのパラメータにはどのような意味が有るのか考えてみましょう。<BR>
<img width="267" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/44ca05af-221a-4cd2-b5e7-133aa735ce0b">

[Azure OpenAI Service の REST API リファレンス](https://learn.microsoft.com/ja-jp/azure/cognitive-services/openai/reference)

| パラメータ | 意味 |
| ---- | ---- |
| prompt | 文字列、文字列の一覧。<BR>またはトークン リストの一覧としてエンコードされた、入力候補の生成対象となるプロンプト。|
| max_tokens | 入力候補に生成するトークンの最大数。<BR>[日本語の場合はトークン量が増える](https://note.com/yutakikuchi/n/n0b32eb5567de)ため、可能であれば英語で書いた方が安くなる。|
| temperature | **ランダム性の制御[0-1]**<BR>使用するサンプリング温度 (0 から 2)。 値が大きいほど、モデルはより多くのリスクを負います。 よりクリエイティブなアプリケーションの場合は 0.9、明確に定義された回答の場合は 0 (argmax sampling) をお試しください。|
| frequency_penalty | **周波数制御[0-2]**：高いと同じ話題を繰り返さなくなる<BR>-2.0 から 2.0 の数値。 値を正にすると、これまでのテキストに存在する頻度に基づいて新しいトークンにペナルティが課せられ、モデルが同じ行を逐語的に繰り返す可能性が低下します。
| top_n | 多様性の制御[0-1] |
| presence_penalty | **新規トピック制御[0-2]**：高いと新規のトピックが出現しやすくなる |

参考 URL:
- [OpenAI APIで設定するtemperatureは回答のランダム性を指定するもの。実験してみた](https://note.com/eurekachan/n/n68c1b346809c)
- [ChatGPT API利用方法の簡単解説](https://qiita.com/mikito/items/b69f38c54b362c20e9e6)
- [ChatGPT APIの各種パラメーターを指定して動作確認してみた。](https://qiita.com/kuromame1020611/items/0233be428a92d2d4e762)
- [ChatGPTで用いられるGPT-3.5系のモデルをAPIから利用してみた](https://qiita.com/kaz2ngt/items/d26dd572bd82fcd3dfd3)


# 7. Microsoft Sentinel インシデント情報から何が得られるのか？
> Microsoft Sentinel のインシデントから何が得られて、何を OpenAI に問い合わせるのか

セキュリティオペレーションセンターでは、インシデント運用を効率化するためにインシデント情報から AI を活用することを考えています。
Microsoft Sentinel からはどのような情報を Azure OpenAI に渡せるのか考えてみましょう。

| インシデント情報から得られるパラメータ | 意味 |
| ---- | ---- |
| インシデントのタイトル | Analytics Rule に作成する分析ルール名。 |
| インシデントの説明 | Analytics Rule に適用されているルール詳細。 |
| インシデントの重要度 | Analytics Rule に適用されているルール詳細。 |
| エンティティ | Analytics Rule にて検出したエンティティ情報 (JSON 出力) |
| インシデントの戦術 | Analytics Rule にて検出した MITRE 戦術情報 |

<img width="297" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/a12e03c8-123b-405b-90ee-8bb3378e5656">

# 8. Microsoft Sentinel に対して、どのような対処が出来るのかを考える
> Microsoft Sentinel のインシデントを操作する

Microsoft Sentinel のオートメーション機能では、インシデント内容の更新を行うことで内容を上書きすることが出来るようになっています。
本演習ではインシデント情報を以下のように更新することを実践しました。
- タグに正規化された ``model`` 情報を付与
- インシデント説明の内容を正規化された ``text`` 情報を付与
  
<img width="315" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/4fb3f3d7-af41-42c6-abdd-f44517375b8f">

他にどのようなことが出来るのでしょうか？ ロジックアプリの Microsoft Sentinel コネクターを用いると以下のような処理を実現することが出来ます。
- インシデントブックマークの登録
- インシデントに通知を追加する
- [インシデントにタスクを追加する](https://learn.microsoft.com/ja-jp/azure/sentinel/incident-tasks)
- [インシデントにコメントを追加する](https://learn.microsoft.com/ja-jp/azure/sentinel/investigate-incidents#considerations-for-comments)

# 9. ユースケースを考える
> Microsoft Sentinel の Azure OpenAI 活用ストーリーを考えてみましょう

- 各自アイデアを考えてみましょう。
- インシデント情報を元に、ChatGPT に問い合わせを行い、得られた情報をどのようにインシデント管理に活用出来ますか？

# Next Action
お疲れさまでした！[最後の演習](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work4.md)に移って下さい。



