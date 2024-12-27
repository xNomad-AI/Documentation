# AI-NFT Metadata

Creating AI-NFTs is just like traditional NFTs, **with** an extra field `ai_agent` that describes the configuration of an AI agent and the engine it uses, stored in the metadata.

## Supported AI Engine <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="203">Engine</th><th width="204">Engine Name</th><th>Config File</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li>Docs: <a href="https://elizaos.github.io/eliza/docs/core/characterfile/">https://elizaos.github.io/eliza/docs/core/characterfile/</a></li><li>Template: <a href="https://github.com/elizaOS/characterfile">https://github.com/elizaOS/characterfile</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Field                        | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Newly added)  | object | <p>The configuration that define the AI agent behind this NFT. </p><ul><li><strong>engine</strong> (string): the engine used to run the AI agent. Default as "eliza".</li><li><strong>config</strong> (object): the config JSON that describes the configuration of an AI agent.</li></ul>                                                                                                                                                                                                                                                                        |
| **name**                     | string | Name of the asset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | Description of the asset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI pointing to the asset's logo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI pointing to the asset's animation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | URI pointing to an external URL defining the asset — e.g. the game's main site.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Array of attributes defining the characteristics of the asset.</p><ul><li><strong>trait_type</strong> (string): The type of attribute.</li><li><strong>value</strong> (string): The value for that attribute.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>Additional properties that define the asset.</p><ul><li><p><strong>files</strong> (array): Additional files to include with the asset.</p><ul><li><strong>uri</strong> (string): The file's URI.</li><li><strong>type</strong> (string): The file's type. E.g. <code>image/png</code>, <code>video/mp4</code>, etc.</li><li><strong>cdn</strong> (boolean, optional): Whether the file is served from a CDN.</li></ul></li><li><strong>category</strong> (string): A media category for the asset. E.g. <code>video</code>, <code>image</code>, etc.</li></ul> |

## Example

```json
{
  // AI agent field
  ai_agent: {
    engine: "elizaos",
    config: {
      // agent name
      name:"eliza",
      // background statements
      bio: [
        "Bio lines are each short snippets which can be composed together in a random order.",
        "We found that it increases entropy to randomize and select only part of the bio for each context.",
        "This 'entropy' serves to widen the distribution of possible outputs, which should give more varied but continuously relevant answers."
      ],
      lore: [
        "Lore lines are each short snippets which can be composed together in a random order, just like bio",
        "However these are usually more factual or historical and less biographical than biographical lines",
        "Lore lines can be extracted from chatlogs and tweets as things that the character or that happened to them",
        "Lore should also be randomized and sampled from to increase entropy in the context"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // typical NFT metadata standard
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
