---
title: Extra fields
weight: 7
---
In some cases the Zotero fields do not offer a place to enter the
data you need to get your references just right. For this Zotero
has a so-called "cheater syntax" which allows you to add extra
"fields" as separate lines in the `extra` field all items in Zotero
have. These fields are supported by the citation processor inside
Zotero, and BBT understands them too, and adds one "cheater syntax
of its own.

You can add such fields by adding each on their own line in the following format:

```
Label: value
```

or the older format you migh have seen, which is supported but considered depracated:

```
{:csl-variable: value}
```

The full list of labels and the Zotero/CSL variables they translate to can be found in the table at the end.

These extra-fields are available to [postscripts](scripting) as `item.extraField.kv.<variable-name>`. Which variable it is depends (sorry):

* when you export to CSL, it is attempted to map it to the corrsponding CSL fields; if none are available, it is available under their *zotero* name
* when you export to Better BibTeX/Better BibLaTeX, it is attempted to map it to the corresponding zotero fields; if none are available, it is available under their *csl variable* name

## BBT-specific

There is also a BBT-specific extra-field format that looks like

```
tex.field: value
```

It is important to note that these BBT-specific fields are not recognized by any other exporter. These fields are simply copied to the output, so if you have

```
tex.bestfield: philosophy
```

you will end up with

```
  bestfield = {philosophy}
```

in the written bib(la)tex.

You can make BBT export the field only for bibtex or biblatex by changing the prefix to `bibtex.` (so `bibtex.bestfield:`) or `biblatex.` respectively. Finally, you can use `=` instead of `:` as a delimiter, and that will indicate to BBT that what follows the `=` is "raw LaTeX"; BBT will not do any escaping and just copy it out unchanged. This means, for example, that you would probably want

```
tex.corp: Black & Decker
tex.formula= $\sum\limits_{i=1}^{n} -p(m_{i})\log_{2}(p(m_{i}))$
```

and not

```
tex.corp= Black & Decker
tex.formula: $\sum\limits_{i=1}^{n} -p(m_{i})\log_{2}(p(m_{i}))$
```

## Label/variable list

{{% extra-fields %}}