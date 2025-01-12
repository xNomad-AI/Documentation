
# המטא-דאטה של AI-NFT

תהליך יצירת AI-NFT דומה לתהליך יצירת NFT קונבנציונלי, אך מתווסף שדה **`ai_agent`**. שדה זה מציין את הגדרות והפעלת סוכן ה-AI, והמידע נשמר במטא-דאטה.

## מנועי AI נתמכים <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">מנוע</th><th width="231">שם מנוע</th><th>קובץ דמויות</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> (ElizaOS)</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">הוראות שימוש</a></li><li><a href="https://github.com/elizaOS/characterfile">תבנית</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">דוגמאות</a></li></ul></td></tr></tbody></table>

## AI-NFT JSON של המטא-דאטה <a href="#metadata-json" id="metadata-json"></a>

| שדה                          | סוג    | תיאור                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (חדש)          | object | <p>הגדרות הסוכן המלאכותי AI המחובר ל-NFT הזה</p><ul><li><strong>engine</strong> (string): המנוע המשמש להפעלת סוכן ה-AI. ברירת המחדל היא "eliza"</li><li><strong>character</strong> (object): קובץ JSON של דמות המתאר את הסוכן ה-AI. לפרטים נוספים, בקרו ב-<a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">כאן</a>.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | שם הנכס                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **description**              | string | תיאור הנכס                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | URI של הלוגו המייצג את הנכס                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | URI של האנימציה המייצגת את הנכס                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **external\_url**            | string | URI חיצוני המתאר את הנכס — למשל האתר הרשמי של המשחק                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>מערך של מאפיינים המגדירים את הנכס</p><ul><li><strong>trait_type</strong> (string): סוג המאפיין</li><li><strong>value</strong> (string): ערך המאפיין</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>מאפיינים נוספים המגדירים את הנכס</p><ul><li><p><strong>files</strong> (array): קבצים נוספים הכלולים עם הנכס</p><ul><li><strong>uri</strong> (string): URI של הקובץ</li><li><strong>type</strong> (string): סוג הקובץ, לדוגמה <code>image/png</code>, <code>video/mp4</code></li><li><strong>cdn</strong> (boolean, optional): האם הקובץ מסופק מ-CDN</li></ul></li><li><strong>category</strong> (string): קטגוריית המדיה של הנכס, לדוגמה <code>video</code>, <code>image</code></li></ul> |

## דוגמה
```json
{
  // שדה סוכן AI
  ai_agent: {
    engine: "eliza",
    character: {
      // שם הסוכן
      name: "eliza",
      // הצהרות רקע
      bio: [
        "שורות ביוגרפיה הן קטעים קצרים שניתן להרכיבם יחד בסדר אקראי.",
        "מצאנו שזה מגדיל את האקראיות לבחור חלק מהביוגרפיה לכל הקשר.",
        "האקראיות הזו מגדילה את טווח האפשרויות של התשובות, מה שמוביל לתשובות מגוונות אך עדיין רלוונטיות."
      ],
      lore: [
        "שורות סיפור רקע הן קטעים קצרים שניתן להרכיב יחד בסדר אקראי, בדומה לביוגרפיה.",
        "עם זאת, הן בדרך כלל יותר עובדתיות או היסטוריות ופחות ביוגרפיות.",
        "שורות סיפור רקע יכולות להילקח מלוגי צ'אט וציטוטים כתיאורים של דמויות או אירועים שקרו להן.",
        "יש להוסיף גם אקראיות לשורות סיפור הרקע כדי להגדיל את האקראיות בהקשר."
      ],
      ... // xxx.character.json מ-https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // מטא-דאטה טיפוסי ל-NFT
  name: 'ה-NFT שלי',
  description: 'זהו NFT על Solana',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: 'מאפיין1',
      value: 'ערך1',
    },
    {
      trait_type: 'מאפיין2',
      value: 'ערך2',
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
