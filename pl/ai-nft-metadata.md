# Metadane AI-NFT

Tworzenie AI-NFT jest takie samo jak tworzenie tradycyjnych NFT, **z** dodatkowym polem `ai_agent`, które opisuje konfigurację agenta AI i używany przez niego silnik, zapisanym w metadanych.

## Obsługiwany silnik AI <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Silnik</th><th width="231">Nazwa silnika</th><th>Plik znaków</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentacja</a></li><li><a href="https://github.com/elizaOS/characterfile">Szablon</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Przykład</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Pole | Typ | Opis |
| ---------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Nowo dodane) | obiekt | <p>Konfiguracja definiująca agenta AI połączonego z tym NFT. </p><ul><li><strong>engine</strong> (string): silnik używany do uruchomienia agenta AI. Domyślnie „eliza”.</li><li><strong>character</strong> (obiekt): plik JSON pliku znaków, który opisuje agenta AI. Sprawdź <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">tutaj</a>.</li></ul> |
| **name** | string | Nazwa zasobu. |
| **description** | string | Opis zasobu. |
| **image** | string | URI wskazujący na logo zasobu. |
| **animation\_url** | string | URI wskazujący na animację zasobu. |
| **external\_url** | string | URI wskazujący na zewnętrzny adres URL definiujący zasób — np. główną witrynę gry. |
| **attributes** | array | <p>Tablica atrybutów definiujących cechy zasobu.</p><ul><li><strong>trait_type</strong> (string): Typ atrybutu.</li><li><strong>value</strong> (string): Wartość tego atrybutu.</li></ul> |
| **properties** | object | <p>Dodatkowe właściwości definiujące zasób.</p><ul><li><p><strong>files</strong> (array): Dodatkowe pliki do uwzględnienia w zasobie.</p><ul><li><strong>uri</strong> (string): URI pliku.</li><li><strong>type</strong> (string): Typ pliku. Np. <code>image/png</code>, <code>video/mp4</code> itd.</li><li><strong>cdn</strong> (wartość logiczna, opcjonalnie): Czy plik jest obsługiwany z CDN.</li></ul></li><li><strong>category</strong> (string): Kategoria multimediów dla zasobu. Np. <code>video</code>, <code>image</code> itd.</li></ul> |

## Przykład

```json
{
  // Pole agenta AI
  ai_agent: {
    engine: "eliza",
    character: {
      // nazwa agenta
      name:"eliza",
      // oświadczenia dotyczące tła
      bio: [
        "Linie biograficzne składają się z krótkich fragmentów, które można komponować w losowej kolejności.",
        "Odkryliśmy, że losowe wybieranie tylko części biografii w każdym kontekście zwiększa entropię.",
        "Ta „entropia” służy poszerzeniu rozkładu możliwych wyników, co powinno dać bardziej zróżnicowane, ale stale trafne odpowiedzi."
      ],
      lore: [
        "Linie wiedzy to krótkie fragmenty, które można układać w losowej kolejności, tak jak biografie.",
        "Są one jednak zazwyczaj bardziej faktograficzne lub historyczne i mniej biograficzne niż wątki biograficzne",
        "Linie wiedzy można wyodrębnić z czatów i tweetów jako rzeczy dotyczące postaci lub tego, co się jej przydarzyło",
        "Wiedzę należy również losowo dobierać i pobierać próbki, aby zwiększyć entropię w kontekście"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // typowy standard metadanych NFT
  name: 'Mój NFT',
  description: 'To jest NFT na Solanie',
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
