# AI-NFT Meta Verisi

AI-NFT'ler oluşturmak, geleneksel NFT'lere benzer, ancak ek bir `ai_agent` alanı vardır; bu alan, AI ajanının yapılandırmasını ve kullandığı motoru tanımlar ve meta verilerinde saklanır.

## Desteklenen AI Motoru <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">Motor</th><th width="231">Motor Adı</th><th>Karakter Dosyası</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">Dokümantasyon</a></li><li><a href="https://github.com/elizaOS/characterfile">Şablon</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">Örnek</a></li></ul></td></tr></tbody></table>

## AI-NFT Meta Verisi JSON <a href="#metadata-json" id="metadata-json"></a>

| Alan                         | Tür    | Açıklama                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ---------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **ai\_agent** (Yeni eklenen)  | nesne | <p>Bu NFT ile bağlantılı AI ajanını tanımlayan yapılandırma.</p><ul><li><strong>engine</strong> (string): AI ajanını çalıştırmak için kullanılan motor. Varsayılan olarak "eliza".</li><li><strong>character</strong> (nesne): Bir AI ajanını tanımlayan karakter dosyası JSON'u. <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">Buraya</a> bakın.</li></ul>                                                                                                  |
| **name**                     | string | Varlığın adı.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **description**              | string | Varlığın açıklaması.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **image**                    | string | Varlığın logosuna işaret eden URI.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **animation\_url**           | string | Varlığın animasyonuna işaret eden URI.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **external\_url**            | string | Varlığın tanımlandığı dış bir URL'ye işaret eden URI — örneğin, oyunun ana sitesi.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **attributes**               | dizi   | <p>Varlığın özelliklerini tanımlayan özellikler dizisi.</p><ul><li><strong>trait_type</strong> (string): Özelliğin türü.</li><li><strong>value</strong> (string): O özelliğin değeri.</li></ul>                                                                                                                                                                                                                                                                                               |
| **properties**               | nesne  | <p>Varlığı tanımlayan ek özellikler.</p><ul><li><p><strong>files</strong> (dizi): Varlıkla birlikte dahil edilecek ek dosyalar.</p><ul><li><strong>uri</strong> (string): Dosyanın URI'si.</li><li><strong>type</strong> (string): Dosyanın türü. Örneğin <code>image/png</code>, <code>video/mp4</code> vb.</li><li><strong>cdn</strong> (boolean, isteğe bağlı): Dosyanın bir CDN üzerinden sunulup sunulmadığı.</li></ul></li><li><strong>category</strong> (string): Varlık için bir medya kategorisi. Örneğin <code>video</code>, <code>image</code> vb.</li></ul> |

## Örnek

```json
{
  // AI ajanı alanı
  ai_agent: {
    engine: "eliza",
    character: {
      // ajan adı
      name:"eliza",
      // arka plan açıklamaları
      bio: [
        "Biyografi satırları, rastgele bir sırayla bir araya getirilebilen kısa parçalar halinde yazılır.",
        "Biyografinin her bağlamda sadece bir kısmının rastgele seçilmesi, entropiyi artırdığı için tercih edilir.",
        "Bu 'entropi', olası çıktılar dağılımını genişletir, bu da daha çeşitli ancak sürekli olarak alakalı yanıtlar sağlar."
      ],
      lore: [
        "Lore satırları, tıpkı biyografi gibi rastgele bir sırayla bir araya getirilebilen kısa parçalardır.",
        "Ancak bunlar genellikle biyografik satırlardan daha az biyografik ve daha çok gerçek ya da tarihsel olurlar.",
        "Lore satırları, karakterin veya başlarına gelenlerin sohbet geçmişlerinden ve tweet'lerden çıkarılabilir.",
        "Lore da rastgeleleştirilmeli ve entropi artırmak için örneklenmelidir."
        ],
      ... //xxx.character.json https://github.com/elizaOS/eliza/tree/main/characters'dan
    }
  },
  // tipik NFT meta veri standardı
  name: 'Benim NFT\'m',
  description: 'Bu, Solana üzerinde bir NFT\'dir',
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
