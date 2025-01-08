# AI-NFT 元数据

创建 AI-NFT 与传统 NFT 的创建类似，但会增加一个名为 **`ai_agent`** 的字段，该字段描述 AI 代理的配置及所使用的引擎，并存储在元数据中。

## 支持的 AI 引擎

| 引擎 | 引擎名称 | 角色文件 |
| --- | --- | --- |
| [Eliza](https://github.com/elizaOS/eliza) by ElizaOS | eliza | [文档](https://elizaos.github.io/eliza/docs/core/characterfile/), [模板](https://github.com/elizaOS/characterfile), [示例](https://github.com/elizaOS/eliza/tree/main/characters) |

## AI-NFT 元数据 JSON

| 字段 | 类型 | 描述 |
| --- | --- | --- |
| **ai_agent** (新增) | 对象 | <p>定义与此 NFT 相关联的 AI 代理的配置。</p><ul><li>**engine** (字符串): 用于运行 AI 代理的引擎。默认值为 "eliza".</li><li>**character** (对象): 描述 AI 代理的 characterfile JSON. [参考这里](https://github.com/elizaOS/characterfile?tab=readme-ov-file).</li></ul> |
| **name** | 字符串 | 资产的名称。 |
| **description** | 字符串 | 资产的描述。 |
| **image** | 字符串 | 指向资产徽标的 URI。 |
| **animation_url** | 字符串 | 指向资产动画的 URI。 |
| **external_url** | 字符串 | 定义资产的外部 URL。 |
| **attributes** | 数组 | 定义资产特性的属性数组。 |
| **properties** | 对象 | 定义资产的附加属性。 |

## 示例

```json
{
  // AI 代理字段
  ai_agent: {
    engine: "eliza",
    character: {
      // 代理名称
      name:"eliza",
      // 背景描述
      bio: [
        "Bio 行由简短的片段组成，可以随机组合。",
        "在每种上下文中，仅选择 Bio 的一部分会增加熵。",
        "这种“熵”会扩大可能输出的分布，提供更加多样但始终相关的响应。"
      ],
      lore: [
        "Lore 行与 Bio 类似，由简短的片段组成，可以随机组合。",
        "然而，Lore 通常比 Bio 更真实或历史性。",
        "Lore 行可以从聊天记录或推文中提取，以反映该角色的事件或经历。",
        "Lore 也可以随机化并取样，从而在上下文中增加熵。"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // 常见的 NFT 元数据标准
  name: '我的 NFT',
  description: '这是一个基于 Solana 的 NFT.',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: '特性1',
      value: '值1',
    },
    {
      trait_type: '特性2',
      value: '值2',
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
