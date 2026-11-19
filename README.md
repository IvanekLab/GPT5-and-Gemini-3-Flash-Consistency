# GPT-5 and Gemini 3 Flash Consistency

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24374226.svg)](https://doi.org/10.5281/zenodo.24374226)

*"Semantic repeatability and reproducibility of GPT-5 and Gemini 3 Flash on H5N1 One Health questions"* (Dalla Pria, Nelson, & Ivanek, 2026).

This repository contains the four Jupyter notebooks used to collect LLM responses from GPT-5 and Gemini 3 Flash and to compute the semantic repeatability, reproducibility, and inter-embedding-agreement statistics reported in the paper.

---

## Citation

If you use this code, please cite the paper:

> Dalla Pria, L., Nelson, A. L., & Ivanek, R. (2026). Semantic repeatability and reproducibility of GPT-5 and Gemini 3 Flash on H5N1 One Health questions. Submitted to PLOS Digital Health.

BibTeX:

```bibtex
@article{dallapria2026consistency,
  author  = {Dalla Pria, Luizza and Nelson, Amelia L. and Ivanek, Renata},
  title   = {Semantic repeatability and reproducibility of GPT-5 and Gemini 3 Flash on H5N1 One Health questions},
  journal = {PLOS Digital Health},
  year    = {2026},
  note    = {TODO: volume, issue, pages, DOI}
}
```
The code is also archived on Zenodo (DOI: [10.5281/zenodo.24374226](https://doi.org/10.5281/zenodo.24374226)).
---

## What this repository contains

Four Jupyter notebooks under `notebooks/`:

| Notebook | Paper section |
|---|---|
| `GPT5_Repeatability_Collection_github.ipynb` | §2.3 (GPT-5, 450 responses) |
| `GPT5_Reproducibility_Collection_github.ipynb` | §2.3 (GPT-5, 2,250 responses) |
| `Gemini_3_Flash_Collection_github.ipynb` | §2.3 (Gemini 3 Flash, both metrics, 2,700 responses) |
| `Repeat_Repro_Analysis_v2_centroid_github.ipynb` | §2.4–2.6 + all Results tables and figures |

---

## What this repository does NOT contain (and why)

- **The prompt corpus** (15 base questions + 75 CoT variants) — withheld to protect the privacy of Reddit community contributors, per the paper's Methods §2.2.
- **The raw LLM responses** (5,400 total: 2,700 per model) — withheld per OpenAI and Google API Terms of Service, which restrict redistribution of model outputs.
- **Intermediate embedding caches and per-prompt score CSVs** — regenerable from the notebooks given the inputs above; omitted to keep the repository small.

Qualified researchers may contact the corresponding author (<ln326@cornell.edu>) to request access to the prompt corpus and/or raw responses under a data-use agreement that specifies responsible use.

---

## Reproduction steps

1. **Clone the repository.**
   ```bash
   git clone https://github.com/IvanekLab/GPT5-and-Gemini-3-Flash-Consistency.git
   cd GPT5-and-Gemini-3-Flash-Consistency
   ```

2. **Install dependencies** (Python 3.11.3 recommended):
   ```bash
   pip install -r requirements.txt
   ```

3. **Set your API keys.** Copy the template and fill in the two keys:
   ```bash
   cp .env.example .env
   # then edit .env with your OPENAI_API_KEY and GOOGLE_API_KEY
   ```

4. **Update the `PROJECT_DIR` line** near the top of each notebook to point to your local copy of the repository.

5. **Place the prompt CSVs** (obtained from the corresponding author under a data-use agreement, as described above) in `PROJECT_DIR/Prompts_to_GPT/`.

6. **Run the notebooks in order:**
   - The two GPT-5 collection notebooks (repeatability + reproducibility)
   - The Gemini 3 Flash collection notebook
   - The analysis notebook (produces all tables and figures in the paper)

---

## Dependencies

See `requirements.txt`. The core stack is Python 3.11.3, `openai` + `google-genai` for data collection, `sentence-transformers` + OpenAI embeddings for the vector representations, and `scipy` + `pingouin` + `statsmodels` for the statistical tests.

---

## License

This project is licensed under the Apache License 2.0 — see the `LICENSE` file for the full text.

---

## Authors and affiliations

- **Luizza Dalla Pria** — College of Professional Studies, Northeastern University, Boston, MA; Department of Population Medicine and Diagnostic Sciences, College of Veterinary Medicine, Cornell University, Ithaca, NY. ✉ <ln326@cornell.edu> (corresponding author)
- **Amelia L. Nelson** — Department of Population Medicine and Diagnostic Sciences, College of Veterinary Medicine, Cornell University, Ithaca, NY.
- **Renata Ivanek** — Department of Population Medicine and Diagnostic Sciences, College of Veterinary Medicine, Cornell University, Ithaca, NY.

---

## Acknowledgments

We thank Shyr et al. (2025) for the semantic consistency framework we adapted and extended, and Savage et al. (2024) for the Chain-of-Thought reasoning taxonomy used in the reproducibility analysis.
