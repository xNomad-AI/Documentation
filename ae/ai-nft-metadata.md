# بيانات AI-NFT الوصفية

إنشاء AI-NFT يشبه تمامًا إنشاء NFT التقليدي، **مع** إضافة حقل `ai_agent` الذي يصف إعدادات وكيل الذكاء الاصطناعي والمحرك الذي يستخدمه، والمحفوظة في البيانات الوصفية.

## محرك الذكاء الاصطناعي المدعوم <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">المحرك</th><th width="231">اسم المحرك</th><th>ملف الشخصية</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> بواسطة ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">التوثيق</a></li><li><a href="https://github.com/elizaOS/characterfile">القالب</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">الأمثلة</a></li></ul></td></tr></tbody></table>

## JSON بيانات AI-NFT الوصفية <a href="#metadata-json" id="metadata-json"></a>

| الحقل                        | النوع   | الوصف                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (أضيف حديثاً)  | كائن | <p>إعدادات وكيل الذكاء الاصطناعي المرتبط بهذا الـ NFT. </p><ul><li><strong>المحرك</strong> (نص): المحرك المستخدم لتشغيل وكيل الذكاء الاصطناعي. افتراضي كـ "eliza".</li><li><strong>الشخصية</strong> (كائن): ملف JSON الذي يصف وكيل الذكاء الاصطناعي. تحقق من <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">هنا</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | نص | اسم الأصل.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **description**              | نص | وصف الأصل.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | نص | عنوان URI يشير إلى شعار الأصل.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | نص | عنوان URI يشير إلى الرسوم المتحركة للأصل.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**            | نص | عنوان URI يشير إلى رابط خارجي يعرّف الأصل — مثل الموقع الرئيسي للعبة.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | مصفوفة  | <p>مصفوفة من السمات التي تحدد خصائص الأصل.</p><ul><li><strong>trait_type</strong> (نص): نوع السمة.</li><li><strong>value</strong> (نص): القيمة لتلك السمة.</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | كائن | <p>خصائص إضافية تحدد الأصل.</p><ul><li><p><strong>الملفات</strong> (مصفوفة): ملفات إضافية لتضمينها مع الأصل.</p><ul><li><strong>uri</strong> (نص): عنوان URI للملف.</li><li><strong>type</strong> (نص): نوع الملف. مثل <code>image/png</code>، <code>video/mp4</code>، إلخ.</li><li><strong>cdn</strong> (منطقي، اختياري): ما إذا كان الملف يُخدم من شبكة CDN.</li></ul></li><li><strong>category</strong> (نص): فئة الوسائط للأصل. مثل <code>video</code>، <code>image</code>، إلخ.</li></ul> |

## مثال

```json
{
  // حقل وكيل الذكاء الاصطناعي
  ai_agent: {
    engine: "eliza",
    character: {
      // اسم الوكيل
      name:"eliza",
      // بيانات الخلفية
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
      ... //xxx.character.json من https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // معيار البيانات الوصفية لـ NFT النموذجي
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