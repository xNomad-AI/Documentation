markdown
# AI-NFT Metaadatok

Az AI-NFT-k létrehozása hasonló a hagyományos NFT-khez, **azzal** a kiegészítéssel, hogy tartalmaz egy `ai_agent` mezőt, amely leírja az AI-ügynök konfigurációját és a használt motort, amelyet a metaadatokban tárolnak.

## Támogatott AI-motor <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Motor</th><th width="231">Motor neve</th><th>Karakterfájl</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> az ElizaOS-től</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentáció</a></li><li><a href="https://github.com/elizaOS/characterfile">Sablon</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Példa</a></li></ul></td></tr></tbody></table>

## AI-NFT Metaadatok JSON <a href="#metadata-json" id="metadata-json"></a>

| Mező                         | Típus  | Leírás                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Új hozzáadott) | object | <p>A konfiguráció, amely meghatározza az AI-ügynököt, amely ehhez az NFT-hez kapcsolódik.</p><ul><li><strong>engine</strong> (string): az AI-ügynök futtatásához használt motor. Alapértelmezett: "eliza".</li><li><strong>character</strong> (object): az AI-ügynököt leíró karakterfájl JSON. Nézd meg <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">itt</a>.</li></ul>                                                                                                                                                         |
| **name**                     | string | Az eszköz neve.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **description**              | string | Az eszköz leírása.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **image**                    | string | Az eszköz logójára mutató URI.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **animation\_url**           | string | Az eszköz animációjára mutató URI.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **external\_url**            | string | Egy külső URL-re mutató URI, amely meghatározza az eszközt – pl. a játék főoldala.                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **attributes**               | array  | <p>Az eszköz jellemzőit meghatározó attribútumok tömbje.</p><ul><li><strong>trait_type</strong> (string): Az attribútum típusa.</li><li><strong>value</strong> (string): Az attribútum értéke.</li></ul>                                                                                                                                                                                                                                                                                                                                                     |
| **properties**               | object | <p>További tulajdonságok, amelyek meghatározzák az eszközt.</p><ul><li><p><strong>files</strong> (array): Az eszközhöz tartozó további fájlok.</p><ul><li><strong>uri</strong> (string): A fájl URI-je.</li><li><strong>type</strong> (string): A fájl típusa, pl. <code>image/png</code>, <code>video/mp4</code>, stb.</li><li><strong>cdn</strong> (boolean, optional): Meg van-e osztva CDN-ről.</li></ul></li><li><strong>category</strong> (string): Az eszköz média kategóriája, pl. <code>video</code>, <code>image</code>, stb.</li></ul> |

## Példa

```json
{
  // AI-ügynök mező
  ai_agent: {
    engine: "eliza",
    character: {
      // ügynök neve
      name:"eliza",
      // háttérinformációk
      bio: [
        "A bio sorok rövid információk, amelyeket véletlenszerű sorrendben lehet kombinálni.",
        "Kimutattuk, hogy az entropia növelésére hasznos véletlenszerűen kiválasztani a bio egy részét az adott kontextushoz.",
        "Ez az 'entropia' szélesíti a lehetséges válaszok eloszlását, változatosabb és releváns válaszokat eredményezve."
      ],
      lore: [
        "A lore sorok szintén rövid információk, amelyek véletlenszerű sorrendben kombinálhatók, hasonlóan a bio sorokhoz.",
        "Azonban ezek általában tényszerűbbek vagy történelmibbek, mint a biográfiai sorok.",
        "A lore sorok chatnaplókból és tweetekből származhatnak, mint a karakterrel kapcsolatos események.",
        "A lore sorokat is randomizálni kell, hogy növeljük az entropiát a kontextusban."
        ],
      ... //xxx.character.json innen: https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // tipikus NFT metaadat szabvány
  name: 'Az én NFT-m',
  description: 'Ez egy NFT a Solanán',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: 'tulajdonság1',
      value: 'érték1',
    },
    {
      trait_type: 'tulajdonság2',
      value: 'érték2',
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

