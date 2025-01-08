# AI-NFT 메타데이터

AI-NFT를 생성하는 것은 전통적인 NFT 생성과 비슷하지만, **`ai_agent`**라는 필드가 추가되어 AI 에이전트의 구성 및 사용하는 엔진을 설명하며 메타데이터에 저장됩니다.

## 지원되는 AI 엔진

| 엔진 | 엔진 이름 | 캐릭터 파일 |
| --- | --- | --- |
| [Eliza](https://github.com/elizaOS/eliza) by ElizaOS | eliza | [문서](https://elizaos.github.io/eliza/docs/core/characterfile/), [템플릿](https://github.com/elizaOS/characterfile), [예제](https://github.com/elizaOS/eliza/tree/main/characters) |

## AI-NFT 메타데이터 JSON

| 필드 | 타입 | 설명 |
| --- | --- | --- |
| **ai_agent** (새로 추가됨) | 객체 | <p>이 NFT와 연결된 AI 에이전트를 정의하는 구성.</p><ul><li>**engine** (문자열): AI 에이전트를 실행하는 데 사용하는 엔진. 기본값은 "eliza".</li><li>**character** (객체): AI 에이전트를 설명하는 characterfile JSON. [여기](https://github.com/elizaOS/characterfile?tab=readme-ov-file) 참고.</li></ul> |
| **name** | 문자열 | 자산의 이름. |
| **description** | 문자열 | 자산의 설명. |
| **image** | 문자열 | 자산의 로고를 가리키는 URI. |
| **animation_url** | 문자열 | 자산의 애니메이션을 가리키는 URI. |
| **external_url** | 문자열 | 자산을 정의하는 외부 URL. |
| **attributes** | 배열 | 자산의 특성을 정의하는 속성 배열. |
| **properties** | 객체 | 자산을 정의하는 추가 속성들. |

## 예시

```json
{
  // AI 에이전트 필드
  ai_agent: {
    engine: "eliza",
    character: {
      // 에이전트 이름
      name:"eliza",
      // 배경 설명
      bio: [
        "바이오 라인은 각 짧은 스니펫으로 구성되며 무작위로 조합될 수 있습니다.",
        "각 문맥에서 바이오의 일부만 무작위로 선택하면 엔트로피가 증가합니다.",
        "이 '엔트로피'는 가능한 출력의 분포를 넓혀주며, 더욱 다양하지만 지속적으로 관련된 응답을 제공합니다."
      ],
      lore: [
        "로어 라인은 바이오와 같이 짧은 스니펫으로 구성되며 무작위로 조합될 수 있습니다.",
        "하지만, 로어는 일반적으로 바이오 라인보다 더 사실적이거나 역사적입니다.",
        "로어 라인은 채팅 로그나 트윗에서 추출하여 해당 캐릭터의 사건이나 경험을 반영할 수 있습니다.",
        "로어도 랜덤화하고 샘플링하여 문맥에서 엔트로피를 증가시키는 것이 좋습니다."
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // 일반적인 NFT 메타데이터 표준
  name: '내 NFT',
  description: '이것은 Solana 기반 NFT입니다.',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: '특성1',
      value: '값1',
    },
    {
      trait_type: '특성2',
      value: '값2',
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
