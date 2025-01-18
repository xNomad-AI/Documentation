# AI-NFT Metadata

Kreiranje AI-NFT-ova je slično tradicionalnim NFT-ovima, **s** dodatnim poljem `ai_agent` koje opisuje konfiguraciju AI agenta i motor koji koristi, pohranjen u metapodacima.

## Podržani AI motor <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Motor</th><th width="231">Ime motora</th><th>Datoteka lika</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentacija</a></li><li><a href="https://github.com/elizaOS/characterfile">Predložak</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Primjer</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Polje                       | Tip    | Opis                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Novo dodano) | objekt | <p>Konfiguracija koja definira AI agenta povezanog s ovim NFT-om. </p><ul><li><strong>engine</strong> (string): motor korišten za pokretanje AI agenta. Zadano kao "eliza".</li><li><strong>character</strong> (objekt): JSON datoteka lika koja opisuje AI agenta. Provjerite <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">ovdje</a>.</li></ul>                                                                                                                                                                                     |
| **name**                    | string | Ime imovine.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**             | string | Opis imovine.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                   | string | URI koji pokazuje na logotip imovine.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**          | string | URI koji pokazuje na animaciju imovine.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**           | string | URI koji pokazuje na vanjski URL koji definira imovinu — npr. glavna stranica igre.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**              | niz    | <p>Niz atributa koji definiraju karakteristike imovine.</p><ul><li><strong>trait_type</strong> (string): Vrsta atributa.</li><li><strong>value</strong> (string): Vrijednost za taj atribut.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**              | objekt | <p>Dodatna svojstva koja definiraju imovinu.</p><ul><li><p><strong>files</strong> (niz): Dodatne datoteke za uključivanje s imovinom.</p><ul><li><strong>uri</strong> (string): URI datoteke.</li><li><strong>type</strong> (string): Tip datoteke. Npr. <code>image/png</code>, <code>video/mp4</code>, itd.</li><li><strong>cdn</strong> (boolean, opcionalno): Je li datoteka poslužena s CDN-a.</li></ul></li><li><strong>category</strong> (string): Medijska kategorija za imovinu. Npr. <code>video</code>, <code>image</code>, itd.</li></ul> |

## Primjer

```json
{
  // Polje za AI agenta
  ai_agent: {
    engine: "eliza",
    character: {
      // ime agenta
      name:"eliza",
      // pozadinske izjave
      bio: [
        "Bio linije su kratki isječci koji se mogu nasumično kombinirati.",
        "Otkrili smo da povećava entropiju kada nasumično odaberemo samo dio bio linija za svaki kontekst.",
        "Ova 'entropija' služi za proširenje distribucije mogućih izlaza, što bi trebalo dati raznovrsnije ali stalno relevantne odgovore."
      ],
      lore: [
        "Lore linije su kratki isječci koji se također mogu nasumično kombinirati, slično bio linijama",
        "Međutim, obično su više činjenične ili povijesne prirode, a manje biografske",
        "Lore linije mogu se izvući iz chatlogova i tweetova kao događaji koji su povezani s likom",
        "Lore bi također trebalo nasumično odabrati kako bi se povećala entropija u kontekstu"
        ],
      ... //xxx.character.json iz https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // Standardni NFT metapodaci
  name: 'Moj NFT',
  description: 'Ovo je NFT na Solani',
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