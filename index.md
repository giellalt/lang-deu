# German documentation

[![Maturity: Experiment](https://img.shields.io/badge/Maturity-Experiment-black.svg)](https://giellalt.github.io/MaturityClassification.html)
[![License](https://img.shields.io/github/license/giellalt/lang-deu)](https://github.com/giellalt/lang-deu/blob/main/LICENSE)
[![Issues](https://img.shields.io/github/issues/giellalt/lang-deu)](https://github.com/giellalt/lang-deu/issues)
[![Build Status](https://divvun-tc.thetc.se/api/github/v1/repository/giellalt/lang-deu/main/badge.svg)](https://github.com/giellalt/lang-deu/actions)

This page documents the work on the **German language model**. 

# Project documentation

* (Add links to project specific documentation here as needed. Keep the documentation in the `docs/` directory.)

# In-source documentation

Below is an autogenerated list of documentation pages built from structured comments in the source code. All pages are also concatenated and can be read as one long text [here](deu.md).

* `src/`
    * `cg3/`
        * [functions.cg3](src-cg3-functions.cg3.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/cg3/functions.cg3))
    * `fst/`
        * `affixes/`
            * [adjectives.lexc](src-fst-affixes-adjectives.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/affixes/adjectives.lexc))
            * [adverbs.lexc](src-fst-affixes-adverbs.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/affixes/adverbs.lexc))
            * [nouns.lexc](src-fst-affixes-nouns.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/affixes/nouns.lexc))
            * [prepositions.lexc](src-fst-affixes-prepositions.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/affixes/prepositions.lexc))
            * [propernouns.lexc](src-fst-affixes-propernouns.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/affixes/propernouns.lexc))
            * [symbols.lexc](src-fst-affixes-symbols.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/affixes/symbols.lexc))
            * [verbs.lexc](src-fst-affixes-verbs.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/affixes/verbs.lexc))
        * [phonology.twolc](src-fst-phonology.twolc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/phonology.twolc))
        * [root.lexc](src-fst-root.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/root.lexc))
        * `stems/`
            * [abbreviations.lexc](src-fst-stems-abbreviations.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/abbreviations.lexc))
            * [adjectives.lexc](src-fst-stems-adjectives.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/adjectives.lexc))
            * [adverbs.lexc](src-fst-stems-adverbs.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/adverbs.lexc))
            * [exceptions.lexc](src-fst-stems-exceptions.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/exceptions.lexc))
            * [interjections.lexc](src-fst-stems-interjections.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/interjections.lexc))
            * [nouns.lexc](src-fst-stems-nouns.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/nouns.lexc))
            * [numerals.lexc](src-fst-stems-numerals.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/numerals.lexc))
            * [prefixes.lexc](src-fst-stems-prefixes.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/prefixes.lexc))
            * [propernouns.lexc](src-fst-stems-propernouns.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/propernouns.lexc))
            * [verbs.lexc](src-fst-stems-verbs.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/fst/stems/verbs.lexc))
    * `phonetics/`
        * [txt2ipa.xfscript](src-phonetics-txt2ipa.xfscript.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/phonetics/txt2ipa.xfscript))
    * `transcriptions/`
        * [transcriptor-abbrevs2text.lexc](src-transcriptions-transcriptor-abbrevs2text.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/transcriptions/transcriptor-abbrevs2text.lexc))
        * [transcriptor-numbers-digit2text.lexc](src-transcriptions-transcriptor-numbers-digit2text.lexc.html) ([src](https://github.com/giellalt/lang-deu/blob/main/src/transcriptions/transcriptor-numbers-digit2text.lexc))
* `tools/`
    * `grammarcheckers/`
        * [grammarchecker.cg3](tools-grammarcheckers-grammarchecker.cg3.html) ([src](https://github.com/giellalt/lang-deu/blob/main/tools/grammarcheckers/grammarchecker.cg3))
    * `tokenisers/`
        * [tokeniser-disamb-gt-desc.pmscript](tools-tokenisers-tokeniser-disamb-gt-desc.pmscript.html) ([src](https://github.com/giellalt/lang-deu/blob/main/tools/tokenisers/tokeniser-disamb-gt-desc.pmscript))
        * [tokeniser-gramcheck-gt-desc.pmscript](tools-tokenisers-tokeniser-gramcheck-gt-desc.pmscript.html) ([src](https://github.com/giellalt/lang-deu/blob/main/tools/tokenisers/tokeniser-gramcheck-gt-desc.pmscript))