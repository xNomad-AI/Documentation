# AI-NFTメタデータ

AI-NFTを生成する方法は既存のNFTと似ていますが、メタデータにおいてAIエージェントの設定と使用するエンジンを説明する`ai_agent`フィールドが追加されます。

## サポートされているAIエンジン <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">エンジン</th><th width="231">エンジン名</th><th>キャラクターファイル</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">ドキュメント</a></li><li><a href="https://github.com/elizaOS/characterfile">テンプレート</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">例</a></li></ul></td></tr></tbody></table>

## AI-NFTメタデータ <a href="#metadata-json" id="metadata-json"></a>

| フィールド               | タイプ | 説明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------ | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (新規追加) | object | <p>このNFTに接続されたAIエージェントを定義する設定です。</p><ul><li><strong>engine</strong> (string): AIエージェントを実行するために使用されるエンジン。デフォルトは"eliza"です。</li><li><strong>character</strong> (object): エージェントを説明するcharacterfile JSONです。こちらの<a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">ドキュメント</a>を参照してください。</li></ul>                                                                                                                                |
| **name**                 | string | アセットの名前。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **description**          | string | アセットの説明。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                | string | アセットのロゴを指すURI。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **animation\_url**       | string | アセットのアニメーションを指すURI。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **external\_url**        | string | アセットを定義する外部URL — 例：ゲームのメインサイト。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**           | array  | <p>アセットの特性を定義する属性（attributes）配列。</p><ul><li><strong>trait_type</strong> (string): 属性タイプ。</li><li><strong>value</strong> (string): その属性の値。</li></ul>                                                                                                                                                                                                                                                                                                                                                      |
| **properties**           | object | <p>アセットを定義する追加情報。</p><ul><li><p><strong>files</strong> (array): アセットと共に含まれる追加ファイルのリスト。</p><ul><li><strong>uri</strong> (string): ファイルのURI。</li><li><strong>type</strong> (string): ファイルの種類 (例：<code>image/png</code>, <code>video/mp4</code> など)。</li><li><strong>cdn</strong> (boolean, optional): ファイルがCDNから提供されているかどうか。</li></ul></li><li><strong>category</strong> (string): メディアカテゴリ (例：<code>video</code>, <code>image</code> など)。</li></ul> |

## 例

```json
{
  // AI agent フィールド
  ai_agent: {
    engine: "eliza",
    character: {
      // エージェント名
      name:"eliza",
      // 背景情報（bio）文
      bio: [
        "Bioの各行は、ランダムな順序で組み合わせることができる短いスニペットです。",
        "各コンテキストでバイオの一部だけをランダムに選択することでエントロピーが増加することがわかりました。",
        "この'エントロピー'は可能な出力の分布を広げ、より多様でありながら一貫して関連性のある回答を提供するはずです。"
      ],
      lore: [
        "Loreの各行も、bioと同様にランダムな順序で組み合わせることができる短いスニペットです",
        "ただし、これらは通常、伝記的な行よりも事実的または歴史的な内容が多くなります",
        "Loreの行は、キャラクターに起こったことやチャットログやツイートから抽出できます",
        "Loreもコンテキストのエントロピーを増やすためにランダム化とサンプリングを行うべきです"
      ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // 一般的なNFTメタデータ標準
  name: 'My NFT',
  description: 'This is an NFT on Solana',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: 'trait1',
      value: 'value1',
    },
    {
      trait_type: 'trait2',
      value: 'value2',
    },
  ],
  properties: {
    files: [
      {
        uri: imageUri[0],
        type: 'image/jpeg',
      },
    ],
    category: 'image',
  },
}
```
