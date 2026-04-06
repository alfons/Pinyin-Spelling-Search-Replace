# Pinyin-Spelling-Search-Replace
A simple pre-processing tool for correcting common spelling errors in Hànyǔ Pīnyīn via plain-text replacements.

# Overview

This tool performs simple plain-text replacements without grammatical analysis. It may be used to correct common spelling issues in podcast subtitle transcripts written in Hànyǔ Pīnyīn, such as those from Mandarin Corner. It is intended as a convenient pre-processing step before reviewing the text sentence by sentence.

The primary norm used is *National Standards of the People's Republic of China, GB/T 16159-2012* (中华人民共和国国家标准); Yīn Bǐnyōng’s Chinese Romanization Pronunciation and Orthography is used as interpretive fallback.

# Interface Overview

- **Replacement Rules**  
  Editable list of search-and-replace rules used during processing. Two columns separated by a semicolon, whitespace sensitive.

- **Input Text**  
  Tone-marked Pīnyīn content to be processed.

- **Output Text**  
  Processed result after applying all replacement rules. Processing is done twice per rule, one as is, and one with initial capital letter.

- **Final Changes Log**  
  Displays a line-by-line diff `- original`, `+ processed`.

# Examples of replacements and problems

## Basic correction

```
去过
- qù guo
+ qùguo
```

Processed the Replacement Rule "` guo;guo`", which follows the spelling rule 6.1.2.1 of GB/T 16159-2012, "Verbs and the aspect particles “着 (zhe)”, “过 (guo)” and in some cases “了 (le)” are written together."

## Limitations: No validation and correction of incorrect romanisation/transcription

Legend: `→ after manual correction`

### Wrong spelling of diacritics

```
其实我做过挺多工作的。
- Qíshí wǒ zuò guò tǐng duō gōngzuò de.
→ Qíshí wǒ zuòguo tǐng duō gōngzuò de.
```

Here, *guò* has been incorrectly tone-marked in the given input text, when it should have been transcribed as neutral-tone *guo*. This requires manual correction.

### Wrong compound forming

```
那今天呢我们就请来了一位外汉语教学
- Nà jīntiān ne wǒmen jiù qǐng lái le yī wèi Hànyǔ jiàoxué
+ Nà jīntiān ne wǒmen jiù qǐng láile yī wèi Hànyǔ jiàoxué
→ Nà jīntiān ne wǒmen jiù qǐngláile yī wèi Hànyǔ jiàoxué
```

Processed the Replacement Rule *` le;le`*. However, *qǐnglái* should be written as a compound verb. This requires manual correction.

Note: when `le` is a sentence-final, it becomes *qǐnglái le* rather than *qǐngláile*.

## Multi-error transcription

```
因为我觉得中国人就是很习惯性地会给别人泼冷水，对吧？| 对
- Yīnwèi wǒ juédé zhōngguó rén jiùshì hěn xíguàn xìng dì huì gěi biérén pōlěngshuǐ, duì ba?
→ Yīnwèi wǒ juédé Zhōngguórén jiùshì hěn xíguànxìng de huì gěi biérén pōlěngshuǐ, duì ba?
```

In this example, Google Translate made four (4) transcription mistakes in a single sentence. These cannot be resolved with simple replacement rules and require manual correction.
      
Errors include:
- **zhōngguó rén → Zhōngguórén**

  a) The words need to be written together, because rule 5.2, "Disyllabic and trisyllabic structures expressing a single concept are written together."

  b) Zhōngguóren needs to be written with an initial capital letter, because of rule 6.3.3, "If the component of proper nouns is written together with the component of ordinary nouns, the first letter is capitalized."

- **xíguàn xìng → xíguànxìng**
  
  xíguànxìng is a lexicalised adjective (here, adverbial modifier) and should be written as one word, as per rule 5.2

- **地 → de**

  "地" should be transcribed as "de"

---

Have fun with Hànyǔ Pīnyīn. 🚀 Text replacement tool © 2026 by Alfons Grabher, MIT license.
