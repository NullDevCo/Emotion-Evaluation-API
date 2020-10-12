# Emotion-Evaluation-API

# :exclamation: DISCONTINNUED

A newer version of the project can be found here: 
https://github.com/EMMA-Emotion-AI

---

**Better Version:** <br>
[nulldevco.github.io/Emotion-Evaluation-API](https://nulldevco.github.io/Emotion-Evaluation-API/)

This is the documentation of the NullDev Emotion Evaluation API

Type of API: Representational State Transfer (REST)

REST Endpoint: [api.nulldev.org/emo](https://api.nulldev.org/emo)

More Info: [https://api.nulldev.org](https://api.nulldev.org)

<br>

**Note:** This API is HTTPS only. While HTTP calls normaly get redirected to HTTPS, it could happen that the API returns `301 Moved Permanently`.

<br>

<hr>

## POST Data / Calls

| Call | Description | 
|------|-------------|
| text        | The text to evaluate the emotions from          |
| split       | Evaluate the sentence AND each word seperately  |
| prettyprint | Shall the JSON output be formatted / prettified |

<hr>

## Responses

| Response | Description | 
|----------|-------------|
| error               | The error code of the operation                                           |
| given_text          | The text from which the emotion was evaluated                             |
| emotion_tone        | Whenether the input was evaluated to positive or negative                 |
| probability_value   | The calculated probability value                                          |
| probability_percent | Same as `probability_value` but rounded and in per cent                   |
| given_sentence      | The whole input text; **Only set, if** `split` = **1**                    |
| given_words         | Array of all words seperately evaluated; **Only set, if** `split` = **1** |

<hr>

## Error Codes

| Code | Meaning | 
|------|---------|
| 0 | No Error / Successful operation |
| 1 | No Input Provided               |
| 2 | Text is too long                |
| 3 | Rate Limit reached              |
| 4 | Unknown Exception               |

<hr>

<br>

### Call Types:

- `text`: String - URL Encoded; Example: `hello+there`
- `split`: Integer - Either `0` for no Split or `1` for Split
- `prettyprint`: Integer - Either `0` for no PrettyPrint or `1` for PrettyPrint

### Callbacks:

0.)

<a href="https://api.nulldev.org/emo?">`?`</a>

```javascript
{"error":1,"given_text":null,"message":"No Input provided. Usage: ?text={query}","copyright":"NullDev"}
```

<hr>

1.)

<a href="https://api.nulldev.org/emo?text=hello+there">`?text=hello+there`</a>

```javascript
{"error":0,"given_text":"hello there","emotion_tone":"positive","probability_value":0.8804341585225719,"probability_percent":"88.04%","copyright":"NullDev"}
```

<hr>

2.)

<a href="https://api.nulldev.org/emo?text=hello+there&prettyprint=1">`?text=hello+there&prettyprint=1`</a>

```javascript
{
    "error": 0,
    "given_text": "hello there",
    "emotion_tone": "positive",
    "probability_value": 0.8804341585225719,
    "probability_percent": "88.04%",
    "copyright": "NullDev"
}
```

<hr>

3.)

<a href="https://api.nulldev.org/emo?text=hello+there&split=1">`?text=hello+there&split=1`</a>

```javascript
{"given_sentence":{"error":0,"given_text":"hello there","emotion_tone":"positive","probability_value":0.8804341585225719,"probability_percent":"88.04%","copyright":"NullDev"},"given_words":[{"error":0,"given_text":"hello","emotion_tone":"positive","probability_value":0.8804341585225719,"probability_percent":"88.04%","copyright":"NullDev"},{"error":0,"given_text":"there","emotion_tone":"neutral","probability_value":0.5,"probability_percent":"50%","copyright":"NullDev"}]}
```

<hr>

4.)

<a href="https://api.nulldev.org/emo?text=hello+there&split=1&prettyprint=1">`?text=hello+there&split=1&prettyprint=1`</a>

```javascript
{
    "given_sentence": {
        "error": 0,
        "given_text": "hello there",
        "emotion_tone": "positive",
        "probability_value": 0.8804341585225719,
        "probability_percent": "88.04%",
        "copyright": "NullDev"
    },
    "given_words": [
        {
            "error": 0,
            "given_text": "hello",
            "emotion_tone": "positive",
            "probability_value": 0.8804341585225719,
            "probability_percent": "88.04%",
            "copyright": "NullDev"
        },
        {
            "error": 0,
            "given_text": "there",
            "emotion_tone": "neutral",
            "probability_value": 0.5,
            "probability_percent": "50%",
            "copyright": "NullDev"
        }
    ]
}
```

<hr>

Good examples:

[https://api.nulldev.org/emo?text=I+am+happy!&prettyprint=1](https://api.nulldev.org/emo?text=I+am+happy!&prettyprint=1)

[https://api.nulldev.org/emo?text=I+am+sad&prettyprint=1&split=1](https://api.nulldev.org/emo?text=I+am+sad&prettyprint=1&split=1)

[https://api.nulldev.org/emo?text=I+am+okay](https://api.nulldev.org/emo?text=I+am+okay)

[https://api.nulldev.org/emo?text=I+get+it&split=0](https://api.nulldev.org/emo?text=I+get+it&split=0)

<hr>

**Disclaimer**: <br>
This API provided by us (NullDev) is public, but comes with zero warrenty. We cannot ensure uptime. However, we still try to keep all of our API's online!
