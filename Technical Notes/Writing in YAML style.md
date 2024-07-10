---
created: 2024-05-25 17:07
tags:
  - metadata
---
nav links: [[START HERE]], [[YAML + JSON notes]], [[YAML Cheatsheet]], [[Markdown]]

## Writing scenes in YAML style

```
---
#title::
#location::
#description::
#next:: [[sc]]
```
The rationale for this 👆 syntax:
- `#` makes it a **comment** in YAML and a **tag** in Obsidian
- `key::` makes it an **inline field** for Dataview[^1] (see: [Inline Fields - Adding Metadata - Dataview](https://blacksmithgu.github.io/obsidian-dataview/annotation/add-metadata/#inline-fields)) which enables Dataview fields to work in my custom **YAML-in-MD** format
- No closing `---` because the whole file is in my custom **YAML-in-MD** format


[^1]: Dataview is an Obsidian community plugin that adds powerful database-like querying features to an Obsidian vault. For simplicity's sake, I haven't added the plugin to this vault.

