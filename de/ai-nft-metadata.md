# AI-NFT-Metadaten

Das Erstellen von AI-NFTs funktioniert genau wie bei herkömmlichen NFTs, **mit** einem zusätzlichen Feld „ai_agent“, das die Konfiguration eines AI-Agenten und der von ihm verwendeten Engine beschreibt und in den Metadaten gespeichert ist.

## Unterstützte KI-Engine <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Engine</th><th width="231">Engine-Name</th><th>Charakterdatei</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> von ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokumentation</a></li><li><a href="https://github.com/elizaOS/characterfile">Vorlage</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Beispiel</a></li></ul></td></tr></tbody></table>

## AI-NFT-Metadaten JSON <a href="#metadata-json" id="metadata-json"></a>

| Feld | Typ | Beschreibung |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Neu hinzugefügt) | Objekt | <p>Die Konfiguration, die den mit diesem NFT verbundenen KI-Agenten definiert. </p><ul><li><strong>engine</strong> (Zeichenfolge): die Engine, die zum Ausführen des KI-Agenten verwendet wird. Standardmäßig „eliza“.</li><li><strong>character</strong> (Objekt): die JSON-Charakterdatei, die einen KI-Agenten beschreibt. Prüfen Sie <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">hier</a>.</li></ul> |
| **Name** | Zeichenfolge | Name des Assets. |
| **Beschreibung** | Zeichenfolge | Beschreibung des Assets. |
| **Bild** | Zeichenfolge | URI, die auf das Logo des Assets verweist. |
| **Animation\_URL** | Zeichenfolge | URI, die auf die Animation des Assets verweist. |
| **external\_url** | Zeichenfolge | URI, die auf eine externe URL verweist, die das Asset definiert – z. B. die Hauptseite des Spiels. |
| **Attribute** | Array | <p>Array von Attributen, die die Eigenschaften des Assets definieren.</p><ul><li><strong>trait_type</strong> (Zeichenfolge): Der Typ des Attributs.</li><li><strong>value</strong> (Zeichenfolge): Der Wert für dieses Attribut.</li></ul> |
| **Eigenschaften** | Objekt | <p>Zusätzliche Eigenschaften, die das Asset definieren.</p><ul><li><p><strong>files</strong> (Array): Zusätzliche Dateien, die in das Asset aufgenommen werden sollen.</p><ul><li><strong>uri</strong> (Zeichenfolge): Die URI der Datei.</li><li><strong>type</strong> (Zeichenfolge): Der Typ der Datei. Z. B. <code>image/png</code>, <code>video/mp4</code> usw.</li><li><strong>cdn</strong> (Boolesch, optional): Ob die Datei von einem CDN bereitgestellt wird.</li></ul></li><li><strong>category</strong> (Zeichenfolge): Eine Medienkategorie für das Asset. Z. B. <code>video</code>, <code>image</code> usw.</li></ul> |

## Beispiel

```json
{
  // KI-Agentenfeld
  ai_agent: {
    engine: "eliza",
    character: {
      // Agentenname
      name:"eliza",
      // Hintergrundaussagen
      bio: [
        "Biozeilen sind jeweils kurze Textausschnitte, die in beliebiger Reihenfolge aneinandergereiht werden können.",
        "Wir haben festgestellt, dass die Entropie zunimmt, wenn für jeden Kontext nur ein Teil der Biografie zufällig ausgewählt wird.",
        "Diese „Entropie“ dient dazu, die Streuung möglicher Ergebnisse zu erweitern, was zu vielfältigeren, aber durchgängig relevanten Antworten führen sollte."
      ],
      lore: [
        "Überlieferungslinien sind jeweils kurze Ausschnitte, die in beliebiger Reihenfolge zusammengesetzt werden können, genau wie Bio",
        "Allerdings sind diese in der Regel eher sachlich oder historisch und weniger biographisch als biographische Linien",
        "Überlieferungslinien können aus Chatprotokollen und Tweets als Dinge extrahiert werden, die der Charakter oder die ihm passiert sind",
        "Überlieferungen sollten auch randomisiert und abgetastet werden, um die Entropie im Kontext zu erhöhen"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // typischer NFT-Metadatenstandard
  name: 'Mein NFT',
  description: 'Dies ist ein NFT auf Solana',
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
