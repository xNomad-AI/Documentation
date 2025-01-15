# AI-NFT Metadata

Création de AI-NFTs ye ka NFT traditional, **ka** fɔlɔ `ai_agent` ka fɔlɔ AI agent la ka engine ye, a ye metadata la.

## AI Engine ka fɔlɔ <a href="#metadata-json" id="metadata-json"></a>

| Engine                                               | Engine Name | Character File                                                                                                                                                                                        |
| ---------------------------------------------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Eliza](https://github.com/elizaOS/eliza) ka ElizaOS | eliza       | - [Documentation](https://elizaos.github.io/eliza/docs/core/characterfile/) - [Template](https://github.com/elizaOS/characterfile) - [Example](https://github.com/elizaOS/eliza/tree/main/characters) |

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Field                      | Type   | Description                                                                                                                                                                                                                                                      |
| -------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai_agent** (Newly added) | object | Configuration ka fɔlɔ AI agent la ka NFT la. - **engine** (string): engine ka fɔlɔ AI agent la. Default ka "eliza". - **character** (object): characterfile JSON ka fɔlɔ AI agent la. [Check here](https://github.com/elizaOS/characterfile?tab=readme-ov-file). |
| **name**                   | string | Asset la tɔɔrɔ.                                                                                                                                                                                                                                                  |
| **description**            | string | Asset la fɔlɔ.                                                                                                                                                                                                                                                   |
| **image**                  | string | URI ka asset la logo.                                                                                                                                                                                                                                            |
| **animation_url**          | string | URI ka asset la animation.                                                                                                                                                                                                                                       |
| **external_url**           | string | URI ka external URL ka asset la.                                                                                                                                                                                                                                 |
| **attributes**             | array  | Array ka attributes ka asset la. - **trait_type** (string): Attribute type. - **value** (string): Attribute value.                                                                                                                                               |
| **properties**             | object | Additional properties ka asset la. - **files** (array): Additional files ka asset la. - **category** (string): Media category ka asset la.                                                                                                                       |

## Example

```json
{
  // AI agent field
  ai_agent: {
    engine: "eliza",
    character: {
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
