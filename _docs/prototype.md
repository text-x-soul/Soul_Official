---
title: Prototype
permalink: /docs/prototype/
---

`This documentation page` talks about implementation prototypes for the `latest format` and how to implement a `clean` Soul File Format `Parser` and `Reader`.

### `Prototype Structure for Implementation`
All these are just tips on how to implement a clean support for handling soul files. You have the freedom to implement it however you want as long as this project is in public-domain.

**(i)** Provide a `Parser class`

**(ii)** Provide a `Reader class`

**(iii)** Provide a `TypeIdentifier` **array** or **enum**

**(iv)** Provide `Parser` with appropriate matching methods to `identify quantities`, either through `regular expressions` or by `any other method` you want to.

**(v)** Provide a `SoulMap` **enum** or **array** for `identifying types` and returning a `TypeIdentifier` value.

**(vi)** Provide `file reading methods` for `SoulReader`, read `full bytes` first, ignore `comments` by replacing or removing them entirely during stream.

**(vii)** `Iterate` cleaned lines , search for `quantities` with `Parser` and add up to `appropriate maps`.

**(viii)** These are some `preferred options`:

(a) For `variables`: 
- use a string<->string map

(b) For `SOUL_Registers`:
- use a string<->string map

(c) For `Groups`:
- use a string<->list map

(d) For `Group Variables`:
- use a unchangeable-list<->string map

**(ix)** Removing previous `file entries` from `maps` is your `decision`.

**(x)** Provide `enough documentation` of what each of your `personal method` does.
