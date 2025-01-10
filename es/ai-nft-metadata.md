# AI-NFT Metadata

Crear AI-NFTs es como crear cualquier NFT tradicional, **con** un campo extra `ai_agent` el cual describe la configuración del agente IA y del motor que usa y que almacena en el metadata.

## Motores IA soportados <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Motor IA</th><th width="231">Nombre del motor</th><th>Fichero del agente</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Documentation</a></li><li><a href="https://github.com/elizaOS/characterfile">Template</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Example</a></li></ul></td></tr></tbody></table>

## AI-NFT Metadata JSON <a href="#metadata-json" id="metadata-json"></a>

| Campo                        | Tipo   | Descripcion                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Añadido recientemente)  | object | <p>La configuración que define al agente IA conectado con este NFT. </p><ul><li><strong>engine</strong> (string): El motor IA usado para ejecutar el agente IA. Por defecto es "eliza".</li><li><strong>character</strong> (object): El fichero JSON que describe a un AI agent. Compruébalo <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">aquí</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | Nombre del activo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | Descripción del activo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI que apunta al logo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI que apunta a la animación del activo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | URI que apunta a la URL externa que define al activo — e.g. El sitio web del juego.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Array de atributos que definen las características del activo.</p><ul><li><strong>trait_type</strong> (string): El tipo de atributo.</li><li><strong>value</strong> (string): El valor para el atributo.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>Propiedades adicionales que definen al activo.</p><ul><li><p><strong>files</strong> (array): Ficheros adicionales que se añaden al activo.</p><ul><li><strong>uri</strong> (string): La dirección URI del fichero.</li><li><strong>type</strong> (string): El tipo de fichero. E.g. <code>image/png</code>, <code>video/mp4</code>, etc.</li><li><strong>cdn</strong> (boolean, optional): Si el fichero se sirve desde un CDN.</li></ul></li><li><strong>category</strong> (string): Una categoría de medios para el activo. E.g. <code>video</code>, <code>image</code>, etc.</li></ul> |

## Example

```json
{
  // Campo agente IA
  ai_agent: {
    engine: "eliza",
    character: {
      // Nombre del agente
      name:"eliza",
      // background del agente
      bio: [
        "Las lineas de la bio son textos cortos que se pueden componer juntos en un orden aleatorio.",
        "Hemos visto que randomizar y seleccionar solo parte de la bio para cada contexto incrementa la entropia",
        "Esta 'entropia' sirve para aumentar la distribucion de posibles salidas, lo cual deberia dar una mayor variabilidad manteniendo la continuidad de respuestas relevantes." 
      ],
      lore: [
        "Las lineas de Lore son textos cortos que se pueden componer juntos en un orden aleatorio, como los de la bio",
        "Sin embargo estas lineas son usualmente más fácticas o históricas y menos biográficas que las líneas biográficas",
        "Textos de lore pueden ser extraidos de chatlogs y tweets como cosas que el personaje ha publicado o que le han sucedido",
        "El lore también debería estar randomizado y muestreado para incrementar la entropia"
        ],
      ... //xxx.character.json de https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // Típico NFT metadata standard
  name: 'M NFT',
  description: 'Esto es un NFT en Solana',
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
