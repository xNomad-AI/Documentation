# AI-NFT 메타데이터

AI-NFT를 생성하는 방식은 기존 NFT와 비슷하지만, 메타데이터에서 AI 에이전트의 설정과 사용하는 엔진을 설명하는 `ai_agent` 필드가 추가됩니다.

## 지원되는 AI 엔진 <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">엔진</th><th width="231">엔진 이름</th><th>캐릭터 파일</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">문서</a></li><li><a href="https://github.com/elizaOS/characterfile">템플릿</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">예시</a></li></ul></td></tr></tbody></table>

## AI-NFT 메타데이터 <a href="#metadata-json" id="metadata-json"></a>

| 필드                        | 타입   | 설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (새로 추가됨)  | object | <p>이 NFT에 연결된 AI 에이전트를 정의하는 설정입니다. </p><ul><li><strong>engine</strong> (string): AI 에이전트를 실행하는 데 사용되는 엔진. 기본값은 "eliza" 입니다.</li><li><strong>character</strong> (object): 에이전트를 설명하는 characterfile JSON 입니다. 여기 <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">문서</a>를 참고하세요.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | 자산(asset)의 이름.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | string | 자산의 설명.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | 자산 로고를 가리키는 URI.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | 자산의 애니메이션을 가리키는 URI.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | string | 자산을 정의하는 외부 URL — 예: 게임의 메인 사이트.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **attributes**               | array  | <p>자산의 특성을 정의하는 속성(attributes) 배열. </p><ul><li><strong>trait_type</strong> (string): 속성 타입.</li><li><strong>value</strong> (string): 해당 속성의 값.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>자산을 정의하는 추가 정보.</p><ul><li><p><strong>files</strong> (array): 자산과 함께 포함될 추가 파일 목록.</p><ul><li><strong>uri</strong> (string): 파일의 URI.</li><li><strong>type</strong> (string): 파일의 유형 (예: <code>image/png</code>, <code>video/mp4</code> 등).</li><li><strong>cdn</strong> (boolean, optional): 파일이 CDN에서 제공되고 있는지 여부.</li></ul></li><li><strong>category</strong> (string): 자신의 미디어 카테고리 (예: <code>video</code>, <code>image</code> 등).</li></ul> |

## 예시

```json
{
  // AI agent 필드
  ai_agent: {
    engine: "eliza",
    character: {
      // 에이전트 이름
      name:"eliza",
      // 배경 정보(bio) 문장
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
  // 일반적인 NFT 메타데이터 표준
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
