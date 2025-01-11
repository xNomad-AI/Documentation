# AI-NFT এর মেটাডেটা

AI-NFT তৈরি প্রচলিত NFT তৈরির প্রক্রিয়ার মতো, তবে **`ai_agent` ফিল্ড** যুক্ত করা হয়েছে। এই ফিল্ডটি AI এজেন্টের সেটিংস এবং ব্যবহৃত ইঞ্জিনের তথ্য নির্দেশ করে, যা মেটাডেটাতে সংরক্ষিত হয়।

## সমর্থিত AI ইঞ্জিন <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">ইঞ্জিন</th><th width="231">ইঞ্জিনের নাম</th><th>ক্যারেক্টার ফাইল</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> (ElizaOS)</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">ব্যবহার নির্দেশিকা</a></li><li><a href="https://github.com/elizaOS/characterfile">টেমপ্লেট</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">উদাহরণ</a></li></ul></td></tr></tbody></table>

## AI-NFT মেটাডেটা JSON <a href="#metadata-json" id="metadata-json"></a>

| ফিল্ড                         | প্রকার    | বর্ণনা                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ---------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **ai\_agent** (নতুন সংযোজন) | object | <p>এই NFT-তে সংযুক্ত AI এজেন্টের সেটিংস</p><ul><li><strong>engine</strong> (string): AI এজেন্ট চালানোর জন্য ব্যবহৃত ইঞ্জিন। ডিফল্ট হলো "eliza"</li><li><strong>character</strong> (object): AI এজেন্টকে বর্ণনা করার জন্য JSON ফরম্যাটে ক্যারেক্টার ফাইল। বিস্তারিত জানতে <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">এখানে</a> দেখুন।</li></ul>                                                                                                                                                                              |
| **name**                     | string | সম্পদের নাম                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **description**              | string | সম্পদের বর্ণনা                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **image**                    | string | সম্পদের লোগো নির্দেশকারী URI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **animation\_url**           | string | সম্পদের অ্যানিমেশন নির্দেশকারী URI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **external\_url**            | string | সম্পদ সম্পর্কিত বাইরের URL নির্দেশকারী URI — উদাহরণস্বরূপ, গেমের অফিসিয়াল ওয়েবসাইট                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **attributes**               | array  | <p>সম্পদের বৈশিষ্ট্য সংজ্ঞায়িত করা একটি বৈশিষ্ট্য অ্যারে</p><ul><li><strong>trait_type</strong> (string): বৈশিষ্ট্যের ধরন</li><li><strong>value</strong> (string): বৈশিষ্ট্যের মান</li></ul>                                                                                                                                                                                                                                                                                                                                       |
| **properties**               | object | <p>সম্পদের বৈশিষ্ট্য সংজ্ঞায়িত করা অতিরিক্ত বৈশিষ্ট্য</p><ul><li><p><strong>files</strong> (array): সম্পদের সঙ্গে অন্তর্ভুক্ত অতিরিক্ত ফাইল</p><ul><li><strong>uri</strong> (string): ফাইলের URI</li><li><strong>type</strong> (string): ফাইলের প্রকার, উদাহরণস্বরূপ <code>image/png</code>, <code>video/mp4</code></li><li><strong>cdn</strong> (boolean, optional): ফাইল CDN থেকে সরবরাহ করা হয় কি না</li></ul></li><li><strong>category</strong> (string): সম্পদের মিডিয়া ক্যাটেগরি, উদাহরণস্বরূপ <code>video</code>, <code>image</code></li></ul> |

## উদাহরণ

```json
{
  // AI agent field
  ai_agent: {
    engine: "eliza",
    character: {
      // agent name
      name:"eliza",
      // background statements
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
  // typical NFT metadata standard
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
