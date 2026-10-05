# Kaisetsu Corpus Analysis

Corpus-based analysis of Japanese elementary school foreign language curriculum guidelines (*kaisetsu*) across the 2008 and 2017 revisions. Compares terminology, discourse focus, and pedagogical framing between the activity-based (外国語活動) and subject-based (外国語科) documents using computational text analysis.

This project examines whether the shift from activity-based to subject-based foreign language education in Japan's 2017 curriculum reform is visible at the level of policy language. Using corpus and computational methods, it analyzes the terminology and pedagogical framing of three official MEXT curriculum guidelines to trace how form-focused instruction became encoded upstream, before reaching textbooks or classrooms.

## Corpora

| File | Year | Type | Grade |
|------|------|------|-------|
| `kaisetsu_2008_fla.pdf` | 2008 | Activity | 5–6 |
| `kaisetsu_2017_fla.pdf` | 2017 | Activity | 3–4 |
| `kaisetsu_2017_fls.pdf` | 2017 | Subject | 5–6 |

> All PDFs are publicly available MEXT publications and are included in this repository.

## Methods

- **Text extraction** — `pdfplumber`, with manual section tagging (総説 vs. pedagogical)
- **Tokenization** — `SudachiPy` (split mode C), lemma-based, nouns and verbs retained
- **Frequency analysis** — form-related and meaning-related term lists, normalized per 1,000 content words
- **Collocation analysis** — window-based (±3 tokens), bigram-aware for compound terms
- **Keyness analysis** — log-likelihood scoring across corpus pairs

## Setup

```bash
pip install pdfplumber
pip install pandas numpy
pip install matplotlib japanize-matplotlib
pip install sudachipy sudachidict-core
```

Then run the notebook top to bottom. Outputs saved to:
- `kaisetsu_corpus.csv` — tokenized dataframe
- `frequency_results.csv` — term frequency table
- `keyness_results.json` — log-likelihood scores across corpus pairs
- `freq_by_corpus.png` — frequency bar chart

## Notes

SudachiPy splits some compound terms (e.g. 言語活動 → 言語 + 活動). The collocation functions handle this with bigram-aware matching — see the `get_collocates_universal` function.

## Related Publication

This repository supports the following preprint:

DiSorbo, A. (2026). Natural Language Processing Analysis of Form-Focused Specification in MEXT Kaisetsu Documents. *EdArXiv*. https://osf.io/preprints/edarxiv/24sz9_v1

## Author
Anthony DiSorbo — Data Analyst, Greater Tokyo
[LinkedIn](https://www.linkedin.com/in/adisorbo/) · [GitHub](https://github.com/adisorbo)
