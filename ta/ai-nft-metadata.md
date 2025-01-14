# AI-NFT மெட்டாடேட்டா  

AI-NFT உருவாக்கம் பாரம்பரிய NFT உருவாக்கத் செயல்முறையுடன் ஒத்துள்ளது, ஆனால், **`ai_agent` புலம்** சேர்க்கப்பட்டுள்ளது. இந்த புலம் AI முகவரியின் அமைப்புகள் மற்றும் பயன்படுத்தப்படும் என்ஜினைப் குறிக்கிறது, மேலும் இந்த தகவல் மெட்டாடேட்டாவில் சேமிக்கப்படுகிறது.  

## ஆதரவு AI என்ஜின்கள் <a href="#metadata-json" id="metadata-json"></a>  

<table><thead><tr><th width="224">என்ஜின்</th><th width="231">என்ஜின் பெயர்</th><th>கேரக்டர் கோப்பு</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> (ElizaOS)</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">பயன்பாட்டு விளக்கம்</a></li><li><a href="https://github.com/elizaOS/characterfile">வார்ப்புரு</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">மாதிரிகள்</a></li></ul></td></tr></tbody></table>  

## AI-NFT மெட்டாடேட்டா JSON <a href="#metadata-json" id="metadata-json"></a>  

| புலம்                          | வகை     | விளக்கம்                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |  
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |  
| **ai\_agent** (புதியது)  | object | <p>இந்த NFT உடன் இணைக்கப்பட்ட AI முகவரியின் அமைப்பு</p><ul><li><strong>engine</strong> (string): AI முகவர் செயல்பட பயன்படும் என்ஜின். இயல்புநிலை "eliza"</li><li><strong>character</strong> (object): AI முகவரியை விளக்கும் JSON வடிவத்தில் கேரக்டர் கோப்பு. மேலும் விவரங்களுக்கு <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">இங்கு</a> பார்க்கவும்.</li></ul>  
                                                                                                                                                                                   |  
| **name**                     | string | சொத்தின் பெயர்                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |  
| **description**              | string | சொத்தின் விளக்கம்                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |  
| **image**                    | string | சொத்தின் லோகோவை குறிக்கும் URI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |  
| **animation\_url**           | string | சொத்தின் அனிமேஷனை குறிக்கும் URI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |  
| **external\_url**            | string | சொத்தை விளக்கும் வெளியூர் URL, உதாரணமாக விளையாட்டின் உத்தியோகப்பூர்வ இணையதளம்                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |  
| **attributes**               | array  | <p>சொத்தின் பண்புகளை வரையறுக்கும் பண்புகளின் வரிசை</p><ul><li><strong>trait_type</strong> (string): பண்பு வகை</li><li><strong>value</strong> (string): பண்பு மதிப்பு</li></ul>                                                                                                                                                                                                                                                                                                                                        |  
| **properties**               | object | <p>சொத்தின் பண்புகளை வரையறுக்கும் கூடுதல் பண்புகள்</p><ul><li><p><strong>files</strong> (array): சொத்துடன் சேர்க்கப்பட்ட கூடுதல் கோப்புகள்</p><ul><li><strong>uri</strong> (string): கோப்பின் URI</li><li><strong>type</strong> (string): கோப்பு வகை, உதாரணமாக <code>image/png</code>, <code>video/mp4</code></li><li><strong>cdn</strong> (boolean, optional): கோப்பு CDN மூலம் வழங்கப்பட்டதா என்பது</li></ul></li><li><strong>category</strong> (string): சொத்தின் மீடியா வகை, உதாரணமாக <code>video</code>, <code>image</code></li></ul> |  

## எடுத்துக்காட்டு  

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
```