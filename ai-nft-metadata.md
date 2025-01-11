# AI-NFT کی میٹاڈیٹا

AI-NFT کی تخلیق عام NFT تخلیقی عمل سے ملتی جلتی ہے، لیکن **`ai_agent` فیلڈ** شامل ہوتی ہے۔ یہ فیلڈ AI ایجنٹ کی ترتیب اور استعمال شدہ انجن کی نشاندہی کرتی ہے، اور یہ معلومات میٹاڈیٹا میں محفوظ کی جاتی ہے۔

## معاون AI انجن <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">انجن</th><th width="231">انجن کا نام</th><th>کریکٹر فائل</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> (ElizaOS)</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">استعمال کی گائیڈ</a></li><li><a href="https://github.com/elizaOS/characterfile">ٹیمپلیٹ</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">مثال</a></li></ul></td></tr></tbody></table>

## AI-NFT میٹاڈیٹا JSON <a href="#metadata-json" id="metadata-json"></a>

| فیلڈ                          | قسم    | وضاحت                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (نیا شامل کیا گیا)  | object | <p>اس NFT سے منسلک AI ایجنٹ کی ترتیبات</p><ul><li><strong>engine</strong> (string): AI ایجنٹ کو چلانے کے لیے استعمال ہونے والا انجن۔ ڈیفالٹ ویلیو "eliza" ہے۔</li><li><strong>character</strong> (object): JSON فارمیٹ میں AI ایجنٹ کو بیان کرنے والی کریکٹر فائل۔ مزید تفصیلات کے لیے <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">یہاں</a> دیکھیں۔</li></ul>                                                                                                                                                                                     |
| **name**                     | string | اثاثہ کا نام                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **description**              | string | اثاثہ کی وضاحت                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | اثاثہ کے لوگو کی نشاندہی کرنے والا URI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | اثاثہ کی اینیمیشن کی نشاندہی کرنے والا URI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **external\_url**            | string | اثاثہ کو بیان کرنے والے بیرونی URL کی نشاندہی کرنے والا URI — مثال کے طور پر گیم کی آفیشل ویب سائٹ                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>اثاثہ کی خصوصیات کی وضاحت کرنے والی صف</p><ul><li><strong>trait_type</strong> (string): خصوصیت کی قسم</li><li><strong>value</strong> (string): خصوصیت کی قدر</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>اثاثہ کی خصوصیات کی وضاحت کرنے والی اضافی صفات</p><ul><li><p><strong>files</strong> (array): اثاثہ کے ساتھ شامل اضافی فائلیں</p><ul><li><strong>uri</strong> (string): فائل کا URI</li><li><strong>type</strong> (string): فائل کی قسم، مثال: <code>image/png</code>, <code>video/mp4</code></li><li><strong>cdn</strong> (boolean, optional): فائل کے CDN سے فراہم ہونے کی حالت</li></ul></li><li><strong>category</strong> (string): اثاثہ کے میڈیا کیٹیگری، مثال: <code>video</code>, <code>image</code></li></ul> |

## مثال

```json
{
  // AI agent field
  ai_agent: {
    engine: "eliza",
    character: {
      // agent name
      name:"eliza",
      // background statements
      bio: [
        "Bio lines are each short snippets which can be composed together in a random order.",
        "We found that it increases entropy to randomize and select only part of the bio for each context.",
        "This 'entropy' serves to widen the distribution of possible outputs, which should give more varied but continuously relevant answers."
      ],
      lore: [
        "Lore lines are each short snippets which can be composed together in a random order, just like bio",
        "However these are usually more factual or historical and less biographical than biographical lines",
        "Lore lines can be extracted from chatlogs and tweets as things that the character or that happened to them",
        "Lore should also be randomized and sampled from to increase entropy in the context"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // typical NFT metadata standard
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