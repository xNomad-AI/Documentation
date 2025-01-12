markdown
# AI-NFT Metadata

AI-NFT:iden luominen on kuin perinteisten NFT:iden luominen, **mutta** siihen lisätään ylimääräinen kenttä `ai_agent`, joka kuvaa tekoälyagentin konfiguraation ja käyttämän moottorin, tallennettuna metadataan.

## Tuetut tekoälymoottorit <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Moottori</th><th width="231">Moottorin nimi</th><th>Hahmotiedosto</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a>, kehittänyt ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentaatio</a></li><li><a href="https://github.com/elizaOS/characterfile">Malli</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Esimerkki</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Kenttä                       | Tyyppi | Kuvaus                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Uusi kenttä)  | object | <p>Konfiguraatio, joka määrittää NFT:hen liittyvän tekoälyagentin.</p><ul><li><strong>engine</strong> (string): moottori, jota käytetään tekoälyagentin suorittamiseen. Oletuksena "eliza".</li><li><strong>character</strong> (object): JSON-tiedosto, joka kuvaa tekoälyagentin. Katso <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">tästä</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | Ominaisuuden nimi.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | Ominaisuuden kuvaus.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI, joka osoittaa omaisuuden logoon.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI, joka osoittaa omaisuuden animaatioon.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | URI, joka osoittaa ulkoiseen URL-osoitteeseen, joka määrittelee omaisuuden – esim. pelin pääsivusto.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Attribuuttien taulukko, joka määrittää omaisuuden ominaisuudet.</p><ul><li><strong>trait_type</strong> (string): Attribuutin tyyppi.</li><li><strong>value</strong> (string): Attribuutin arvo.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>Lisäominaisuudet, jotka määrittävät omaisuuden.</p><ul><li><p><strong>files</strong> (array): Lisätiedostot, jotka liitetään omaisuuteen.</p><ul><li><strong>uri</strong> (string): Tiedoston URI.</li><li><strong>type</strong> (string): Tiedoston tyyppi, esim. <code>image/png</code>, <code>video/mp4</code> jne.</li><li><strong>cdn</strong> (boolean, valinnainen): Onko tiedosto toimitettu CDN:ltä.</li></ul></li><li><strong>category</strong> (string): Median kategoria omaisuudelle, esim. <code>video</code>, <code>image</code> jne.</li></ul> |

## Esimerkki

```json
{
  // Tekoälyagentin kenttä
  ai_agent: {
    engine: "eliza",
    character: {
      // agentin nimi
      name:"eliza",
      // taustakuvaukset
      bio: [
        "Bio-linjat ovat lyhyitä katkelmia, joita voidaan yhdistää satunnaisessa järjestyksessä.",
        "Huomasimme, että se lisää entropiaa satunnaistamalla ja valitsemalla vain osan bio:sta kuhunkin kontekstiin.",
        "Tämä 'entropia' laajentaa mahdollisten tulosten jakautumista, mikä antaa monipuolisempia mutta jatkuvasti merkityksellisiä vastauksia."
      ],
      lore: [
        "Lore-linjat ovat lyhyitä katkelmia, joita voidaan yhdistää satunnaisessa järjestyksessä, kuten bio.",
        "Ne ovat kuitenkin yleensä faktapohjaisempia tai historiallisia kuin biografiset linjat.",
        "Lore voidaan kerätä keskustelulokeista ja twiiteistä, jotka liittyvät hahmoon tai tapahtumiin.",
        "Lore-linjojen pitäisi myös olla satunnaistettuja ja näytteenotettuja entropian lisäämiseksi kontekstissa."
        ],
      ... //xxx.character.json osoitteesta https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // Tyypillinen NFT-metadata-standardi
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
```
