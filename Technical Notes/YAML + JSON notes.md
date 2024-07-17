---
created: 2021-08-29
tags:
  - metadata
---
# YAML + JSON notes

nav links: [[START HERE]], [[YAML Cheatsheet]], [[Writing in YAML style]], [[Markdown, YAML & JSON]]

## Converting from yaml to json

YAML notes must be properly formatted as YAML otherwise the conversion to JSON will not work. Therefore:

- All **notes** within a scene file must start with `##` or up to 6 `######`

==NOTE:== use VS Code extension - **YAML ❤️ JSON** - to "Easily convert yaml to json and ==json to yaml=="

## Comparing json & yaml

Below from https://www.json2yaml.com/ (a very useful site):

```yaml
---
# <- yaml supports comments, json does not
# did you know you can embed json in yaml?
# try uncommenting the next line
# { foo: 'bar' }

json:
  - rigid
  - better for data interchange
yaml:
  - slim and flexible
  - better for configuration
object:
  key: value
  array:
    - null_value:
    - boolean: true
    - integer: 1
paragraph: >
   blank lines denote

   paragraph breaks
content: |-
   or we
   can auto
   convert line breaks
   to save space
```

## Example converting yaml to json

### this yaml

```yaml
## NOTE as a yaml comment

description:
  Mei's party, extract
  end of scene
convoturns:
  - voiceType: HayleySays
    lexia: I must've...
  - voiceType: Frankie
    lexia: It wasn't you, Hayley.
  - voiceType: HayleyPonders
    ponder:
    - lexia: No one's to blame.
    - lexia: We all broke the mirror.
    - lexia: The mirror broke itself
    - lexia: Miss Nobody broke the mirror
goTo: [[sc16]]
```

### converts to this json

```json
{
  "description": "Mei's party, extract end of scene",
  "convoturns": [
    {
      "voiceType": "HayleySays",
      "lexia": "I must've..."
    },
    {
      "voiceType": "Frankie",
      "lexia": "It wasn't you, Hayley."
    },
    {
      "voiceType": "HayleyPonders",
      "ponder": [
        {
          "lexia": "No one's to blame."
        },
        {
          "lexia": "We all broke the mirror."
        },
        {
          "lexia": "The mirror broke itself"
        },
        {
          "lexia": "Miss Nobody broke the mirror"
        }
      ]
    }
  ],
  "goTo": [
    [
      "sc16"
    ]
  ]
}
```

## Another example from [[YAML Cheatsheet]]

### this yaml

```yaml
## YAML sequences, hashes (objects), & multiline strings

array:
  - 132
  - 2.434
  - 'abc'

my_list_of_lists:
  - [1, 2, 3]
  - [4, 5, 6]

my_hash:
  subkey:
    subsubkey1: 5
    subsubkey2: 6
  another:
    somethingelse: 'Important!'

my_hash_with_json: {nr1: 5, nr2: 6}

content_1:
    Arbitrary free text
    over multiple lines stopping only
    after the indentation changes...

content_2: >
  Arbitrary free text
  over "multiple lines" stopping
  after indentation changes...
```

### converts to this json

```json
{
  "array": [
    132,
    2.434,
    "abc"
  ],
  "my_list_of_lists": [
    [
      1,
      2,
      3
    ],
    [
      4,
      5,
      6
    ]
  ],
  "my_hash": {
    "subkey": {
      "subsubkey1": 5,
      "subsubkey2": 6
    },
    "another": {
      "somethingelse": "Important!"
    }
  },
  "my_hash_with_json": {
    "nr1": 5,
    "nr2": 6
  },
  "content_1": "Arbitrary free text over multiple lines stopping only after the indentation changes...",
  "content_2": "Arbitrary free text over \"multiple lines\" stopping after indentation changes...\n"
}
```

