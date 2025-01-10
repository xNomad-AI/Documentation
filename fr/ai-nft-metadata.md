# Métadonnées AI-NFT

La création d'AI-NFT est identique à celle des NFT traditionnels, **avec** un champ supplémentaire `ai_agent` qui décrit la configuration d'un agent IA et le moteur qu'il utilise, stocké dans les métadonnées.

## Moteur d'IA pris en charge <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Moteur</th><th width="231">Nom du moteur</th><th>Fichier de caractères</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> par ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Documentation</a></li><li><a href="https://github.com/elizaOS/characterfile">Modèle</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Exemple</a></li></ul></td></tr></tbody></table>

## Métadonnées JSON AI-NFT <a href="#metadata-json" id="metadata-json"></a>

| Champ | Type | Description |
| ---------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Nouvellement ajouté) | objet | <p>La configuration qui définit l'agent IA connecté à ce NFT. </p><ul><li><strong>engine</strong> (chaîne) : le moteur utilisé pour exécuter l'agent IA. Par défaut, « eliza ».</li><li><strong>character</strong> (objet) : le fichier de caractères JSON qui décrit un agent IA. Vérifiez <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">ici</a>.</li></ul> |
| **name** | string | Nom de l'actif. |
| **description** | string | Description de l'actif. |
| **image** | string | URI pointant vers le logo de l'actif. |
| **animation\_url** | string | URI pointant vers l'animation de l'actif. |
| **external\_url** | string | URI pointant vers une URL externe définissant l'actif, par exemple le site principal du jeu. |
| **attributes** | array | <p>Tableau d'attributs définissant les caractéristiques de l'actif.</p><ul><li><strong>trait_type</strong> (string) : le type d'attribut.</li><li><strong>value</strong> (string) : la valeur de cet attribut.</li></ul> |
| **properties** | object | <p>Propriétés supplémentaires qui définissent l'actif.</p><ul><li><p><strong>files</strong> (array) : fichiers supplémentaires à inclure avec l'actif.</p><ul><li><strong>uri</strong> (string) : l'URI du fichier.</li><li><strong>type</strong> (string) : le type du fichier. Par exemple <code>image/png</code>, <code>vidéo/mp4</code>, etc.</li><li><strong>cdn</strong> (booléen, facultatif) : si le fichier est diffusé à partir d'un CDN.</li></ul></li><li><strong>catégorie</strong> (chaîne) : une catégorie de média pour l'élément. Par exemple, <code>vidéo</code>, <code>image</code>, etc.</li></ul> |

## Exemple

```json
{
  // Domaine d'agent IA
  ai_agent: {
    engine: "eliza",
    character: {
      // nom de l'agent
      name:"eliza",
      // Déclarations de fond
      bio: [
        "Les lignes biologiques sont chacune de courts extraits qui peuvent être composés ensemble dans un ordre aléatoire.",
        "Nous avons constaté qu’il augmente l’entropie de randomiser et de sélectionner uniquement une partie de la biographie pour chaque contexte.",
        "Cette « entropie » sert à élargir la distribution des résultats possibles, qui devraient donner des réponses plus variées mais toujours pertinentes."
      ],
      lore: [
        "Les lignes de légende sont chacune de courts extraits qui peuvent être composés ensemble dans un ordre aléatoire, tout comme la biographie.",
        "Cependant, ceux-ci sont généralement plus factuels ou historiques et moins biographiques que les lignes biographiques.",
        "Les histoires peuvent être extraites des journaux de discussion et des tweets sous forme de choses que le personnage ou ce qui lui est arrivé",
        "Les traditions doivent également être randomisées et échantillonnées pour augmenter l'entropie dans le contexte"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // norme de métadonnées NFT typique
  name: 'Mon NFT',
  description: 'Ceci est un NFT sur Solana',
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
