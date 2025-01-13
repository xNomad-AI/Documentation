# Metadata AI-NFT

AI-NFT digawe kanthi proses sing padha karo nggawe NFT umum, nanging **`ai_agent` lapangan** ditambahake. Lapangan iki nuduhake pangaturan lan mesin sing digunakake dening AI agen, lan informasi iki disimpen ing metadata.

## Mesin AI sing Didhukung <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Mesin</th><th width="231">Jeneng Mesin</th><th>File Karakter</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> (ElizaOS)</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Pandhuan Panganggo</a></li><li><a href="https://github.com/elizaOS/characterfile">Template</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Conto</a></li></ul></td></tr></tbody></table>

## JSON Metadata AI-NFT <a href="#metadata-json" id="metadata-json"></a>

| Lapangan                       | Tipe    | Katran                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (anyar ditambah) | object  | <p>Pengaturan AI agen sing disambungake menyang NFT iki</p><ul><li><strong>engine</strong> (string): Mesin sing digunakake kanggo mbukak AI agen. Nilai standar yaiku "eliza"</li><li><strong>character</strong> (object): File karakter ing format JSON sing njlèntrèhaké AI agen. Kanggo rincian luwih lengkap, waca <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">kene</a>.</li></ul>                                                                                                                                                        |
| **name**                      | string  | Jeneng aset                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **description**               | string  | Katrangan babagan aset                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **image**                     | string  | URI sing nuduhake logo saka aset                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **animation\_url**            | string  | URI sing nuduhake animasi saka aset                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **external\_url**             | string  | URI sing nuduhake situs web eksternal sing njlèntrèhaké aset — contone situs web resmi game                                                                                                                                                                                                                                                                                                                                                                                                |
| **attributes**                | array   | <p>Array atribut sing nemtokake karakteristik saka aset</p><ul><li><strong>trait_type</strong> (string): Jenis atribut</li><li><strong>value</strong> (string): Nilai atribut</li></ul>                                                                                                                                                                                                                                                            |
| **properties**                | object  | <p>Atribut tambahan kanggo nemtokake karakteristik saka aset</p><ul><li><p><strong>files</strong> (array): File tambahan sing kalebu karo aset</p><ul><li><strong>uri</strong> (string): URI file</li><li><strong>type</strong> (string): Tipe file, contone: <code>image/png</code>, <code>video/mp4</code></li><li><strong>cdn</strong> (boolean, opsional): Nggoleki apa file kasebut kasedhiya liwat CDN</li></ul></li><li><strong>category</strong> (string): Kategori media aset, contone: <code>video</code>, <code>image</code></li></ul> |

## Tuladhane

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
