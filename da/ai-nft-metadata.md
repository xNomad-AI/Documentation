# AI-NFT-metadata

Oprettelse af AI-NFT'er er ligesom traditionelle NFT'er, **med** et ekstra felt 'ai_agent', der beskriver konfigurationen af ​​en AI-agent og den motor, den bruger, gemt i metadataene.

## Understøttet AI Engine <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Motor</th><th width="231">Motornavn</th><th>Tegnfil</th></tr>< /thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> af ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentation</ a></li><li><a href="https://github.com/elizaOS/characterfile">Skabelon</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Eksempel</a></li></ul></td></tr></tbody></table >

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Felt                | Skriv  | Beskrivelse |
|---------------------|--------|-------------|
| **ai\_agent**       | objekt | Konfigurationen, der definerer AI-agenten forbundet med denne NFT. <ul><li><strong>motor</strong> (streng): motoren, der bruges til at køre AI-agenten. Standard som "eliza".</li><li><strong>karakter</strong> (objekt): karakterfilen JSON, der beskriver en AI-agent. Tjek <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">her</a>.</li></ul> |
| **navn**            | streng | Aktivets navn. |
| **beskrivelse**     | streng | Beskrivelse af aktivet. |
| **billede**         | streng | URI, der peger på aktivets logo. |
| **animation\_url**  | streng | URI, der peger på aktivets animation. |
| **ekstern\_url**    | streng | URI, der peger på en ekstern URL, der definerer aktivet - f.eks. spillets hovedside. |
| **attributter**     | række  | Array af attributter, der definerer aktivets karakteristika. <ul><li><strong>trait_type</strong> (streng): Typen af ​​attribut.</li><li><strong>værdi</strong> (streng): Værdien for den attribut.</li></ul> |
| **ejendomme**       | objekt | Yderligere egenskaber, der definerer aktivet. <ul><li><strong>filer</strong> (array): Yderligere filer, der skal inkluderes med aktivet. <ul><li><strong>uri</strong> (streng): Filens URI.</li><li><strong>type</strong> (streng): Filens type. F.eks. <code>image/png</code>, <code>video/mp4</code> osv.</li><li><strong>cdn</strong> (boolesk, valgfrit): Om filen vises fra et CDN.</li></ul></li><li><strong>kategori</strong> (streng): En mediekategori for aktivet. F.eks. <code>video</code>, <code>image</code> osv.</li></ul> |

## Eksempel

```json
{
  // AI-agentfelt
  ai_agent: {
    engine: "eliza",
    character: {
      // agent navn
      name:"eliza",
      // baggrundserklæringer
      bio: [
        "Bio-linjer er hver korte uddrag, som kan komponeres sammen i en tilfældig rækkefølge.",
        "Vi fandt ud af, at det øger entropien at randomisere og kun vælge en del af bio til hver kontekst.",
        "Denne 'entropi' tjener til at udvide fordelingen af ​​mulige output, hvilket burde give mere varierede, men løbende relevante svar."
      ],
      lore: [
        "Lore-linjer er hver korte uddrag, som kan komponeres sammen i en tilfældig rækkefølge, ligesom bio",
        "Disse er dog normalt mere faktuelle eller historiske og mindre biografiske end biografiske linjer",
        "Lore linjer kan uddrages fra chatlogs og tweets som ting, som karakteren eller det skete med dem",
        "Lore bør også randomiseres og samples fra for at øge entropi i konteksten"
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
