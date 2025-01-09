# AI-NFT 元數據

建立 AI-NFT 與傳統 NFT 的建立類似，但會增加一個名為 **`ai_agent`** 的字段，該字段描述 AI 代理的配置及所使用的引擎，並儲存在元資料中。

## 支援的 AI 引擎

| 引擎 | 引擎名稱 | 角色檔 |
| --- | --- | --- |
| [Eliza](https://github.com/elizaOS/eliza) by ElizaOS | eliza | [文件](https://elizaos.github.io/eliza/docs/core/characterfile/), [範本]( https://github.com/elizaOS/characterfile), [範例](https://github.com/elizaOS/eliza/tree/main/characters) |

## AI-NFT 元資料 JSON

| 字段 | 類型 | 描述 |
| --- | --- | --- |
| **ai_agent** (新增) | 物件 | <p>定義與此 NFT 相關聯的 AI 代理程式的配置。 </p><ul><li>**engine** (字串): 用於執行 AI 代理的引擎。預設值為"eliza".</li><li>**character** (物件): 描述AI 代理程式的characterfile JSON. [參考這裡](https://github.com/elizaOS/characterfile?tab=readme -ov-file).</li></ul> |
| **name** | 字串 | 資產的名稱。 |
| **description** | 字串 | 資產的描述。 |
| **image** | 字串 | 指向資產標誌的 URI。 |
| **animation_url** | 字串 | 指向資產動畫的 URI。 |
| **external_url** | 字串 | 定義資產的外部 URL。 |
| **attributes** | 陣列 | 定義資產特性的屬性陣列。 |
| **properties** | 物件 | 定義資產的附加屬性。 |

## 範例

```json
{
    // AI 代理字段
    ai_agent: {
    engine: "eliza",
    character: {
            // 代理名稱
    name: "eliza",
            // 背景描述
    bio: [
                "Bio 行由簡短的片段組成，可以隨機組合。",
                "在每種上下文中，僅選擇 Bio 的一部分會增加熵。",
                "這種「熵」會擴大可能輸出的分佈，提供更多樣化但始終相關的反應。"
            ],
    lore: [
                "Lore 行與 Bio 類似，由簡短的片段組成，可以隨機組合。",
                "然而，Lore 通常比 Bio 更真實或歷史性。",
                "Lore 行可以從聊天記錄或推文中提取，以反映該角色的事件或經歷。",
                "Lore 也可以隨機化並取樣，從而在上下文中增加熵。"
            ],
    ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
        }
    },
    // 常見的 NFT 元資料標準
    name: '我的 NFT',
    description: '這是一個基於 Solana 的 NFT.',
    image: imageUri[
        0
    ],
    external_url: 'https: //example.com',
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
    uri: imageUri[
                    0
                ],
    type: 'image/jpeg',
            },
        ],
    category: 'image',
    },
}
```