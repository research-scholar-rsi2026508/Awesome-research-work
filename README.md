# Awesome Grounded vs. Ungrounded LLMs

A curated collection of research papers, datasets, tools, implementations, and learning resources related to grounded versus ungrounded large language models (LLMs), with a focus on factual accuracy, hallucination, retrieval-augmented generation (RAG), provenance, and domain-specific research queries.

This repository is based primarily on the research paper **“Comparing Grounded and Ungrounded LLM Response Accuracy on Domain-Specific Research Queries.”**

## Contents

- [Overview](#overview)
- [AI-Assisted Research Paper](#ai-assisted-research-paper)
- [Survey Papers](#survey-papers)
- [Foundational Papers](#foundational-papers)
- [Recent Research Papers](#recent-research-papers)
- [Datasets](#datasets)
- [Tools and Libraries](#tools-and-libraries)
- [GitHub Implementations](#github-implementations)
- [Citation Integrity Audit](#citation-integrity-audit)
- [License](#license)

## Overview

Large language models are increasingly used for research and decision support in specialized domains such as law, medicine, and science. These settings require answers that are not only fluent but also factually accurate, verifiable, and attributable to reliable sources.

The paper compares two broad approaches:

- **Ungrounded / closed-book LLMs** — answer using knowledge stored in model parameters.
- **Grounded / RAG LLMs** — combine model knowledge with external evidence retrieved at inference time.

The paper concludes that grounding substantially improves accuracy, particularly for long-tail and low-frequency facts, but does not eliminate hallucinations. Instead, residual errors often shift from wholesale fabrication toward misattribution, misapplication, and retrieval failure.

## AI-Assisted Research Paper

**Comparing Grounded and Ungrounded LLM Response Accuracy on Domain-Specific Research Queries**

[View Paper](paper/AI_Assisted_Research_Paper.pdf)

## Survey Papers

- **Gao et al. (2023)** — *Retrieval-Augmented Generation for Large Language Models: A Survey*
  - https://arxiv.org/abs/2312.10997
- **Ji et al. (2023)** — *Survey of Hallucination in Natural Language Generation*
  - https://doi.org/10.1145/3571730

## Foundational Papers

- **Lewis et al. (2020)** — *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*
  - https://arxiv.org/abs/2005.11401
- **Shuster et al. (2021)** — *Retrieval Augmentation Reduces Hallucination in Conversation*
  - https://aclanthology.org/2021.findings-emnlp.320/
- **Ji et al. (2023)** — *Survey of Hallucination in Natural Language Generation*
  - https://doi.org/10.1145/3571730

## Recent Research Papers

- **Asai et al. (2024)** — *Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection*
  - https://arxiv.org/abs/2310.11511
- **Dahl et al. (2024)** — *Large Legal Fictions: Profiling Legal Hallucinations in Large Language Models*
  - https://academic.oup.com/jla/article/16/1/64/7699227
- **Magesh et al. (2025)** — *Hallucination-Free? Assessing the Reliability of Leading AI Legal Research Tools*
  - https://doi.org/10.1111/jels.12413
- **Mallen et al. (2023)** — *When Not to Trust Language Models: Investigating Effectiveness of Parametric and Non-Parametric Memories*
  - https://aclanthology.org/2023.acl-long.546/
- **Singhal et al. (2023)** — *Large Language Models Encode Clinical Knowledge*
  - https://doi.org/10.1038/s41586-023-06291-2
- **Li et al. (2023)** — *HaluEval: A Large-Scale Hallucination Evaluation Benchmark for Large Language Models*
  - https://aclanthology.org/2023.emnlp-main.397/
- **Lin et al. (2022)** — *TruthfulQA: Measuring How Models Mimic Human Falsehoods*
  - https://aclanthology.org/2022.acl-long.229/
- **Min et al. (2023)** — *FActScore: Fine-Grained Atomic Evaluation of Factual Precision in Long Form Text Generation*
  - https://aclanthology.org/2023.emnlp-main.741/
- **Manakul et al. (2023)** — *SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models*
  - https://aclanthology.org/2023.emnlp-main.557/

## Datasets

See [datasets/datasets.md](datasets/datasets.md).

## Tools and Libraries

See [tools/tools.md](tools/tools.md).

## GitHub Implementations

See [implementations/github-repositories.md](implementations/github-repositories.md).

## Citation Integrity Audit

See [citation-audit/Citation_Integrity_Audit.pdf](citation-audit/Citation_Integrity_Audit.pdf).

## Key Findings

The paper reports the clearest matched legal-domain comparison as:

| System | Reported hallucination/error range |
|---|---:|
| Ungrounded general-purpose LLMs | 58–88% |
| Deployed RAG-based legal research tools | 17–33% |

Grounding therefore provides a substantial reduction in error, but it is not an accuracy guarantee.

Other major findings:

1. Retrieval is particularly useful for long-tail, low-frequency knowledge.
2. Ungrounded systems are more prone to fabricated facts and citations.
3. Grounded systems can misattribute or misapply genuine retrieved evidence.
4. Retrieval quality becomes a new source of system failure.
5. Self-reflective and modular RAG approaches are promising mitigations.
6. Human verification and provenance remain necessary for high-stakes research.

## Research Challenges

- Benchmark-domain mismatch
- Closed commercial systems and limited reproducibility
- Confounding grounding with model/prompt/guardrail differences
- Unreliable model self-assessment
- Binary rather than graded hallucination metrics
- Static snapshot evaluations

## Future Research Directions

- Cross-domain replication of legal-style audits
- Provenance-aware domain-specific accuracy metrics
- Independent evaluation of retriever quality and generator faithfulness
- Longitudinal/versioned evaluations
- User-facing calibration and abstention
- Task-conditioned accuracy definitions

## License

This repository is intended for educational and research purposes. Individual papers, datasets, source code, and external resources remain subject to their respective licenses and terms of use.
