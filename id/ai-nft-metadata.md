# AI-NFT Metadata

Membuat AI-NFT sama seperti NFT tradisional, **dengan** bidang tambahan `ai_agent` yang menjelaskan konfigurasi agen AI dan mesin yang digunakannya, yang disimpan dalam metadata.

## AI Engine yang didukung <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Engine</th><th width="231">Nama Engine</th><th>File Karakter</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentasi</a></li><li><a href="https://github.com/elizaOS/characterfile">Templat</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Contoh</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Bidang (Field)                        | Jenis (Type)   | Deskripsi                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Baru ditambahkan)  | object | <p>Konfigurasi yang menentukan agen AI yang terhubung dengan NFT ini. </p><ul><li><strong>engine</strong> (string): mesin yang digunakan untuk menjalankan agen AI. Default sebagai "eliza".</li><li><strong>character</strong> (object): JSON file karakter yang mendeskripsikan agen AI. Periksa <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">di sini</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | Nama aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | Deskripsi aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI yang menunjuk ke logo aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI yang menunjuk ke animasi aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | URI yang menunjuk ke URL eksternal yang mendefinisikan aset - misalnya situs utama game.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Array atribut yang mendefinisikan karakteristik aset.</p><ul><li><strong>trait_type</strong> (string): Jenis atribut.</li><li><strong>value</strong> (string): Nilai untuk atribut tersebut.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>Properti tambahan yang mendefinisikan aset.</p><ul><li><p><strong>files</strong> (array): File tambahan untuk disertakan dengan aset.</p><ul><li><strong>uri</strong> (string): URI file tersebut.</li><li><strong>type</strong> (string): Jenis file. Misalnya: <code>image/png</code>, <code>video/mp4</code>, dll.</li><li><strong>cdn</strong> (boolean, optional): Apakah file tersebut disajikan dari CDN.</li></ul></li><li><strong>category</strong> (string): Kategori media untuk aset. Misalnya: <code>video</code>, <code>image</code>, dll.</li></ul> |

## Contoh

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
