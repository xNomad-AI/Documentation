# Getting Started

Now, you can access and interact with your xNomad agent through the xNomad agent API.&#x20;

| PARAM       | VALUE                                     |
| ----------- | ----------------------------------------- |
| base\_url\* | `https://core.xnomad.fun`                 |
| api\_key    | [Apply for an API Key](get-an-api-key.md) |

&#x20;       To support compatibility, you may also use `https://core.xnomad.fun/v1`. The `v1` path refers to the API version, not the model version.

### Invoke the Chat API

Once you have your API key, you can begin making your first Agent request using standard OpenAI completion API methods. Below is a simple example using `curl` for non-streamed output.

<pre class="language-bash"><code class="lang-bash"><strong>curl -X POST https://core.xnomad.fun/v1/chat/completions \
</strong>  -H "Content-Type: application/json" \
  -H "Authorization: Bearer &#x3C;Your API Key>" \
  -d '{
        "model": "",
        "messages": [
          {"role": "user", "content": "Hey, who are you and what do you do?"}
        ],
        "temperature": 0.7,
        "max_tokens": 1000
      }'
</code></pre>

