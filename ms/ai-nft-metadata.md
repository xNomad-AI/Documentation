# Metadata AI-NFT

Penciptaan AI-NFTs adalah serupa dengan penciptaan NFTs tradisional, dengan satu medan tambahan yang dipanggil ai_agent, yang menggambarkan konfigurasi agen IA dan mekanisme yang digunakan, disimpan dalam metadata.

## Mekanisme IA yang Disokong <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Mecanismo</th><th width="231">Nama Mekanisme</th><th>Fail Watak</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> oleh ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentasi</a></li><li><a href="https://github.com/elizaOS/characterfile">Modelo</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Contoh</a></li></ul></td></tr></tbody></table>

## Mekanisme IA yang Disokong <a href="#metadata-json" id="metadata-json"></a>

| Field             | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ----------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai_agent**      | object | <p>Konfigurasi yang menentukan agen IA yang disambungkan ke NFT ini. </p><ul><li><strong>engine</strong> (string): Mekanisme yang digunakan untuk menjalankan agen IA. Secara lalai "eliza".</li><li><strong>character</strong> (object): Fail JSON watak yang menggambarkan agen IA.<a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file"></a>Lihat di sini</li></ul>                                                                                                                                                                      |
| **name**          | string | Nama aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **description**   | string | Penerangan tentang aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **image**         | string | URI yang menunjuk ke logo aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **animation_url** | string | URI yang menunjuk ke animasi aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **external_url**  | string | URL luaran yang menentukan aset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **attributes**    | array  | <p>Senarai atribut yang menentukan ciri-ciri aset.</p><ul><li><strong>trait_type</strong> (string): Jenis atribut.</li><li><strong>value</strong> (string): Nilai bagi atribut ini.</li></ul>                                                                                                                                                                                                                                                                                                                                                               |
| **properties**    | object | <p>Hartanah tambahan yang menentukan aset.</p><ul><li><p><strong>files</strong> (array): Fail tambahan untuk disertakan bersama aset.</p><ul><li><strong>uri</strong> (string): URI fail.</li><li><strong>type</strong> (string): Jenis fail. Contoh: <code>image/png</code>, <code>video/mp4</code>, dsb.</li><li><strong>cdn</strong> (boolean, pilihan): Menunjukkan sama ada fail dihantar melalui CDN.</li></ul></li><li><strong>category</strong> (string): Kategori media untuk aset. Contoh: <code>video</code>, <code>image</code>, dsb.</li></ul> |

## Example

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
