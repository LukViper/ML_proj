# Dataset Download Links — Factual / Non-Factual Literature Review (20 Papers)

This file lists **official and commonly used mirror links** to download the datasets referenced in the 20-paper literature review. Links are grouped by paper number and assignee folder.

**Last updated:** August 2026  
**Note:** Some datasets require registration, agreement forms, or are not fully public. Check each entry before use.

---

## Quick index

| # | Dataset | Primary download | Folder |
|---|---------|------------------|--------|
| 1 | FEVER | https://fever.ai/dataset/fever.html | Shasank |
| 2 | LIAR | https://www.cs.ucsb.edu/~william/data/liar_dataset.zip | Shasank |
| 3 | MultiFC | https://github.com/casperhansen/fake-news-reasoning | Shasank |
| 4 | FEVEROUS | https://fever.ai/dataset/feverous.html | Shasank |
| 5 | CFEVER | https://github.com/IKMLab/CFEVER-data | Shasank |
| 6 | Monti Twitter propagation | Not publicly released (see note) | Shasank |
| 7 | FANG | https://github.com/nguyenvanhoang7398/FANG | Shasank |
| 8 | X-FACT | https://github.com/utahnlp/x-fact | Shasank |
| 9 | SciFact | https://scifact.s3-us-west-2.amazonaws.com/release/latest/data.tar.gz | HarshaVardhan |
| 10 | HoVer | https://github.com/hover-nlp/hover | HarshaVardhan |
| 11/18 | AVeriTeC | https://fever.ai/dataset/averitec.html | HarshaVardhan / Ruthvika |
| 12 | CLIMATE-FEVER | https://github.com/tdiggelm/climate-fever-dataset | HarshaVardhan |
| 13 | AVeriTeC ST 2024 (Knowledge Store) | https://fever.ai/dataset/averitec.html | HarshaVardhan |
| 14 | AVeriTeC ST 2025 (Knowledge Store) | https://fever.ai/dataset/averitec.html | HarshaVardhan |
| 15 | Misbar (+ AVeriTeC) | https://doi.org/10.1016/j.ins.2025.122868 | HarshaVardhan |
| 16 | CheckThat! 2021 (CT-FAN-21) | https://zenodo.org/records/4714517 | Ruthvika |
| 17 | Murayama survey (118 datasets) | https://arxiv.org/abs/2111.03299 | Ruthvika |
| 19 | Papers With Code hub | https://paperswithcode.com/task/fact-checking | Ruthvika |
| 20 | fever.ai AVeriTeC hub | https://fever.ai/dataset/averitec.html | Ruthvika |

---

## Shasank — Papers 1–8

### Paper 1 — FEVER (185,445 claims)

| Resource | Link |
|----------|------|
| **Official dataset page** | https://fever.ai/dataset/fever.html |
| **Dataset viewer** | https://fever.ai/dataset/fever.html (View the dataset) |
| **Direct download base** | https://fever.ai/download/fever/ |
| Train split | https://fever.ai/download/fever/train.jsonl |
| Shared task dev (labeled) | https://fever.ai/download/fever/shared_task_dev.jsonl |
| Shared task dev (public/unlabeled) | https://fever.ai/download/fever/shared_task_dev_public.jsonl |
| Shared task test (unlabeled) | https://fever.ai/download/fever/shared_task_test.jsonl |
| Paper dev | https://fever.ai/download/fever/paper_dev.jsonl |
| Paper test | https://fever.ai/download/fever/paper_test.jsonl |
| Wikipedia pages corpus | https://fever.ai/download/fever/wiki-pages.zip |
| **Hugging Face** | https://huggingface.co/datasets/fever/fever |
| **GitHub (code + baselines)** | https://github.com/awslabs/fever |
| **Baseline experiments** | https://github.com/sheffieldnlp/fever-baselines |
| **Scorer** | https://github.com/sheffieldnlp/fever-scorer |
| **Paper** | https://aclanthology.org/N18-1074/ |

**License:** Check fever.ai terms.  
**Format:** JSONL (`id`, `label`, `claim`, `evidence`).

---

### Paper 2 — LIAR (12,836 PolitiFact statements)

| Resource | Link |
|----------|------|
| **Official ZIP download** | https://www.cs.ucsb.edu/~william/data/liar_dataset.zip |
| **Hugging Face mirror** | https://huggingface.co/datasets/ucsbai/liar |
| **GitHub mirror / docs** | https://github.com/tfs4/liar_dataset |
| **PolitiFact API (full verdict reports)** | https://www.politifact.com/api/v/2/statement/[ID]/?format=json |
| **PolitiFact API docs** | http://static.politifact.com/api/v2apidoc.html |
| **Paper** | https://aclanthology.org/P17-2067/ |

**License:** Research use; PolitiFact content has its own terms.  
**Format:** TSV files (`train.tsv`, `valid.tsv`, `test.tsv`) + metadata columns.

---

### Paper 3 — MultiFC (~34,918 claims, 26 fact-check sites)

| Resource | Link |
|----------|------|
| **Paper / project page** | https://copenlu.github.io/publication/2019_emnlp_augenstein/ |
| **GitHub (MultiFC public data zip)** | https://github.com/casperhansen/fake-news-reasoning |
| **Direct file name** | `multi_fc_publicdata.zip` (inside repo / releases) |
| **Hugging Face mirror** | https://huggingface.co/datasets/pszemraj/multi_fc |
| **CodaLab competition (legacy)** | https://competitions.codalab.org/competitions/21163 |
| **Paper** | https://aclanthology.org/D19-1475/ |
| **arXiv** | https://arxiv.org/abs/1909.03242 |

**License:** Check original paper / repository.  
**Format:** JSON/TSV with claim, metadata, evidence pages, labels.

---

### Paper 4 — FEVEROUS (87,026 claims; text + tables)

| Resource | Link |
|----------|------|
| **Official dataset page** | https://fever.ai/dataset/feverous.html |
| **Dataset viewer** | https://fever.ai/dataset/feverous.html |
| **Zenodo archive (DOI)** | https://doi.org/10.5281/zenodo.4911508 |
| **Zenodo record** | https://zenodo.org/records/4911508 |
| **GitHub (code + download script)** | https://github.com/Raldir/FEVEROUS |
| **Shared task overview** | https://aclanthology.org/2021.fever-1.1.pdf |
| **Paper** | https://arxiv.org/abs/2106.05707 |

**Includes:** Training data, development data, Wikipedia sqlite DB (`feverous-wiki-pages-db.zip`, ~20 GB).  
**Format:** JSONL with structured evidence (sentences, table cells, lists).

---

### Paper 5 — CFEVER (30,012 Chinese claims)

| Resource | Link |
|----------|------|
| **Project homepage** | https://ikmlab.github.io/CFEVER/ |
| **GitHub (dataset download)** | https://github.com/IKMLab/CFEVER-data |
| **Baselines code** | https://github.com/IKMLab/CFEVER-baselines |
| **Paper (AAAI 2024)** | https://arxiv.org/abs/2402.13025 |
| **AAAI page** | https://ojs.aaai.org/index.php/AAAI/article/view/29825 |

**Note:** Test labels are not public; submit predictions via GitHub instructions.  
**Format:** FEVER-style JSON with Chinese Wikipedia evidence.

---

### Paper 6 — Monti et al. Twitter propagation dataset

| Resource | Link |
|----------|------|
| **Paper** | https://arxiv.org/abs/1902.06673 |
| **Public dataset download** | **Not publicly released** by authors (Fabula AI proprietary crawl) |

**Alternatives for similar social-propagation research:**

| Alternative | Link |
|-------------|------|
| FakeNewsNet | https://github.com/KaiDM19/FakeNewsNet |
| Twitter15 / Twitter16 | https://github.com/majingCUHK/Rumor_RvNN |
| Weibo rumor datasets | Various academic mirrors |

**Note:** Paper 6 dataset (~1,084 labeled claims, Twitter cascades) was built in-house; use FakeNewsNet or FANG (Paper 7) for reproducible graph-based experiments.

---

### Paper 7 — FANG (social-context fake news graph)

| Resource | Link |
|----------|------|
| **GitHub (code + processed data)** | https://github.com/nguyenvanhoang7398/FANG |
| **Helper repo (stance models)** | https://github.com/nguyenvanhoang7398/FANG-helper |
| **Processed graph data** | `data/news_graph/` inside repo |
| **Raw CSV files** | `data/fang_fake.csv`, `data/fang_real.csv` |
| **Paper (CIKM 2020)** | https://arxiv.org/abs/2008.07939 |
| **ACM** | https://dl.acm.org/doi/10.1145/3340531.3412046 |

**Related (FakeNewsNet-style social data):** https://github.com/KaiDM19/FakeNewsNet

---

### Paper 8 — X-FACT (31,189 multilingual claims, 25 languages)

| Resource | Link |
|----------|------|
| **GitHub (official code + data)** | https://github.com/utahnlp/x-fact |
| **Hugging Face mirror** | https://huggingface.co/datasets/utahnlp/x-fact |
| **Paper** | https://arxiv.org/abs/2106.09248 |
| **Fact Check Explorer (source)** | https://toolbox.google.com/factcheck/explorer |

**Format:** JSON with claims, labels, metadata, search snippets; splits α1/α2/α3 for OOD and zero-shot.

---

## HarshaVardhan — Papers 9–15

### Paper 9 — SciFact (1,409 scientific claims)

| Resource | Link |
|----------|------|
| **Direct dataset tarball** | https://scifact.s3-us-west-2.amazonaws.com/release/latest/data.tar.gz |
| **Claims with citances** | https://scifact.s3-us-west-2.amazonaws.com/release/latest/claims_with_citances.jsonl |
| **GitHub (code + download scripts)** | https://github.com/allenai/scifact |
| **Leaderboard / test eval** | https://leaderboard.allenai.org/scifact |
| **Paper** | https://aclanthology.org/2020.emnlp-main.609/ |
| **arXiv** | https://arxiv.org/abs/2004.14974 |

**Contains:** `claims_train.jsonl`, `claims_dev.jsonl`, `claims_test.jsonl`, `corpus.jsonl`.

**Download command:**
```bash
wget https://scifact.s3-us-west-2.amazonaws.com/release/latest/data.tar.gz
tar -xzf data.tar.gz
```

---

### Paper 10 — HoVer (26,171 multi-hop claims)

| Resource | Link |
|----------|------|
| **Project homepage** | https://hover-nlp.github.io/ |
| **GitHub (code + download script)** | https://github.com/hover-nlp/hover |
| **Baseline model code** | https://github.com/hover-nlp/hover |
| **Wikipedia corpus (HotpotQA)** | Use HotpotQA Wikipedia dump (see HoVer README) |
| **Test evaluation** | Email predictions to hover.nlp.dataset@gmail.com |
| **Paper** | https://aclanthology.org/2020.findings-emnlp.309/ |

**License:** CC BY-SA 4.0  
**Note:** Clone repo and run provided download script for train/dev/test splits.

---

### Papers 11 & 18 — AVeriTeC (4,568 real-world claims)

| Resource | Link |
|----------|------|
| **Official dataset page** | https://fever.ai/dataset/averitec.html |
| **Dataset viewer** | https://fever.ai/dataset/averitec.html |
| **GitHub (baseline + data)** | https://github.com/MichSchli/AVeriTeC |
| **Hugging Face (baseline + Knowledge Store)** | https://huggingface.co/chenxwh/AVeriTeC |
| **Paper (NeurIPS 2023)** | https://arxiv.org/abs/2305.13117 |
| **OpenReview** | https://openreview.net/forum?id=fKzSz0oyaI |

**Downloads on fever.ai:**
- Training dataset
- Development dataset
- Evidence collection (FEVER 7 / FEVER 8 Knowledge Store)
- Blind test sets + evaluation scripts

**License:** CC BY-NC 4.0

---

### Paper 12 — CLIMATE-FEVER (1,535 climate claims)

| Resource | Link |
|----------|------|
| **Project homepage** | http://climatefever.ai |
| **GitHub (dataset)** | https://github.com/tdiggelm/climate-fever-dataset |
| **GitHub releases** | https://github.com/tdiggelm/climate-fever-dataset/releases |
| **Hugging Face** | https://huggingface.co/datasets/climate_fever |
| **Paper** | https://arxiv.org/abs/2012.00614 |

**Contains:** 1,535 claims + 7,675 claim–evidence pairs; macro labels include DISPUTED.

---

### Paper 13 — AVeriTeC Shared Task 2024 (FEVER 7)

| Resource | Link |
|----------|------|
| **Shared task page / downloads** | https://fever.ai/dataset/averitec.html |
| **Knowledge Store (FEVER 7)** | https://fever.ai/dataset/averitec.html → Evidence Collection (Fever 7) |
| **Blind test set (FEVER 7)** | https://fever.ai/dataset/averitec.html |
| **Evaluation script** | https://fever.ai/dataset/averitec.html |
| **Hugging Face repo** | https://huggingface.co/chenxwh/AVeriTeC |
| **Shared task paper** | https://aclanthology.org/2024.fever-1.1/ |

**New test set:** +1,215 claims (temporal extension beyond original AVeriTeC test).

---

### Paper 14 — 2nd AVeriTeC Shared Task 2025 (FEVER 8)

| Resource | Link |
|----------|------|
| **Shared task page / downloads** | https://fever.ai/dataset/averitec.html |
| **Knowledge Store (FEVER 8)** | https://fever.ai/dataset/averitec.html → Evidence Collection (Fever 8) |
| **Blind test set (FEVER 8)** | https://fever.ai/dataset/averitec.html |
| **Evaluation script** | https://fever.ai/dataset/averitec.html |
| **Shared task paper** | https://aclanthology.org/2025.fever-1.15/ |

**New test set:** 1,000 claims from Jan–Dec 2024; larger Knowledge Store (~1M URLs).

---

### Paper 15 — Misbar + AVeriTeC (Hou et al., Information Sciences 2025)

| Resource | Link |
|----------|------|
| **Paper (open access)** | https://doi.org/10.1016/j.ins.2025.122868 |
| **ScienceDirect** | https://www.sciencedirect.com/science/article/pii/S0020025525010047 |
| **Misbar dataset** | **Contact authors** — not yet found on a public hub at time of writing |
| **Related benchmark used in paper** | https://fever.ai/dataset/averitec.html (AVeriTeC) |

**Authors:** Ziwei Hou, Bahadorreza Ofoghi, John Yearwood (Deakin University)  
**Action:** Download paper from DOI; request Misbar dataset from corresponding author if not linked in supplementary materials.

---

## Ruthvika — Papers 16–20

### Paper 16 — CheckThat! 2021 Task 3 / CT-FAN-21 (NoFake BERT paper)

| Resource | Link |
|----------|------|
| **Zenodo record (CT-FAN-21 corpus)** | https://zenodo.org/records/4714517 |
| **CheckThat! 2021 lab page** | https://sites.google.com/view/clef2021-checkthat/home |
| **Task 3 page** | https://sites.google.com/view/clef2021-checkthat/tasks/task-3-fake-news-detection |
| **GitLab (scripts + data)** | https://gitlab.com/checkthat_lab/clef2021-checkthat-lab/-/tree/master/task3 |
| **Task 3 overview paper** | http://ceur-ws.org/Vol-2936/paper-30.pdf |
| **NoFake system paper** | https://arxiv.org/abs/2108.05419 |

**Access note:** Zenodo may require a **Data Sharing Agreement** — download agreement form from Zenodo and email signed copy to **fakenewstask@gmail.com**.

**Labels:**
- Task 3A: False, Partially False, True, Other
- Task 3B: Health, Election, Crime, Climate, Economy, Education

---

### Paper 17 — Murayama survey (118 datasets catalog)

| Resource | Link |
|----------|------|
| **Survey paper** | https://arxiv.org/abs/2111.03299 |
| **ACM (published version)** | Search "Dataset of Fake News Detection and Fact Verification: A Survey" |

This paper is a **meta-resource** — it links to many datasets. Commonly cited datasets from the survey include:

| Dataset | Typical download |
|---------|------------------|
| FEVER | https://fever.ai/dataset/fever.html |
| LIAR | https://www.cs.ucsb.edu/~william/data/liar_dataset.zip |
| MultiFC | https://github.com/casperhansen/fake-news-reasoning |
| FakeNewsNet | https://github.com/KaiDM19/FakeNewsNet |
| BuzzFeed | Various mirrors on GitHub |
| PHEME | https://figshare.com/articles/dataset/PHEME/4010619 |
| ISOT | https://www.uvic.ca/engineering/ece/isot/datasets/ |
| Snopes | Via MultiFC / fact-check crawls |

---

### Paper 18 — AVeriTeC Benchmark (same as Paper 11)

See **Papers 11 & 18** section above.  
**PDF in Ruthvika folder:** `18_AVeriTeC_Benchmark_NeurIPS_2023.pdf`

---

### Paper 19 — Papers With Code: Fact Checking task hub

| Resource | Link |
|----------|------|
| **Task page** | https://paperswithcode.com/task/fact-checking |
| **Archived snapshot (local)** | `Ruthvika/19_Papers_With_Code_Fact_Checking_Benchmark.html` |

**Note:** Papers With Code was archived/sunset around mid-2025. Use for historical SOTA and code links; verify current scores against primary sources.

**Related live hubs:**

| Hub | Link |
|-----|------|
| fever.ai | https://fever.ai |
| Allen AI SciFact leaderboard | https://leaderboard.allenai.org/scifact |
| Hugging Face datasets search | https://huggingface.co/datasets?search=fact+checking |

---

### Paper 20 — Official AVeriTeC project (fever.ai)

| Resource | Link |
|----------|------|
| **AVeriTeC dataset page** | https://fever.ai/dataset/averitec.html |
| **FEVER project home** | https://fever.ai |
| **All datasets index** | https://fever.ai (Datasets menu) |
| **Local HTML snapshot** | `Ruthvika/20_Official_AVeriTeC_Dataset_Project.html` |

**Also available on fever.ai:**
- FEVER → https://fever.ai/dataset/fever.html
- FEVEROUS → https://fever.ai/dataset/feverous.html
- Shared tasks / workshops → https://fever.ai

---

## Bulk download commands (common datasets)

```bash
# FEVER
wget https://fever.ai/download/fever/train.jsonl
wget https://fever.ai/download/fever/shared_task_dev.jsonl
wget https://fever.ai/download/fever/wiki-pages.zip

# LIAR
wget https://www.cs.ucsb.edu/~william/data/liar_dataset.zip

# SciFact
wget https://scifact.s3-us-west-2.amazonaws.com/release/latest/data.tar.gz

# Clone repos with data
git clone https://github.com/IKMLab/CFEVER-data.git
git clone https://github.com/utahnlp/x-fact.git
git clone https://github.com/tdiggelm/climate-fever-dataset.git
git clone https://github.com/hover-nlp/hover.git
git clone https://github.com/MichSchli/AVeriTeC.git
git clone https://github.com/nguyenvanhoang7398/FANG.git
git clone https://github.com/casperhansen/fake-news-reasoning.git

# Hugging Face (requires: pip install datasets)
python -c "from datasets import load_dataset; load_dataset('fever/fever')"
python -c "from datasets import load_dataset; load_dataset('ucsbai/liar')"
python -c "from datasets import load_dataset; load_dataset('pszemraj/multi_fc')"
python -c "from datasets import load_dataset; load_dataset('climate_fever')"
python -c "from datasets import load_dataset; load_dataset('utahnlp/x-fact')"
```

---

## Access restrictions summary

| Dataset | Restriction |
|---------|-------------|
| LIAR | Research use; PolitiFact API rate limits |
| MultiFC | Check repo license |
| Monti Twitter dataset | **Not public** |
| AVeriTeC | CC BY-NC 4.0; some test splits via shared task only |
| CheckThat! CT-FAN-21 | Data Sharing Agreement required (Zenodo) |
| Misbar (Paper 15) | Request from authors |
| FEVEROUS Wikipedia DB | Large download (~20 GB) |
| FEVER wiki-pages | Large download (~1.7 GB compressed) |

---

## Folder locations (local copies)

| Folder | Papers | Local PDFs |
|--------|--------|------------|
| `Shasank/` | 1–8 | 8 PDFs |
| `HarshaVardhan/` | 9–15 | 6 PDFs + Paper 15 source link |
| `Ruthvika/` | 16–20 | 3 PDFs + 2 HTML pages + notes |
| `Papers_for_literature_review/` | — | `DOWNLOAD_SUMMARY.txt` only (papers moved) |

---

## Related literature review files

| File | Description |
|------|-------------|
| `Literature_Review_Factual_NonFactual_Information.md` | Full 20-paper review |
| `Shasank/Literature_Survey_Shasank_Papers_1-8.md` | Shasank survey |
| `HarshaVardhan/Literature_Survey_HarshaVardhan_Papers_9-15.md` | HarshaVardhan survey |
| `Ruthvika/Literature_Survey_Ruthvika_Papers_16-20.md` | Ruthvika survey |
