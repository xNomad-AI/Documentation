
# Metadata ของ AI-NFT 

การสร้าง AI-NFT นั้นคล้ายกับการสร้าง NFT แบบดั้งเดิม **โดยมี**ฟิลด์เพิ่มเติม `ai_agent` ที่อธิบายการตั้งค่าของ AI Agent และ engine ที่ใช้งาน ซึ่งถูกจัดเก็บไว้ใน metadata

## AI Engine ที่รองรับ <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Engine</th><th width="231">ชื่อ Engine</th><th>ไฟล์ตัวละคร</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> โดย ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">เอกสารประกอบการใช้งาน</a></li><li><a href="https://github.com/elizaOS/characterfile">เทมเพลต</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">ตัวอย่าง</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| ฟิลด์                        | ประเภท   | คำอธิบาย                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Newly added)  | object | <p>การตั้งค่าที่กำหนด AI Agent ที่เชื่อมโยงกับ NFT นี้</p><ul><li><strong>engine</strong> (string): เอนจินที่ใช้ในการรัน AI Agent ค่าเริ่มต้นคือ "eliza"</li><li><strong>character</strong> (object): ไฟล์ JSON ของตัวละครที่อธิบาย AI Agent ดูรายละเอียดเพิ่มเติมได้<a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">ที่นี่</a></li></ul>                                                                                                                                                                                     |
| **name**                     | string | ชื่อของสินทรัพย์                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **description**              | string | คำอธิบายของสินทรัพย์                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI ที่ระบุไปยังโลโก้ของสินทรัพย์                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI ที่ระบุไปยังแอนิเมชันของสินทรัพย์                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **external\_url**            | string | URI ที่ระบุไปยัง URL ภายนอกที่อธิบายสินทรัพย์ — เช่น เว็บไซต์หลักของเกม                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Array ของ Attributes ที่กำหนดลักษณะเฉพาะของสินทรัพย์</p><ul><li><strong>trait_type</strong> (string): ประเภทของ attributes</li><li><strong>value</strong> (string): ค่าที่กำหนดให้กับ attribute นั้น</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>คุณสมบัติเพิ่มเติมที่กำหนดลักษณะของสินทรัพย์</p><ul><li><p><strong>files</strong> (array): ไฟล์เพิ่มเติมที่ต้องการรวมเข้ากับสินทรัพย์</p><ul><li><strong>uri</strong> (string): URI ของไฟล์</li><li><strong>type</strong> (string): ประเภทของไฟล์ เช่น <code>image/png</code>, <code>video/mp4</code> เป็นต้น</li><li><strong>cdn</strong> (boolean, optional): ระบุว่าไฟล์ถูกให้บริการจาก CDN หรือไม่</li></ul></li><li><strong>category</strong> (string): หมวดหมู่มีเดียของสินทรัพย์ เช่น <code>video</code>, <code>image</code> เป็นต้น</li></ul> |

## ตัวอย่าง

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
