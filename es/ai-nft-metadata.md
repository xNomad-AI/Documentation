# Metadata de AI-NFT

Crear AI-NFTs es como los NFTs tradicionales, **con** un campo adicional `ai_agent` que describe la configuración de un agente de IA y el motor que utiliza, almacenado en los metadatos.

## Motor de IA Compatible <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Engine</th><th width="231">Engine Name</th><th>Character File</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Documentation</a></li><li><a href="https://github.com/elizaOS/characterfile">Template</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Example</a></li></ul></td></tr></tbody></table>

## JSON de Metadata AI-NFT <a href="#metadata-json" id="metadata-json"></a>

| Campo                         | Tipo   | Descripción                                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai_agent** (Recién añadido) | objeto | La configuración que define el agente de IA conectado con este NFT.<br>- **engine** (string): el motor utilizado para ejecutar el agente de IA. Por defecto es "eliza".<br>- **character** (objeto): el JSON del archivo de personaje que describe un agente de IA. Consulta [aquí](https://github.com/elizaOS/characterfile?tab=readme-ov-file).                                                               |
| **name**                      | string | Nombre del activo.                                                                                                                                                                                                                                                                                                                                                                                              |
| **description**               | string | Descripción del activo.                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                     | string | URI que apunta al logo del activo.                                                                                                                                                                                                                                                                                                                                                                              |
| **animation_url**             | string | URI que apunta a la animación del activo.                                                                                                                                                                                                                                                                                                                                                                       |
| **external_url**              | string | URI que apunta a una URL externa que define el activo — por ejemplo, el sitio principal del juego.                                                                                                                                                                                                                                                                                                              |
| **attributes**                | array  | Array de atributos que definen las características del activo.<br>- **trait_type** (string): El tipo de atributo.<br>- **value** (string): El valor para ese atributo.                                                                                                                                                                                                                                          |
| **properties**                | objeto | Propiedades adicionales que definen el activo.<br>- **files** (array): Archivos adicionales para incluir con el activo.<br> - **uri** (string): URI del archivo.<br> - **type** (string): Tipo de archivo. Ej. `image/png`, `video/mp4`, etc.<br> - **cdn** (boolean, opcional): Si el archivo se sirve desde un CDN.<br>- **category** (string): Categoría de medio para el activo. Ej. `video`, `image`, etc. |

## Ejemplo

```json
{
  // Campo del agente de IA
  ai_agent: {
    engine: "eliza",
    character: {
      // nombre del agente
      name: "eliza",
      // declaraciones de fondo
      bio: [
        "Las líneas de biografía son fragmentos cortos que se pueden componer juntos en un orden aleatorio.",
        "Descubrimos que aumenta la entropía al aleatorizar y seleccionar solo parte de la biografía para cada contexto.",
        "Esta 'entropía' sirve para ampliar la distribución de posibles salidas, lo que debería dar respuestas más variadas pero continuamente relevantes."
      ],
      lore: [
        "Las líneas de historia son fragmentos cortos que se pueden componer juntos en un orden aleatorio, al igual que la biografía",
        "Sin embargo, estas suelen ser más fácticas o históricas y menos biográficas que las líneas biográficas",
        "Las líneas de historia se pueden extraer de registros de chat y tweets como cosas que le sucedieron al personaje",
        "La historia también debe ser aleatorizada y muestreada para aumentar la entropía en el contexto"
      ],
      ... //xxx.character.json de https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // estándar de metadatos NFT típico
  name: 'Mi NFT',
  description: 'Este es un NFT en Solana',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: 'rasgo1',
      value: 'valor1',
    },
    {
      trait_type: 'rasgo2',
      value: 'valor2',
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
