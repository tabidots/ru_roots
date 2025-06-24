# Russian word roots

This repository contains data from Kuznetsova's *Dictionary of Morphemes of the Russian Language* (Кузнецова А.И., *Словарь морфем русского языка*, 1986).

The data was OCRed from a PDF using Tesseract. I've gone through and corrected all the OCR errors as well as a few stray typos that were present in the actual dictionary itself. I've re-added stress marks to most of the words that had stress marks in the original.

The data has been checked for internal consistency quite meticulously, as I am cross-referencing it against another morphological dataset for use in a dictionary project. 

I've also reformatted homographic roots using superscript notation (`вод¹`, `вод²`) instead of Kuznetsova's notation (`1 вод`, `2 вод`), because that gets a little confusing when there are multiple roots written together.

By combining the data in these two files, it is possible to find однокоренные слова. However, it should be noted that from the persepctive of the modern language, there will be many false positives (see the next section for an explanation why).

# Important notes

The *Dictionary of Morphemes* is a collection of what are called **diachronic** analyses of words. This means that the roots given for each word are as short and etymologically deep as possible. 

To give an example, *около*, *колесо*, and *кольцо* are all tagged with the root `кол²`, because they ultimately relate to the idea of "roundness," even though a **synchronic** analysis (based on the modern language) would show that these words have become quite semantically distinct with their own families of roots:

```
около: около, окольн-
колесо: -колес-, -коляс-, -колёс-
кольцо: -кольц-, -кольч-, -колеч-
```

Synchronic analyses can be found in resources by Tikhonov and others, but this data is often very messy and contains many inconsistencies.

# Data format

## `lemmas_to_roots.tsv`

`lemmas_to_roots.tsv` is data from the Index (Указатель). It contains two columns. 

```
Word (optional notes)    Root
---------------------    ----
ложиться                 лож¹
ложка                    ложк
ложкарный                ложк
ложкарь                  ложк
ложность                 лож²
ложный                   лож²
ложок                    лож¹
ложчатый                 ложч
ложь                     лож²
```
Some words have stress marks for disambiguation:

```
Word (optional notes)    Root
---------------------    ----
ужи́н                     жин
у́жин                     ужин
ужина́ть                  жин
у́жинать                  ужин
```
Notes, if present, are included in parentheses or square brackets following the word in the first column. These are usually given in cases where stress alone is not sufficient to distinguish the sense of the word. 

```
Word (optional notes)                           Root
---------------------                           ----
полка (предмет мебели или часть его)            пол¹
полка (прополка)                                пол⁴
полка (уменьш. к пола)                          пол⁵
...
половой [1 слуга; 2 от пол (настил)]            пол¹
половой [от пол (о живых существах)]            пол⁵
...
просып                                          сып²
просы́пать                                       сып¹
просыпа́ть (высыпать нечаянно)                   сып¹
просыпа́ть (о сне)                               сып²
просы́паться                                     сып¹
просыпа́ться (высыпаться о чем-нибудь сыпучем)   сып¹
просыпа́ться (о сне)                             сып²
```
In order to keep the files as simple as possible, the italic formatting used to distinguish the mention of a word from its normal usage was not preserved (see [Use-mention distinction](https://en.wikipedia.org/wiki/Use–mention_distinction)). This is easy to spot, though (prepositions *к* or *от* followed by something other than a noun in the appropriate case).

## `root_groups.txt`

`root_groups.txt` is data from Appendix 1 (Приложение I).

This is a dual-purpose reference. However, even though it contains two distinct kinds of data, I have chosen not to separate them, for simplicity's sake.

Lines that contain the character ` → ` are "redirects" to a canonical root. Lines that do not contain this character consist of a single root *or* multiple roots separated by slashes.

It's simpler than it sounds. Here's an excerpt from the file to illustrate:

```
...
бер/бир/бор¹/бр¹
бёрд
берег¹/береж¹/береч/брег/бреж²/бреч
берег²/береж²/бреж¹
беред
береж¹ → берег¹
береж² → берег²
берез/берёз
берёз → берез
...
```