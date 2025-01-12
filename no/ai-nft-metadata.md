# AI-NFT-metadata

Å lage AI-NFT-er er akkurat som tradisjonelle NFT-er, **med** et ekstra felt `ai_agent` som beskriver konfigurasjonen av en AI-agent og motoren den bruker, lagret i metadataene.

## Støttet AI-motor <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Motor</th><th width="231">Motornavn</th><th>Tegnfil</th></tr>< /thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> av ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentasjon</ a></li><li><a href="https://github.com/elizaOS/characterfile">Mal</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Eksempel</a></li></ul></td></tr></tbody></table >

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Felt | Skriv | Beskrivelse |
| ---------------------------- | ------ | -------------------------------------------------- -------------------------------------------------- -------------------------------------------------- -------------------------------------------------- -------------------------------------------------- -------------------------------------------------- -------------------------------------------------- -------------------------------------------------- -------------------------------------------------- -------------------------------------------------- ---------------------------------------------------- |
| **ai\_agent** (Nylig lagt til) | objekt | <p>Konfigurasjonen som definerer AI-agenten som er koblet til denne NFT. </p><ul><li><strong>motor</strong> (streng): motoren som brukes til å kjøre AI-agenten. Standard som "eliza".</li><li><strong>karakter</strong> (objekt): karakterfilen JSON som beskriver en AI-agent. Sjekk <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">her</a>.</li></ul> |
| **navn** | streng | Navnet på eiendelen. |
| **beskrivelse** | streng | Beskrivelse av eiendelen. |
| **bilde** | streng | URI som peker til innholdselementets logo. |
| **animasjon\_url** | streng | URI som peker til innholdselementets animasjon. |
| **ekstern\_url** | streng | URI som peker til en ekstern URL som definerer ressursen – f.eks. spillets hovedside. |
| **attributter** | rekke | <p>Array av attributter som definerer egenskapene til eiendelen.</p><ul><li><strong>trekktype</strong> (streng): attributttypen.</li><li><strong> verdi</strong> (streng): Verdien for det attributtet.</li></ul> |
| **eiendommer** | objekt | <p>Ytterligere egenskaper som definerer ressursen.</p><ul><li><p><strong>filer</strong> (matrise): Ytterligere filer som skal inkluderes med ressursen.</p><ul> <li><strong>uri</strong> (streng): Filens URI.</li><li><strong>type</strong> (streng): Filens type. f.eks. <code>image/png</code>, <code>video/mp4</code> osv.</li><li><strong>cdn</strong> (boolsk, valgfritt): Om filen blir servert fra et CDN.</li></ul></li><li><strong>kategori</strong> (streng): En mediekategori for ressursen. f.eks. <code>video</code>, <code>bilde</code> osv.</li></ul> |

## Eksempel

```json
{
  // AI-agentfelt
  ai_agent: {
    engine: "eliza",
    character: {
      // agentnavn
      name:"eliza",
      // bakgrunnsuttalelser
      bio: [
        "Bio-linjer er hver korte tekstutdrag som kan komponeres sammen i en tilfeldig rekkefølge.",
        "Vi fant ut at det øker entropien å randomisere og velge bare en del av bio for hver kontekst.",
        "Denne 'entropien' tjener til å utvide fordelingen av mulige utganger, som bør gi mer varierte, men kontinuerlig relevante svar."
      ],
      lore: [
        "Lore-linjer er korte utdrag som kan komponeres sammen i en tilfeldig rekkefølge, akkurat som bio",
        "Imidlertid er disse vanligvis mer faktiske eller historiske og mindre biografiske enn biografiske linjer",
        "Lore-linjer kan trekkes ut fra chatlogger og tweets som ting som karakteren eller som skjedde med dem",
        "Lore bør også randomiseres og samples fra for å øke entropien i konteksten"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // typisk NFT-metadatastandard
  name: 'Min NFT',
  description: 'Dette er en NFT på Solana',
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
