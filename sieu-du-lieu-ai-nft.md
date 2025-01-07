# Dữ liệu AI-NFT

Việc tạo ra AI-NFT giống như việc tạo NFT truyền thống, **với** một trường bổ sung `ai_agent` mô tả cấu hình của tác nhân AI và động cơ mà nó sử dụng, được lưu trữ trong dữ liệu metadata.

## Các Động Cơ AI Hỗ Trợ <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Động Cơ</th><th width="231">Tên Động Cơ</th><th>Tệp Nhân Vật</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> của ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Tài liệu</a></li><li><a href="https://github.com/elizaOS/characterfile">Mẫu</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Ví dụ</a></li></ul></td></tr></tbody></table>

## Dữ liệu AI-NFT JSON <a href="#metadata-json" id="metadata-json"></a>

| Trường                        | Kiểu   | Mô tả                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (Mới thêm)     | object | <p>Cấu hình xác định tác nhân AI kết nối với NFT này. </p><ul><li><strong>engine</strong> (string): động cơ được sử dụng để vận hành tác nhân AI. Mặc định là "eliza".</li><li><strong>character</strong> (object): tệp JSON mô tả nhân vật của tác nhân AI. Xem <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">tại đây</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | Tên của tài sản.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | Mô tả về tài sản.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI chỉ đến logo của tài sản.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI chỉ đến hoạt ảnh của tài sản.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | URI chỉ đến một URL ngoài để định nghĩa tài sản — ví dụ: trang web chính của trò chơi.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>Mảng các thuộc tính xác định đặc điểm của tài sản.</p><ul><li><strong>trait_type</strong> (string): Loại thuộc tính.</li><li><strong>value</strong> (string): Giá trị của thuộc tính đó.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>Các thuộc tính bổ sung xác định tài sản.</p><ul><li><p><strong>files</strong> (array): Các tệp bổ sung để kèm theo tài sản.</p><ul><li><strong>uri</strong> (string): URI của tệp.</li><li><strong>type</strong> (string): Loại tệp. Ví dụ: <code>image/png</code>, <code>video/mp4</code>, v.v.</li><li><strong>cdn</strong> (boolean, tùy chọn): Liệu tệp có được phục vụ từ một CDN hay không.</li></ul></li><li><strong>category</strong> (string): Danh mục phương tiện của tài sản. Ví dụ: <code>video</code>, <code>image</code>, v.v.</li></ul> |

## Ví Dụ

```json
{
  // Trường tác nhân AI
  ai_agent: {
    engine: "eliza",
    character: {
      // tên tác nhân
      name:"eliza",
      // câu giới thiệu
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
      ... //xxx.character.json từ https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // Dữ liệu metadata NFT chuẩn
  name: 'My NFT',
  description: 'Đây là một NFT trên Solana',
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
