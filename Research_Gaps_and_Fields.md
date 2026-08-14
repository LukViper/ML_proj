# Research Gaps and Possible Directions

**Factual vs Non-Factual Information Detection**

This note is based on the literature review of 20 papers/resources (`Literature_Review_Factual_NonFactual_Information.md`). It is not a full survey. It is more like a list of places the field still looks incomplete, and project ideas that could come out of that.

After reading the papers, the area does not feel like one single problem. It has split into a few tracks that do not talk to each other much:

- **Synthetic Wikipedia claims** (FEVER and related datasets) — large, clean, easier for pipelines
- **Real fact-checked claims** (LIAR, MultiFC, X-FACT, AVeriTeC) — smaller, messy, models struggle
- **Social-graph fake news** (Monti et al., FANG) — uses how news spreads, almost never combined with the NLP verification work

The one point that keeps coming up: **finding the right evidence is harder than classifying the claim after you already have the evidence.**

---

## 1. Retrieval is still the main bottleneck

This is not just a feeling. The numbers are pretty consistent:

| Dataset | What happens | Score |
|---------|----------------|-------|
| FEVER | Correct evidence + label | 31.87% |
| FEVER | Label only (ignore evidence) | 50.91% |
| HoVer | Full pipeline vs humans | 14.9% vs ~81% |
| HoVer | Evidence recall, 2-hop → 4-hop | ~80% → ~15% |
| FEVEROUS | Correct evidence + verdict | ~18% |
| AVeriTeC | Auto evidence / auto veracity / gold-evidence veracity | 0.21 / 0.15 / 0.49 |

If the project is not supposed to be “fine-tune another BERT”, the middle of the pipeline is the better place to work.

**Possible directions**
- Dense vs sparse vs hybrid retrieval, but for fact checking, not generic search
- Multi-hop retrieval that does not collapse after 2 hops
- Question generation as the way you search (AVeriTeC style). Current Q+A quality is still low
- Retrieving from tables and text together (FEVEROUS). A lot of work still treats evidence as sentences only
- Using the offline Knowledge Store from the 2024/2025 shared tasks, so you do not need live Google

This looks like the safest “actual research” direction. Most papers admit retrieval is the problem. It is still not solved.

---

## 2. Models trained on FEVER do not transfer well to real claims

FEVER-trained systems look decent on FEVER. On real data they drop a lot.

- **Climate-FEVER:** same pipeline is about 77.7% on FEVER dev, but only **38.8%** on climate claims (F1 around 32.9%). They also needed a DISPUTED label, because real climate arguments are not clean SUPPORTS / REFUTES
- **CFEVER (Chinese):** even strong English systems, when ported, do worse than they do on English FEVER
- **X-FACT:** around 41.9 macro F1 in-domain. Out-of-domain / zero-shot language drops to about 15–17. Models seem to overfit language-specific patterns

So there is a whole area here: **domain shift, language shift, and label shift** in fact verification.

**Possible directions**
- Why FEVER pretraining helps SciFact a bit, but fails so badly on Climate-FEVER
- How to handle disputed / conflicting evidence (Climate-FEVER DISPUTED, AVeriTeC cherry-picking)
- Whether 3-way Wikipedia labels even make sense for real-world claims
- Cross-lingual transfer that is more than just running mBERT

---

## 3. Labels are inconsistent, and “true” is not a stable target

This is easy to skip, but it affects everything.

- **LIAR:** 6 PolitiFact classes (pants-fire to true). Accuracy around 0.27, barely above majority
- **MultiFC:** 26 websites, each with its own rating scheme. They did not force one scale
- **X-FACT:** same issue across 25 languages. Ratings had to be normalised
- **NoFake:** crawled 90+ sites, merged labels manually, then BERT looks strong (about 83% F1). A lot of that depends on how the labels were merged

The task itself is not stable. Some of the “model improvement” is just taxonomy choices.

**Possible directions**
- Treat label harmonisation as the research problem, not just preprocessing
- Ordinal / ranking setup instead of 6-class softmax (pants-fire vs false is not the same gap as false vs true)
- Learning with mixed label spaces (MultiFC tried MTL + label embeddings in 2019; not much follow-up in this set of papers)
- Keep “partially true” and cherry-picking as real labels, not leftovers

This is a good direction if messy real data is more interesting than leaderboard scores.

---

## 4. LLM justifications can look correct without being faithful

AVeriTeC asks systems to produce questions, answers, **and** a written justification. Evidence is scored with Hungarian METEOR overlap (cutoff λ = 0.25, later 0.5 in 2025).

METEOR is surface overlap. A model can paraphrase the gold text, write a fluent but wrong explanation, or retrieve something that matches on words and still be wrong.

**Gaps**
- Faithfulness: does the verdict actually follow from the evidence the model showed?
- Better grounding than METEOR (citations, attribution)
- Full pages vs snippets. X-FACT already found snippets are often not enough
- Claim-only bias: the model ignores evidence and just guesses from the claim text (also seen in X-FACT)

This is currently a hot area: **faithful RAG fact-checking**.

In 2024, the organiser baseline was about 0.11 and some teams reached 0.6+, mostly from better retrieval + LLMs. In 2025 they asked for open-weight / cheaper systems and raised the evidence cutoff. The winner is only around 0.33.

There is still space here, especially if the goal is not “just call GPT”.

---

## 5. Systems need to be cheaper and actually runnable

The 2025 shared task is basically the community saying research systems are too heavy.

- New test set with later claims (from 2024), more numerical claims (~39%)
- Knowledge Store is huge: about 1.02M URLs / 2.5B tokens
- Baseline: Llama-3.1-8B + BM25 + SFR embeddings → about 0.20
- Winner: about 0.33
- Latency and open weights matter now

**Possible directions**
- Small open RAG fact-checkers
- Distillation / quantisation of the full pipeline
- Retrieval that does not have to scan a huge store naively
- Strict temporal cutoffs, so future articles do not leak into “evidence”

If the project should look a bit more systems-oriented: build a fact checker that can actually run, not only a leaderboard model.

---

## 6. Multi-hop, tables, and numbers need real reasoning

HoVer exists because FEVER can often be solved with word matching. At 3–4 hops, retrieval basically falls apart.

FEVEROUS adds Wikipedia tables, infoboxes, and lists. Using both text and tables is better than either alone, but the baseline is still weak.

AVeriTeC 2025 has more numerical claims. Those look easy (just compare numbers) until the number is inside a table, a PDF, or two sources use different units.

**Underexplored**
- Joint table + text retrieval, not just “linearise the table and hope”
- Quantitative / numerical fact checking as its own problem
- Causal claims (harder; 2025 has fewer of them, so current scores may look a bit optimistic)
- Quote verification
- Combining evidence from multiple pages (CFEVER also has this in Chinese)

This is closer to hard NLP than training a classifier on PolitiFact statements.

---

## 7. Content models and social-spread models are still separate

Monti et al. use graph CNNs on Twitter cascades. Around 92.7% ROC AUC, and it already works after about 2 hours of spread. It is mostly language-agnostic, and harder to fool by rewriting the text.

FANG uses an inductive heterogeneous graph (GraphSAGE) plus temporal engagements and stance. The dataset is small (~1k news items), but the embeddings also help predict source factuality.

The FEVER / AVeriTeC papers almost never look at who shared the claim.

The gap is fairly obvious: **hybrid content + propagation**.

**Ideas**
- Graph model for early warning, then RAG for later confirmation
- Comment stance as extra evidence (FANG started this)
- What to do when Twitter-style graph access is limited
- Echo chambers / polarised sources as features
- Language-agnostic detection for languages where X-FACT transfer already failed

These graph datasets are tiny compared to FEVER. Collecting usable social data is itself a problem now.

---

## 8. Most work is on short claims. Real misinformation is not always short

Almost everything in these 20 papers is a short claim. One sentence, maybe a short statement.

A lot of real misinformation is:

- a long article with one wrong part buried in it
- a screenshot
- a video with a misleading caption
- a meme

Only Paper 15 (Hou et al., 2025, XMDFaVer) really tries long news: summarise → extract claims → QA against a fact pool → classify. They also introduce a Misbar long-news resource.

Murayama’s survey lists satire, clickbait, propaganda, spam, hyperpartisan news, etc. A lot of “fake news” datasets mix these, and then people are surprised that models get confused.

**Still quite open**
- Claim extraction from long documents (do not verify the whole article, find the checkable parts)
- Multimodal fact checking (image + text, out-of-context photos). Almost missing from this set of 20 papers
- Satire vs disinformation vs honest mistakes (intention is rarely labelled)
- Headline vs body mismatch

If the project should move away from FEVER-style short claims, long-form or multimodal is the most empty area.

---

## 9. Multilingual and non-English work is thin

X-FACT is the main resource here (31k claims, 25 languages). Best in-domain result is still around 42 F1. Zero-shot is much worse.

CFEVER is a good Chinese Wikipedia version of FEVER, but it is still synthetic Wikipedia, not real Chinese fact-check claims.

AVeriTeC uses 50 fact-checking organisations, but it is still a limited slice of the world, and English-heavy.

**Possible directions**
- Real-world non-English fact checking (not Wikipedia mutations)
- Using evidence in one language to check a claim in another
- Code-switching, local context, political knowledge that is not in English Wikipedia
- Whether one multilingual RAG system is enough, or each language needs its own setup

This is a more useful gap than another English-only leaderboard.

---

## 10. Evaluation often makes systems look better than they are

A lot of papers report label accuracy. That number is often the wrong one.

Better metrics exist, they are just stricter:

- FEVER score — verdict **and** correct evidence
- HoVer score / FEVEROUS score
- AVeriTeC score — veracity only counts if evidence also matches

If evidence is ignored, models can look almost twice as good. That is how a paper can “solve” fact checking and then fail the moment you ask for a source.

Other evaluation issues:

- Temporal leakage (using articles published after the claim)
- Claim-only shortcuts (the claim text already hints the answer)
- METEOR as a weak proxy for evidence quality
- Human agreement is only okay (FEVER κ = 0.68, AVeriTeC κ ≈ 0.62, CFEVER 0.79). The task is ambiguous for people too

**Better evaluation for automated fact checking** is not a flashy topic, but it is useful, and it is a valid research direction.

---

## 11. Smaller gaps that are still valid

These are more specific, but they are real:

**Claim normalisation.** AVeriTeC spends a whole annotation phase making claims standalone. Real claims sound like “he said that yesterday about the bill”. Models need speaker / date / location, but should not cheat with that metadata.

**Hidden reasoning.** Sometimes a claim cannot be refuted unless you know *why* it was made. AVeriTeC mentions this (Glockner et al.). Example: “vaccines may kill sharks” only makes sense if you know the squalene argument. QA pairs are supposed to recover that. It still does not work that well.

**Metadata vs text.** On LIAR, adding metadata barely helps (0.270 → 0.274). On MultiFC, metadata helps a lot. So it depends. Using speaker party as a feature is also a fairness issue.

**Low-data domains.** SciFact has 1.4k claims. Climate-FEVER has 1.5k. FANG is also small. The interesting domains are often tiny. FEVER’s 185k makes people forget that.

**Domain routing.** NoFake Task 3B (health, election, crime, climate, economy, education) is basically “send this to the right human”. That is a practical piece and not studied much here.

**Science beyond abstracts.** SciFact uses abstracts + rationales. Real scientific misinformation often cites paywalled papers, preprints, or one figure out of context. Retrieval is the bottleneck there too.

**Adversarial rewriting.** Monti et al. argue that spread features are more robust than text, because a lie can be paraphrased. Most FEVER-style papers do not attack their own systems.

**Who the user is.** A tool for journalists, a fully automatic verdict, and a social media ranking system have different costs for errors. Most papers just optimise accuracy as if these are the same product.

---

## Research fields (short list)

If the goal is to pick a lane, these are the actual fields. Not just “fake news detection”:

1. Evidence retrieval for fact verification
2. Multi-hop / compositional reasoning over documents
3. Hybrid structured + unstructured evidence (tables, infoboxes, stats)
4. Real-web RAG fact checking (questions + answers + justification)
5. Faithful explanations / grounded justifications
6. Domain transfer (Wikipedia → climate / science / politics / news)
7. Multilingual and cross-lingual verification
8. Heterogeneous labels / truthfulness scales
9. Conflicting evidence, cherry-picking, disputed claims
10. Time-aware verification (no future leakage)
11. Social-context / propagation graphs, and hybrids with NLP
12. Early fake news detection (hours after posting, not after a fact-check article exists)
13. Long-document misinformation (claim extraction + fact pools)
14. Multimodal misinformation (very thin in this literature)
15. Efficient open-weight fact checkers
16. Evaluation methods for automated fact checking
17. Taxonomy / intention (misinfo vs disinfo vs satire vs rumour)
18. Domain-specific verification (science, climate, health)
19. Numerical / quantitative claim checking
20. Human-in-the-loop systems (routing claims to journalists, ranking what to check first)

---

## What is actually doable (being realistic)

Not all of the above are equally possible with the datasets already in this project.

**Easier to start, still valid**
- Retrieval experiments on FEVER / HoVer / AVeriTeC Knowledge Store
- FEVER → Climate-FEVER transfer, with error analysis (DISPUTED vs NEI vs retrieval failure)
- A small AVeriTeC-style QA pipeline on the offline Knowledge Store (no Google API cost)
- Label merging experiments (LIAR 6-way vs binary, MultiFC multi-task)
- Small open LLM + BM25 vs dense retrieval comparison (similar spirit to the 2025 shared task)
- Summarise-then-verify on long news (direction of Paper 15)

**Medium, more interesting**
- Hybrid GNN + content model (social data is the annoying part)
- A faithfulness metric for justifications that is not METEOR
- Table-aware retrieval on FEVEROUS
- X-FACT out-of-domain analysis, maybe English evidence for non-English claims

**Harder, but high value**
- Multimodal data / models
- A new regional / Indian / non-English real-world fact-check set
- Intention labels (satire vs lie)
- A live temporal evaluation setup that does not leak

---

## If I had to pick five

This is just after reading the papers, not a final decision:

1. **Retrieval + question generation for real-web claims** — AVeriTeC still has a big gap after two shared tasks
2. **Conflicting / cherry-picked / disputed evidence** — most systems treat the world as binary
3. **Transfer from clean Wikipedia tasks to messy real claims**, and actually explaining why it fails
4. **Faithful explanations** — otherwise LLM fact checkers just write confident text
5. **Long-form or multimodal** — short-claim FEVER is a crowded format, even if the scores are still low

The common thread is retrieval / evidence. If a project does not make evidence finding better, more honest, or more usable, it is probably another classifier on top of a pile that already has too many.

---

*Based on `Literature_Review_Factual_NonFactual_Information.md` and the paper extracts.*
