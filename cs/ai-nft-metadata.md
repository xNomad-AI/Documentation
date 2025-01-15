# Metadata AI-NFT

Vytváření AI-NFT je stejné jako u tradičních NFT, **s** dalším polem `ai_agent`, které popisuje konfiguraci agenta AI a engine, který používá, uložené v metadatech.

## Podporovaný AI engine <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Engine</th><th width="231">Název motoru</th><th>Soubor znaků</th></tr>< /thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> od ElizaOS</td><td>eliza</td>< td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentace</a></li><li><a href="https://github.com/elizaOS/ characterfile">Šablona</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Příklad</a></li></ul></td></tr></tbody></table >

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Pole | Typ | Popis |
| ----------------------------- | ------ | -------------------------------------------------- ------------------- -------------------------------------------------- ------------------- -------------------------------------------------- ------------------- -------------------------------------------------- ------------------- -------------------------------------------------- ------------------- -------------------------------------------------- ------------------- -------------------------------------------------- ------------------- -------------------------------------------------- -------------------- |
| **ai\_agent** (Nově přidáno) | objekt | <p>Konfigurace, která definuje agenta AI připojeného k tomuto NFT. </p><ul><li><strong>engine</strong> (řetězec): engine používaný ke spuštění agenta AI. Výchozí hodnota je „eliza“.</li><li><strong>character</strong> (object): znakový soubor JSON, který popisuje agenta AI. Podívejte se <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">sem</a>.</li></ul> |
| **jméno** | řetězec | Název aktiva. |
| **popis** | řetězec | Popis aktiva. |
| **obrázek** | řetězec | URI ukazující na logo díla. |
| **animace\_url** | řetězec | URI ukazující na animaci díla. |
| **externí\_url** | řetězec | URI odkazující na externí adresu URL definující aktivum – např. hlavní stránka hry. |
| **atributy** | pole | <p>Pole atributů definujících vlastnosti díla.</p><ul><li><strong>trait_type</strong> (řetězec): Typ atributu.</li><li><strong> value</strong> (řetězec): Hodnota pro tento atribut.</li></ul> |
| **vlastnosti** | objekt | <p>Další vlastnosti, které definují dílo.</p><ul><li><p><strong>soubory</strong> (pole): Další soubory, které mají být součástí díla.</p><ul> <li><strong>uri</strong> (řetězec): URI souboru.</li><li><strong>type</strong> (řetězec): Typ souboru. Např. <code>image/png</code>, <code>video/mp4</code> atd.</li><li><strong>cdn</strong> (logická hodnota, volitelné): Zda se soubor zobrazí z CDN.</li></ul></li><li><strong>category</strong> (řetězec): Kategorie média pro dílo. Např. <code>video</code>, <code>obrázek</code> atd.</li></ul> |

## Příklad

```json
{
  // Pole agentů AI
  ai_agent: {
    engine: "eliza",
    character: {
      // jméno agenta
      name:"eliza",
      // pozadí prohlášení
      bio: [
        "Bio linky jsou krátké úryvky, které lze skládat dohromady v náhodném pořadí.",
        "Zjistili jsme, že zvyšuje entropii náhodným výběrem a výběrem pouze části životopisu pro každý kontext.",
        "Tato „entropie“ slouží k rozšíření distribuce možných výstupů, které by měly poskytovat rozmanitější, ale stále relevantní odpovědi."
      ],
      lore: [
        "Lore řádky jsou krátké úryvky, které lze skládat dohromady v náhodném pořadí, stejně jako bio",
        "Ty jsou však obvykle více faktické nebo historické a méně biografické než biografické linie",
        "Lore řádky mohou být extrahovány z chatlogů a tweetů jako věci, které se postavě nebo co se jim stalo",
        "Lore by také měl být randomizován a vzorkován, aby se zvýšila entropie v kontextu"
        ],
      ... //xxx.character.json z https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // typický standard metadat NFT
  name: 'Můj NFT',
  description: 'Toto je NFT na Solana',
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
