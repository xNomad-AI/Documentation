# AI-NFT Metadata

Ang paggawa ng AI-NFTs ay katulad ng tradisyonal na NFTs, **ngunit** may karagdagang field na `ai_agent` na naglalarawan ng configuration ng isang AI agent at ang engine na ginagamit nito, na naka-imbak sa metadata.

## Sinusuportahang AI Engine <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Engine</th><th width="231">Pangalan ng Engine</th><th>Character File</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> ng ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentasyon</a></li><li><a href="https://github.com/elizaOS/characterfile">Template</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Halimbawa</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Field                        | Type   | Paglalarawan                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Bagong idinagdag)  | object | <p>Ang configuration na nagtatakda ng AI agent na nakakonekta sa NFT na ito. </p><ul><li><strong>engine</strong> (string): ang engine na ginagamit upang patakbuhin ang AI agent. Default ay "eliza".</li><li><strong>character</strong> (object): ang characterfile JSON na naglalarawan ng isang AI agent. Tingnan <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">dito</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | Pangalan ng asset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | Paglalarawan ng asset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI na tumutukoy sa logo ng asset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI na tumutukoy sa animation ng asset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | URI na tumutukoy sa isang panlabas na URL na naglalarawan ng asset—halimbawa, ang pangunahing website ng laro.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Array ng mga attribute na naglalarawan ng mga katangian ng asset.</p><ul><li><strong>trait_type</strong> (string): Ang uri ng attribute.</li><li><strong>value</strong> (string): Ang halaga para sa attribute na iyon.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>Karagdagang mga properties na naglalarawan ng asset.</p><ul><li><p><strong>files</strong> (array): Karagdagang mga file na isasama sa asset.</p><ul><li><strong>uri</strong> (string): URI ng file.</li><li><strong>type</strong> (string): Uri ng file. Halimbawa: <code>image/png</code>, <code>video/mp4</code>, atbp.</li><li><strong>cdn</strong> (boolean, optional): Kung ang file ay ipinapamahagi mula sa isang CDN.</li></ul></li><li><strong>category</strong> (string): Isang kategorya ng media para sa asset. Halimbawa: <code>video</code>, <code>image</code>, atbp.</li></ul> |

## Halimbawa

```json
{
  // AI agent field
  ai_agent: {
    engine: "eliza",
    character: {
      // pangalan ng agent
      name:"eliza",
      // mga background na pahayag
      bio: [
        "Ang mga bio lines ay mga maiikling pahayag na maaaring pagsamahin nang random.",
        "Napag-alaman namin na nakakatulong ang randomization para magkaroon ng entropy at mapili lamang ang bahagi ng bio para sa bawat konteksto.",
        "Ang 'entropy' na ito ay tumutulong upang mapalawak ang distribusyon ng mga posibleng output, na dapat magbigay ng mas iba-ibang pero patuloy na may kinalaman na mga sagot."
      ],
      lore: [
        "Ang mga lore lines ay mga maiikling pahayag na maaaring pagsamahin nang random, katulad ng bio",
        "Ngunit karaniwan, ang mga ito ay mas factual o historikal kaysa sa biographical na mga linya",
        "Ang mga lore lines ay maaaring kunin mula sa mga chatlogs at tweets bilang mga bagay na nangyari sa karakter o sa kanila",
        "Ang lore ay dapat ding randomize at sample-in upang magdagdag ng entropy sa konteksto"
        ],
      ... //xxx.character.json mula sa https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // karaniwang NFT metadata standard
  name: 'Aking NFT',
  description: 'Ito ay isang NFT sa Solana',
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
