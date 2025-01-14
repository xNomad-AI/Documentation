# Metadata AI-NFT

Membuat AI-NFT mirip dengan NFT tradisional, **dengan** tambahan field `ai_agent` yang menggambarkan konfigurasi agen AI dan mesin yang digunakannya, yang disimpan dalam metadata.

## Mesin AI yang Didukung <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Mesin</th><th width="231">Nama Mesin</th><th>File Karakter</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> oleh ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentasi</a></li><li><a href="https://github.com/elizaOS/characterfile">Template</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Contoh</a></li></ul></td></tr></tbody></table>

## JSON Metadata AI-NFT <a href="#metadata-json" id="metadata-json"></a>

| Field                        | Tipe   | Deskripsi                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Ditambahkan Baru)  | objek | <p>Konfigurasi yang mendefinisikan agen AI yang terhubung dengan NFT ini.</p><ul><li><strong>engine</strong> (string): mesin yang digunakan untuk menjalankan agen AI. Default adalah "eliza".</li><li><strong>character</strong> (objek): file karakter JSON yang menggambarkan agen AI. Lihat <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">di sini</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | Nama dari aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | Deskripsi dari aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI yang menunjuk ke logo aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI yang menunjuk ke animasi aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | URI yang menunjuk ke URL eksternal yang mendefinisikan aset — misalnya situs utama game.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Array atribut yang mendefinisikan karakteristik dari aset.</p><ul><li><strong>trait_type</strong> (string): Jenis atribut.</li><li><strong>value</strong> (string): Nilai untuk atribut tersebut.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | objek | <p>Properti tambahan yang mendefinisikan aset.</p><ul><li><p><strong>files</strong> (array): File tambahan untuk disertakan dengan aset.</p><ul><li><strong>uri</strong> (string): URI file.</li><li><strong>type</strong> (string): Jenis file. Misalnya <code>image/png</code>, <code>video/mp4</code>, dll.</li><li><strong>cdn</strong> (boolean, opsional): Apakah file disajikan dari CDN.</li></ul></li><li><strong>category</strong> (string): Kategori media untuk aset. Misalnya <code>video</code>, <code>image</code>, dll.</li></ul> |

## Contoh

```json
{
  // field agen AI
  ai_agent: {
    engine: "eliza",
    character: {
      // nama agen
      name:"eliza",
      // pernyataan latar belakang
      bio: [
        "Bio adalah setiap potongan pendek yang dapat digabungkan secara acak.",
        "Kami menemukan bahwa hal ini meningkatkan entropi dengan merandom dan memilih hanya sebagian dari bio untuk setiap konteks.",
        "Entropi ini berfungsi untuk memperluas distribusi hasil yang mungkin, yang seharusnya memberi jawaban yang lebih bervariasi namun tetap relevan."
      ],
      lore: [
        "Lore adalah setiap potongan pendek yang dapat digabungkan secara acak, seperti bio",
        "Namun ini biasanya lebih faktual atau historis dan kurang biografis dibandingkan dengan bio",
        "Lore dapat diekstraksi dari chatlog dan tweet tentang hal-hal yang dialami oleh karakter atau yang terjadi pada mereka",
        "Lore juga harus dirandomisasi dan diambil sampelnya untuk meningkatkan entropi dalam konteks"
      ],
      ... //xxx.character.json dari https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // metadata standar NFT
  name: 'NFT Saya',
  description: 'Ini adalah NFT di Solana',
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
