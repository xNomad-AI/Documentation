# AI-NFT Metadata

Att skapa AI-NFTs är precis som traditionella NFTs, **med** ett extra fält `ai_agent` som beskriver konfigurationen av en AI-agent och motorn den använder, lagrat i metadatan.

## Stödda AI-motorer <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Motor</th><th width="231">Motornamn</th><th>Karaktärsfil</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> av ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentation</a></li><li><a href="https://github.com/elizaOS/characterfile">Mall</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Exempel</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Fält                         | Typ    | Beskrivning                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ---------------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Nyligen tillagd) | objekt | <p>Konfigurationen som definierar AI-agenten kopplad till denna NFT. </p><ul><li><strong>engine</strong> (sträng): motorn som används för att köra AI-agenten. Standard är "eliza".</li><li><strong>character</strong> (objekt): karaktärsfilens JSON som beskriver en AI-agent. Kolla <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">här</a>.</li></ul>                                                                                                                                                                                    |
| **name**                     | sträng | Tillgångens namn.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **description**              | sträng | Beskrivning av tillgången.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **image**                    | sträng | URI som pekar på tillgångens logotyp.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **animation\_url**           | sträng | URI som pekar på tillgångens animation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **external\_url**            | sträng | URI som pekar på en extern URL som definierar tillgången — t.ex. spelets huvudsida.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **attributes**               | array  | <p>Array av attribut som definierar tillgångens egenskaper.</p><ul><li><strong>trait_type</strong> (sträng): Typen av attribut.</li><li><strong>value</strong> (sträng): Värdet för det attributet.</li></ul>                                                                                                                                                                                                                                                                                                                                                  |
| **properties**               | objekt | <p>Ytterligare egenskaper som definierar tillgången.</p><ul><li><p><strong>files</strong> (array): Ytterligare filer att inkludera med tillgången.</p><ul><li><strong>uri</strong> (sträng): Filens URI.</li><li><strong>type</strong> (sträng): Filens typ. T.ex. <code>image/png</code>, <code>video/mp4</code>, etc.</li><li><strong>cdn</strong> (boolean, valfritt): Om filen serveras från en CDN.</li></ul></li><li><strong>category</strong> (sträng): En mediekategori för tillgången. T.ex. <code>video</code>, <code>image</code>, etc.</li></ul> |

## Exempel

```json
{
  // AI agent-fält
  ai_agent: {
    engine: "eliza",
    character: {
      // agentnamn
      name:"eliza",
      // bakgrundsuttalanden
      bio: [
        "Bio-rader är korta utdrag som kan komponeras ihop i slumpmässig ordning.",
        "Vi fann att det ökar entropi att randomisera och välja endast delar av bion för varje kontext.",
        "Denna 'entropi' tjänar till att bredda distributionen av möjliga outputs, vilket bör ge mer varierade men kontinuerligt relevanta svar."
      ],
      lore: [
        "Lore-rader är korta utdrag som kan komponeras ihop i slumpmässig ordning, precis som bio",
        "Dock är dessa vanligtvis mer faktabaserade eller historiska och mindre biografiska än biografiska rader",
        "Lore-rader kan extraheras från chattloggar och tweets som saker som karaktären eller som hände dem",
        "Lore bör också randomiseras och samplas från för att öka entropi i kontexten"
        ],
      ... //xxx.character.json från https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // typisk NFT metadata-standard
  name: 'Min NFT',
  description: 'Detta är en NFT på Solana',
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