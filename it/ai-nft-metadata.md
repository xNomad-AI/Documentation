# Metadati AI-NFT

La creazione di AI-NFT è come quella degli NFT tradizionali, **con** un campo extra `ai_agent` che descrive la configurazione di un agente AI e il motore che utilizza, archiviato nei metadati.

## Motore AI supportato <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Motore</th><th width="231">Nome motore</th><th>File personaggio</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> di ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Documentazione</a></li><li><a href="https://github.com/elizaOS/characterfile">Modello</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Esempio</a></li></ul></td></tr></tbody></table>

## Metadati AI-NFT JSON <a href="#metadata-json" id="metadata-json"></a>

| Campo | Tipo | Descrizione |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (aggiunto di recente) | oggetto | <p>La configurazione che definisce l'agente AI connesso a questo NFT. </p><ul><li><strong>motore</strong> (stringa): il motore utilizzato per eseguire l'agente AI. Predefinito come "eliza".</li><li><strong>carattere</strong> (oggetto): il file di caratteri JSON che descrive un agente AI. Controlla <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">qui</a>.</li></ul> |
| **name** | string | Nome della risorsa. |
| **description** | string | Descrizione della risorsa. |
| **image** | string | URI che punta al logo della risorsa. |
| **animation\_url** | string | URI che punta all'animazione della risorsa. |
| **external\_url** | string | URI che punta a un URL esterno che definisce la risorsa, ad esempio il sito principale del gioco. |
| **attributes** | array | <p>Array di attributi che definiscono le caratteristiche della risorsa.</p><ul><li><strong>trait_type</strong> (stringa): il tipo di attributo.</li><li><strong>value</strong> (stringa): il valore per quell'attributo.</li></ul> |
| **properties** | object | <p>Proprietà aggiuntive che definiscono la risorsa.</p><ul><li><p><strong>files</strong> (array): file aggiuntivi da includere con la risorsa.</p><ul><li><strong>uri</strong> (stringa): l'URI del file.</li><li><strong>type</strong> (stringa): il tipo di file. Ad esempio <code>image/png</code>, <code>video/mp4</code>, ecc.</li><li><strong>cdn</strong> (booleano, facoltativo): se il file è servito da una CDN.</li></ul></li><li><strong>category</strong> (stringa): una categoria multimediale per la risorsa. Ad esempio <code>video</code>, <code>image</code>, ecc.</li></ul> |

## Esempio


```json
{
  // Campo agente AI
  ai_agent: {
    engine: "eliza",
    character: {
      // nome dell'agente
      name:"eliza",
      // dichiarazioni di base
      bio: [
        "Le linee biografiche sono brevi frammenti che possono essere composti insieme in ordine casuale.",
        "Abbiamo scoperto che randomizzare e selezionare solo una parte della biografia per ogni contesto aumenta l'entropia.",
        "Questa "entropia" serve ad ampliare la distribuzione dei possibili output, il che dovrebbe fornire risposte più variegate ma sempre pertinenti."
      ],
      lore: [
        "Le linee di tradizione sono brevi frammenti che possono essere composti insieme in un ordine casuale, proprio come la biografia",
        "Tuttavia, di solito si tratta di informazioni più fattuali o storiche e meno biografiche rispetto alle linee biografiche",
        "Le linee di tradizione possono essere estratte dai registri delle chat e dai tweet come cose che il personaggio o che gli sono accadute",
        "La tradizione dovrebbe anche essere randomizzata e campionata per aumentare l'entropia nel contesto"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // tipico standard di metadati NFT
  name: 'Il mio NFT',
  description: 'Questo è un NFT su Solana',
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
