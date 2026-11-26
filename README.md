---
license: cc-by-4.0
pretty_name: Tarot Card Meanings (78 cards, 13 languages)
language: [ru, en, es, pt, de, fr, tr, pl, it, id, uk, ja, he]
task_categories: [text-generation, text-classification, translation]
size_categories: [1K<n<10K]
tags: [tarot, rider-waite-smith, multilingual, divination, culture]
configs:
  - config_name: default
    data_files: cards.jsonl
---

# Tarot Card Meanings: 78 cards, 13 languages

The full Rider–Waite–Smith deck (22 Major Arcana and 56 Minor Arcana) with original, structured interpretations in 13 languages: Russian, English, Spanish, Portuguese, German, French, Turkish, Polish, Italian, Indonesian, Ukrainian, Japanese and Hebrew. 1,014 records (78 cards × 13 languages).

Each record holds, for one card in one language: the card name, suit, number, element or planet correspondence, keywords (upright and reversed), the upright meaning, the reversed meaning, meaning in love, meaning at work, a short piece of advice and the symbolism of the image.

Maintained by [Nightarot](https://nightarot.com), a free online tarot site. The same texts appear on the site's card pages, for example [The Fool](https://nightarot.com/en/cards/the-fool).

Also on Hugging Face: [nightarot/tarot-card-meanings](https://huggingface.co/datasets/nightarot/tarot-card-meanings).

## Files
- `cards.jsonl`: one JSON object per line (recommended).
- `cards.csv`: the same data as UTF-8 CSV with a header row; list fields are joined with `; `.

## Fields
| Field | Meaning |
|---|---|
| `id` | stable English slug, the same for every language (`the-fool`, `ace-of-cups`) |
| `lang` | language code (ISO 639-1) |
| `suit` | `major`, `wands`, `cups`, `swords` or `pentacles` |
| `name_en`, `name` | card name in English and in the record's language |
| `number` | Roman numeral for Major Arcana, rank for Minor Arcana |
| `correspondence` | element, planet or zodiac sign, Golden Dawn / Rider–Waite tradition |
| `keywords_upright`, `keywords_reversed` | short keyword lists |
| `upright`, `reversed` | interpretation upright and reversed |
| `love`, `career` | the card in relationships and at work |
| `advice` | one-sentence practical takeaway |
| `symbols` | what the symbols in the traditional image stand for |

## Use
```python
from datasets import load_dataset
ds = load_dataset("nightarot/tarot-card-meanings", split="train")
fool_de = [r for r in ds if r["id"] == "the-fool" and r["lang"] == "de"][0]
```

## License and attribution
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You may copy, adapt and use the data, including commercially, if you give credit: "Tarot card meanings by Nightarot (https://nightarot.com)", with a link, and say if you changed it.

## Notes and limits
- The interpretations are original texts written for Nightarot. They follow the common Rider–Waite–Smith tradition; tarot has many schools and other readers read the cards differently.
- Corrections are welcome: open an issue or write to hello@nightarot.com.
- The texts are for reflection and entertainment. They are not medical, legal or financial advice and do not predict the future.
