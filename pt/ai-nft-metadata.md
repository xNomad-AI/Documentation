# AI-NFT Metadata (metadados)

Criar AI-NFTs é semelhante aos NFTs tradicionais, **com** um campo extra `ai_agent` que descreve a configuração de um agente de IA e o motor que ele usa, armazenado nos metadados.

## Supported AI Engine <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Engine</th><th width="231">Engine Name</th><th>Character File (arquivo de personagem)</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Documentação</a></li><li><a href="https://github.com/elizaOS/characterfile">Template</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Exemplo</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Field (Campo)                        | Type (Tipo)   | Description (Descrição)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Newly added)  | object | <p>A configuração que define o agente de IA conectado com o NFT. </p><ul><li><strong>engine</strong> (string): a engine useda para rodar o agente de IA. Default (padrão) é "eliza.</li><li><strong>character</strong> (object): o characterfile (arquivo de personagem) JSON que descreve um agente de IA. Veja <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">aqui</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | Nome do ativo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | Descrição do ativo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI apontando para a imagem de logo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **animation\_url**           | string | URI apontando para a imagem de animação.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | URI para uma URL externa definindo o ativo — e.g. the game's main site.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Array (Lista) de atributos denindo as características do ativo.</p><ul><li><strong>trait_type</strong> (string): O tipo de atributo.</li><li><strong>value</strong> (string): O "valor" para o atributo.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>Propriedades adicionais que definem um ativo.</p><ul><li><p><strong>files</strong> (array): Arquivos adicionais para incluir no ativo.</p><ul><li><strong>uri</strong> (string): O arquivo URI.</li><li><strong>type</strong> (string): O tipo de arquivo. E.g. <code>image/png</code>, <code>video/mp4</code>, etc.</li><li><strong>cdn</strong> (boolean, optional): Quando o arquivo é armazenado em uma CDN.</li></ul></li><li><strong>category</strong> (string): O tipo de mídia do ativo. E.g. <code>video</code>, <code>image</code>, etc.</li></ul> |

## Exemplo

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
