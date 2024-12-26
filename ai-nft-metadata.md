# AI-NFT Metadata

Creating AI-NFTs is just like traditional NFTs, **with only some differences in the metadata.** AI-NFT follows the typical metadata standard, with an extended field `ai_agent` that describes the engine and configuration of an AI agent.

## Supported AI engine <a href="#metadata-json" id="metadata-json"></a>

* [**ElizaOS**](https://github.com/elizaOS):  character [examples](https://github.com/elizaOS/eliza/tree/main/characters).

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Field                        | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Newly added)  | object | <p>The configuration that define the AI agent behind this NFT. </p><ul><li><strong>engine</strong> (string): the engine used to run the AI agent. Default as "elizaos".</li><li><strong>config</strong> (json): config json of an AI agent corresponding to the engine. Check the <a href="https://github.com/elizaOS/eliza/tree/main/characters">examples</a> if set <code>engine</code> as "elizaos".</li></ul>                                                                                                                                                 |
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
