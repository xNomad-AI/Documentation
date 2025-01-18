# Metadata AI-NFT

Mae creu AI-NFTs yr un fath â NFTs traddodiadol, **gyda** maes ychwanegol `ai_agent` sy'n disgrifio'r ffurfweddiad o asiant AI a'r peiriant y mae'n ei ddefnyddio, wedi'i storio yn y metadata.

## Peiriannau AI Cefnogol <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Peiriant</th><th width="231">Enw'r Peiriant</th><th>Ffeil Cymeriad</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> gan ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dogfennaeth</a></li><li><a href="https://github.com/elizaOS/characterfile">Templed</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Enghraifft</a></li></ul></td></tr></tbody></table>

## Metadata JSON AI-NFT <a href="#metadata-json" id="metadata-json"></a>

| Maes                          | Math   | Disgrifiad                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Newydd ei ychwanegu) | gwrthrych | <p>Y ffurfweddiad sy'n diffinio'r asiant AI sy'n gysylltiedig â'r NFT hwn. </p><ul><li><strong>peiriant</strong> (llinyn): y peiriant a ddefnyddir i redeg yr asiant AI. Diofyn fel "eliza".</li><li><strong>cymeriad</strong> (gwrthrych): y JSON ffeil cymeriad sy'n disgrifio asiant AI. Gwiriwch <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">yma</a>.</li></ul>                                                                                                                                                                                     |
| **enw**                      | llinyn | Enw'r ased.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **disgrifiad**               | llinyn | Disgrifiad o'r ased.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **delwedd**                   | llinyn | URI sy'n pwyntio at logo'r ased.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | llinyn | URI sy'n pwyntio at animeiddiad yr ased.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | llinyn | URI sy'n pwyntio at URL allanol sy'n diffinio'r ased — e.e. prif safle'r gêm.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **priodoleddau**               | array  | <p>Array o briodoleddau sy'n diffinio nodweddion yr ased.</p><ul><li><strong>trait_type</strong> (llinyn): Math y briodoledd.</li><li><strong>gwerth</strong> (llinyn): Y gwerth ar gyfer y briodoledd honno.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **priodweddau**               | gwrthrych | <p>Priodweddau ychwanegol sy'n diffinio'r ased.</p><ul><li><p><strong>ffeiliau</strong> (array): Ffeiliau ychwanegol i'w cynnwys gyda'r ased.</p><ul><li><strong>uri</strong> (llinyn): URI'r ffeil.</li><li><strong>math</strong> (llinyn): Math y ffeil. E.e. <code>image/png</code>, <code>video/mp4</code>, ac ati.</li><li><strong>cdn</strong> (boole, dewisol): A yw'r ffeil yn cael ei gweini o CDN.</li></ul></li><li><strong>categori</strong> (llinyn): Categori cyfryngau ar gyfer yr ased. E.e. <code>video</code>, <code>image</code>, ac ati.</li></ul> |

## Enghraifft

```json
{
  // Maes asiant AI
  ai_agent: {
    engine: "eliza",
    character: {
      // enw'r asiant
      name:"eliza",
      // datganiadau cefndir
      bio: [
        "Mae llinellau bio yn fyr ac yn cael eu cyfansoddi gyda'i gilydd mewn trefn ar hap.",
        "Gwelsom ei fod yn cynyddu entropy i hap-drefnu ac i ddewis rhan o'r bio ar gyfer pob cyd-destun.",
        "Mae'r 'entropy' hwn yn lledaenu'r dosbarthiad o ganlyniadau posibl, gan roi atebion mwy amrywiol ond yn barhaus berthnasol."
      ],
      lore: [
        "Mae llinellau lore hefyd yn fyr ac yn cael eu cyfansoddi gyda'i gilydd mewn trefn ar hap, yn union fel bio",
        "Fodd bynnag, mae'r rhain fel arfer yn fwy ffeithiol neu hanesyddol nag yn fywgraffyddol",
        "Gellir echdynnu llinellau lore o sgwrslogiau a trydariadau fel pethau a ddywedodd y cymeriad neu a ddigwyddodd iddynt",
        "Dylai llinellau lore hefyd gael eu hap-drefnu a'u samplo i gynyddu entropy yn y cyd-destun"
        ],
      ... //xxx.character.json o https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // safon metadata NFT arferol
  name: 'Fy NFT',
  description: 'Dyma NFT ar Solana',
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