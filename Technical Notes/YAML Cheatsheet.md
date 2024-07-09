---
tags:
  - meta
---
# YAML Cheatsheet

nav links: [[YAML + JSON notes]]
source: http://lzone.de/cheat-sheet/YAML

#### Links to YAML resources

- [YAML 1.2 Spec](http://www.yaml.org/spec/1.2/spec.html)
- [YAML - Wikipedia](https://en.wikipedia.org/wiki/YAML)
- [Online YAML Parser (Python)](http://yaml-online-parser.appspot.com/)
- [online**yaml**tools - yaml to json converter](https://onlineyamltools.com/convert-yaml-to-json)
- [JS-YAML demo. YAML JavaScript parser](http://nodeca.github.io/js-yaml/)
- [YAML Validator](https://jsonformatter.org/yaml-validator)

## YAML Syntax Examples

### YAML Scalars

Scalar types

```yaml
a: 1        # integer
a: 1.234    # float
b: 'abc'    # string
b: "abc"
b: abc
c: false    # boolean type
d: 2015-04-05   # date type
```

Enforcing strings

```yaml
b: !str 2015-04-05
```

### YAML Sequences

#### Simple sequence

```yaml
array:
  - 132
  - 2.434
  - 'abc'
```

#### Sequence of sequences

```yaml
my_list_of_lists:
  - [1, 2, 3]
  - [4, 5, 6]
```

### YAML Hashes

Nested hash

```yaml
my_hash:
  subkey:
    subsubkey1: 5
    subsubkey2: 6
  another:
    somethingelse: 'Important!'
```

Hash with JSON syntax (mixing is possible)

```yaml
my_hash: {nr1: 5, nr2: 6}
```

### YAML HereDoc (multiline strings)

_Block notation_: Newlines become spaces

```yaml
content:
    Arbitrary free text
    over multiple lines stopping only
    after the indentation changes...
```

_Literal style_: Newlines are preserved

```yaml
content: |
    Arbitrary free text
    over "multiple lines" stopping
    after indentation changes...
```

_\+ indicator_: Keep extra newlines after the block

```yaml
content: |+
    Arbitrary free text with newlines after
```

_\- indicator_: remove extra newlines after block

```yaml
content: |-
    Arbitrary free text without newlines after it
```

_folded style_: folded newlines are preserved

```yaml
content: >
  Arbitrary free text
  over "multiple lines" stopping
  after indentation changes...
```

Note that YAML heredocs are the way to escape special characters:

```yaml
# sub key "url" with value 'https://...'
code:
  url: "https://example.com"

# versus key "code" having value 'url: "https://..."'
code: |-
  url: "https://example.com"
```

There is a good online previewer for the different heredoc modes: https://yaml-multiline.info/

### Multiple Documents

A YAML file can have multiple documents, this is why every document needs to start with a "---" line

```yaml
---
content: doc1
---
content: doc2
```

This also means YAML parsers might return multiple documents!

### Content References (Aliases)

```yaml
---
values:
  - &ref Something to reuse
  - *ref      # Literal "Something to reuse" is inserted here!
```

### Merging Keys

Imaging some default properties for a hash like these

```yaml
default_settings:
  install:
    dir: /usr/local
    owner: root
  config:
    enabled: false
```

Use them in another hash using "<<: \*reference"

```yaml
# Derive settings for 'my_app' from default and change install::owner
# and add further setting "group: my_group"

my_app_settings:
  <<: *default_settings
  install:
    owner: my_user
    group: my_group
```

### Complex Mapping

```yaml
---
? - key
:
  - value
```

Note: key and value can be multiple, complex structures that you could not realize with the hash syntax!

## YAML comments syntax

My notes - all of these are valid YAML comments:

```yaml
# this is a comment in a YAML file

#title:: Hayley at home with Frankie
#location:: Hayley-home
#todo:: add sequences & docileBB

```
The latter three ↑ also work as Dataview `field:: value` syntax *and* simultaneously as tags in Obsidian
