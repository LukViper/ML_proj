# Research Gaps and Research Fields 

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

## Our 5 picks 

This is just after reading the papers, not a final decision:

1. **Retrieval + question generation for real-web claims** — AVeriTeC still has a big gap after two shared tasks
2. **Conflicting / cherry-picked / disputed evidence** — most systems treat the world as binary
3. **Transfer from clean Wikipedia tasks to messy real claims**, and actually explaining why it fails
4. **Faithful explanations** — otherwise LLM fact checkers just write confident text
5. **Long-form or multimodal** — short-claim FEVER is a crowded format, even if the scores are still low

The common thread is retrieval / evidence. If a project does not make evidence finding better, more honest, or more usable, it is probably another classifier on top of a pile that already has too many.

---

*Based on `Literature_Review_Factual_NonFactual_Information.md` and the paper extracts.*
