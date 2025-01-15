# AI-NFT Metadata

Die skep van AI-NFT's is net soos tradisionele NFTs, **met** 'n ekstra veld `ai_agent` wat die konfigurasie van 'n AI-agent en die enjin wat dit gebruik, wat in die metadata gestoor word, beskryf.

## Ondersteunde AI Enjin <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Enjin</th><th width="231">Enjin Naam</th><th>Karakterlêer</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> deur ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentasie</a></li><li><a href="https://github.com/elizaOS/characterfile">Template</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Voorbeeld</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Veld                          | Tipe   | Beskrywing                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ----------------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Nuut bygevoeg)  | objek  | <p>Die konfigurasie wat die AI-agent wat met hierdie NFT gekoppel is, definieer.</p><ul><li><strong>engine</strong> (string): die enjin wat gebruik word om die AI-agent te bestuur. Standaard as "eliza".</li><li><strong>character</strong> (objek): die characterfile JSON wat 'n AI-agent beskryf. Kyk <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">hier</a>.</li></ul>                                                                                                                                                     |
| **name**                       | string | Naam van die bate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **description**                | string | Beskrywing van die bate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **image**                      | string | URI wat na die bate se logo wys.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **animation\_url**             | string | URI wat na die bate se animasie wys.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **external\_url**              | string | URI wat na 'n eksterne URL wys wat die bate definieer — bv. die speletjie se hoofblad.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **attributes**                 | array  | <p>Array van eienskappe wat die kenmerke van die bate definieer.</p><ul><li><strong>trait_type</strong> (string): Die tipe eienskap.</li><li><strong>value</strong> (string): Die waarde vir daardie eienskap.</li></ul>                                                                                                                                                                                                                                                                                                     |
| **properties**                 | objek  | <p>Aanvullende eienskappe wat die bate definieer.</p><ul><li><p><strong>files</strong> (array): Aanvullende lêers om saam met die bate in te sluit.</p><ul><li><strong>uri</strong> (string): Die lêer se URI.</li><li><strong>type</strong> (string): Die lêer se tipe. Byvoorbeeld <code>image/png</code>, <code>video/mp4</code>, ens.</li><li><strong>cdn</strong> (booleans, opsioneel): Of die lêer vanaf 'n CDN bedien word.</li></ul></li><li><strong>category</strong> (string): 'n Media kategorie vir die bate. Byvoorbeeld <code>video</code>, <code>image</code>, ens.</li></ul> |

## Voorbeeld

```json
{
  // AI agent veld
  ai_agent: {
    engine: "eliza",
    character: {
      // agent naam
      name:"eliza",
      // agtergrond stellings
      bio: [
        "Bio lynne is kort snippetse wat in 'n ewekansige volgorde saamgestel kan word.",
        "Ons het gevind dat dit entropie verhoog om bio net 'n deel van die tyd te randomiseer en te kies.",
        "Hierdie 'entropie' dien om die verspreiding van moontlike uitsette te verbreed, wat meer afwisselende maar steeds relevante antwoorde moet gee."
      ],
      lore: [
        "Lore lynne is kort snippetse wat saamgestel kan word, net soos bio.",
        "Maar hierdie is gewoonlik meer feitlik of histories en minder biografies.",
        "Lore lynne kan uit chatlogs en tweets onttrek word as dinge wat die karakter of dit wat met hulle gebeur het, beskryf.",
        "Lore moet ook randomiseer en uitgelaat word om entropie in die konteks te verhoog."
        ],
      ... //xxx.character.json van https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // tipiese NFT metadata standaard
  name: 'My NFT',
  description: 'Dit is 'n NFT op Solana',
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
