# Awesome Grounded vs. Ungrounded LLMs

A curated collection of research papers, benchmarks, datasets, tools, implementations, and learning resources related to **grounded versus ungrounded large language models (LLMs)**, with a focus on factual accuracy, hallucination, retrieval-augmented generation (RAG), provenance, and domain-specific research queries.

The repository is based primarily on the research paper **“Comparing Grounded and Ungrounded LLM Response Accuracy on Domain-Specific Research Queries.”** The paper synthesizes evidence across hallucination research, RAG, factuality benchmarks, and domain-specific audits in law and medicine.

## Contents

* [Overview](#overview)
* [AI-Assisted Research Paper](#ai-assisted-research-paper)
* [Survey Papers](#survey-papers)
* [Foundational Papers](#foundational-papers)
* [Recent Research Papers](#recent-research-papers)
* [Datasets and Benchmarks](#datasets-and-benchmarks)
* [Tools and Libraries](#tools-and-libraries)
* [GitHub Implementations](#github-implementations)
* [Tutorials and Learning Resources](#tutorials-and-learning-resources)
* [Key Findings](#key-findings)
* [Grounded vs. Ungrounded Comparison](#grounded-vs-ungrounded-comparison)
* [Research Challenges](#research-challenges)
* [Research Gaps and Future Directions](#research-gaps-and-future-directions)
* [Citation Integrity Audit](#citation-integrity-audit)
* [References](#references)
* [License](#license)

## Overview

Large language models are increasingly used for research and decision support in specialized domains such as law, medicine, and science. These settings require answers that are not only fluent but also factually accurate, verifiable, and attributable to reliable sources.

Two broad approaches are considered:

* **Ungrounded / closed-book LLMs** — answer using knowledge stored in model parameters.
* **Grounded LLMs** — combine model knowledge with external evidence retrieved at inference time, most commonly through Retrieval-Augmented Generation (RAG).

Grounding can provide access to newer information, improve coverage of long-tail facts, and make provenance possible. However, the evidence reviewed in the paper shows that grounding is **necessary but insufficient** for reliable domain-specific accuracy.

### Central finding

Grounded systems generally make substantially fewer factual errors than ungrounded systems, but they continue to produce unsupported or incorrect answers.

The clearest legal-domain comparison reported in the paper is:

| System type                               | Reported hallucination/error rate |
| ----------------------------------------- | --------------------------------: |
| Ungrounded general-purpose LLMs           |                        **58–88%** |
| Commercial RAG-based legal research tools |                        **17–33%** |

Thus, grounding can produce roughly a **two-to-fourfold reduction in error**, but it does not make a system hallucination-free.

---

## AI-Assisted Research Paper

### Comparing Grounded and Ungrounded LLM Response Accuracy on Domain-Specific Research Queries

**Focus:** Grounded versus ungrounded LLMs, hallucination, RAG, factual accuracy, legal AI, clinical NLP, and domain-specific research.

The paper asks three principal questions:

1. How much does grounding improve accuracy compared with parametric-only generation?
2. What failure modes remain in grounded systems?
3. What methodological and infrastructural limitations prevent confident generalization?

**Key conclusion:** Grounding improves accuracy substantially, particularly for long-tail and low-frequency facts, but residual errors remain and require provenance, independent verification, and human oversight.

**Local paper:** `paper/AI_Assisted_Research_Paper.pdf`

---

## Survey Papers

### 1. Retrieval-Augmented Generation for Large Language Models: A Survey

**Gao et al. (2023)**

A broad survey organizing RAG research into:

* Naive RAG
* Advanced RAG
* Modular RAG
* Retrieval
* Generation
* Augmentation
* Evaluation
* Challenges and future directions

The survey emphasizes that RAG addresses hallucination, outdated knowledge, and the lack of transparent knowledge access by incorporating external databases.

[Paper — arXiv](https://arxiv.org/abs/2312.10997?utm_source=chatgpt.com)
[RAG Survey GitHub Repository](https://github.com/Tongji-KGLLM/RAG-Survey?utm_source=chatgpt.com)

### 2. Survey of Hallucination in Natural Language Generation

**Ji et al. (2023)**

A foundational survey of hallucination research that distinguishes:

* Intrinsic hallucination
* Extrinsic hallucination
* Factuality hallucination
* Faithfulness hallucination

This taxonomy is particularly important for comparing grounded and ungrounded systems because grounding can reduce fabricated information while leaving faithfulness errors unresolved.

[ACM Computing Surveys paper](https://doi.org/10.1145/3571730?utm_source=chatgpt.com)

---

## Foundational Papers

### Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks

**Lewis et al. (2020)**

The original RAG work combines:

* A pretrained parametric language model
* A non-parametric external memory
* A neural retriever
* A dense vector index

The authors report improved performance on knowledge-intensive tasks and more specific, diverse, and factual language compared with parametric-only baselines.

[RAG Paper — arXiv](https://arxiv.org/abs/2005.11401?utm_source=chatgpt.com)

### Retrieval Augmentation Reduces Hallucination in Conversation

**Shuster et al. (2021)**

Investigates retrieval-in-the-loop architectures for knowledge-grounded dialogue and finds that retrieval substantially reduces hallucination while maintaining conversational capabilities.

[ACL Anthology](https://aclanthology.org/2021.findings-emnlp.320/?utm_source=chatgpt.com)

### Survey of Hallucination in Natural Language Generation

**Ji et al. (2023)**

Provides the hallucination taxonomy used throughout the research paper and helps explain why grounding changes the *type* of error rather than eliminating errors entirely.

---

## Recent Research Papers

### Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection

**Asai et al. (2024)**

Self-RAG addresses a major weakness of conventional RAG: retrieving information when retrieval is unnecessary or incorporating irrelevant passages.

The system learns to:

1. Decide when retrieval is necessary.
2. Retrieve relevant evidence.
3. Generate an answer.
4. Critique retrieved evidence and generated content.
5. Use reflection tokens to control generation.

The published work reports improvements over ChatGPT and retrieval-augmented Llama 2 Chat across several tasks, including factuality and citation accuracy.

[Self-RAG Paper](https://arxiv.org/abs/2310.11511?utm_source=chatgpt.com)

### Large Legal Fictions: Profiling Legal Hallucinations in Large Language Models

**Dahl et al. (2024)**

A systematic audit of legal hallucinations in public-facing LLMs. The study reports hallucination rates ranging from approximately **58% for GPT-4 to 88% for Llama 2** on specific, verifiable federal court questions. It also finds that models can fail to recognize their own hallucinations and may accept incorrect legal premises from users.

[Journal of Legal Analysis](https://academic.oup.com/jla/article/16/1/64/7699227?utm_source=chatgpt.com)

### Hallucination-Free? Assessing the Reliability of Leading AI Legal Research Tools

**Magesh et al. (2025)**

A preregistered evaluation of commercial RAG-based legal research systems, including Lexis+ AI, Westlaw AI-Assisted Research, and Ask Practical Law AI.

The study found that these systems hallucinated approximately **17–33% of the time**, despite claims that RAG could eliminate or avoid hallucinations.

[Journal of Empirical Legal Studies](https://onlinelibrary.wiley.com/doi/10.1111/jels.12413?utm_source=chatgpt.com)

### When Not to Trust Language Models: Investigating Effectiveness of Parametric and Non-Parametric Memories

**Mallen et al. (2023)**

Shows that parametric models struggle particularly with **less popular, long-tail factual knowledge**. Retrieval augmentation provides substantial benefits in these cases, while scaling models mainly improves memorization of popular knowledge.

[ACL Anthology](https://aclanthology.org/2023.acl-long.546/?utm_source=chatgpt.com)

### Large Language Models Encode Clinical Knowledge

**Singhal et al. (2023)**

Introduces **MultiMedQA** and evaluates medical LLM performance using multiple medical QA datasets plus human assessment of:

* Factuality
* Comprehension
* Reasoning
* Potential harm
* Bias

This supports the paper's argument that medical grounding cannot simply be treated as a retrieval problem because clinical questions often require reasoning across guidelines, evidence, and patient-specific context.

[Nature paper](https://doi.org/10.1038/s41586-023-06291-2?utm_source=chatgpt.com)

### HaluEval: A Large-Scale Hallucination Evaluation Benchmark

**Li et al. (2023)**

HaluEval provides generated and human-annotated hallucination examples for evaluating whether LLMs can recognize hallucinations. The study reports that hallucinated content appeared in approximately **19.5% of sampled user queries** and that models have difficulty recognizing hallucinations without external knowledge or additional reasoning.

[HaluEval — ACL Anthology](https://aclanthology.org/2023.emnlp-main.397/?utm_source=chatgpt.com)

---

## Datasets and Benchmarks

### PopQA

A long-tail open-domain QA dataset containing approximately **14,000 questions** focused on entities of varying popularity.

**Purpose:** Evaluating whether parametric memory or retrieval is better suited to factual knowledge.

Mallen et al. show that retrieval is particularly beneficial for low-popularity entities.

### TruthfulQA

A benchmark containing **817 questions across 38 categories**, including health, law, finance, and politics.

It tests whether models reproduce common human misconceptions. The original study found that the best tested model was truthful on 58% of questions, compared with 94% human performance.

[TruthfulQA — ACL Anthology](https://aclanthology.org/2022.acl-long.229/?utm_source=chatgpt.com)

[TruthfulQA GitHub](https://github.com/sylinrl/TruthfulQA?utm_source=chatgpt.com)

### HaluEval

A benchmark for hallucination detection containing generated and human-annotated hallucinated samples.

[HaluEval — ACL Anthology](https://aclanthology.org/2023.emnlp-main.397/?utm_source=chatgpt.com)

### FActScore

FActScore evaluates long-form factuality at the **atomic-fact level** rather than assigning one binary hallucination label to an entire response.

The metric computes the percentage of atomic facts supported by a reliable knowledge source. The authors also provide an automated evaluation approach using retrieval and a language model.

[FActScore — ACL Anthology](https://aclanthology.org/2023.emnlp-main.741/?utm_source=chatgpt.com)

### MultiMedQA

A medical benchmark combining multiple existing medical QA datasets with HealthSearchQA and evaluating models across factuality, comprehension, reasoning, potential harm, and bias.

---

## Tools and Libraries

### Self-RAG

Adaptive retrieval and self-reflection framework designed to improve factuality and citation accuracy.

[Official Self-RAG implementation](https://github.com/AkariAsai/self-rag?utm_source=chatgpt.com)

### FActScore

Atomic-fact factuality evaluation framework for measuring whether generated claims are supported by reliable evidence.

[FActScore research page](https://ai.meta.com/research/publications/factscore-fine-grained-atomic-evaluation-of-factual-precision-in-long-form-text-generation/?utm_source=chatgpt.com)

### RAG Frameworks

The RAG literature surveyed by Gao et al. covers retrieval, reranking, query transformation, compression, generation, and modular architectures.

Common ecosystem technologies include:

* LangChain
* LlamaIndex
* Vector databases
* Dense retrievers
* Rerankers
* Knowledge bases
* Search engines

These should be treated as implementation technologies rather than evidence that a system is automatically accurate.

---

## GitHub Implementations

### Self-RAG

Official implementation containing:

* 7B and 13B models
* Retrieval components
* Training code
* Evaluation scripts
* Baselines
* Training data
* Inference pipelines

[AkariAsai/self-rag](https://github.com/AkariAsai/self-rag?utm_source=chatgpt.com)

The repository supports both vanilla LM and retrieval-augmented baselines, allowing researchers to compare parametric-only and retrieval-based approaches.

### TruthfulQA

Official benchmark implementation containing:

* Dataset files
* Evaluation code
* Demonstration notebooks
* Multiple-choice evaluation resources

[TruthfulQA GitHub](https://github.com/sylinrl/TruthfulQA?utm_source=chatgpt.com)

### RAG Survey Repository

A companion repository for the RAG survey containing research materials and a growing collection of RAG resources.

[RAG-Survey GitHub](https://github.com/Tongji-KGLLM/RAG-Survey?utm_source=chatgpt.com)

---

## Tutorials and Learning Resources

### RAG Fundamentals

Study the original RAG architecture:

**Parametric memory + external non-parametric memory → retrieved evidence → generation**

[Original RAG paper](https://arxiv.org/abs/2005.11401?utm_source=chatgpt.com)

### Self-RAG

Learn adaptive retrieval and reflection-based generation through the official implementation and documentation.

[Self-RAG project website](https://selfrag.github.io/?utm_source=chatgpt.com)

### Hallucination Evaluation

Recommended progression:

1. Study the Ji et al. hallucination taxonomy.
2. Run TruthfulQA.
3. Explore HaluEval.
4. Evaluate long-form output using FActScore.
5. Examine retrieved evidence and citation correctness.
6. Conduct human verification for high-stakes domains.

---

## Key Findings

### 1. Grounding improves accuracy

Across the evidence synthesized in the paper, matched comparisons generally favor grounded systems.

### 2. Grounding is especially valuable for long-tail knowledge

Parametric-only models perform worse as facts become less popular or less frequently represented in training data. Retrieval remains comparatively effective across the popularity distribution.

### 3. Grounding changes the error type

Ungrounded systems are more likely to **invent**:

* Facts
* Citations
* Cases
* Holdings
* Procedural details

Grounded systems are more likely to:

* Misinterpret retrieved evidence
* Attribute a proposition to the wrong source
* Apply a real source incorrectly
* Combine facts from different retrieved documents

### 4. Retrieval introduces its own failure surface

A poor retriever can fail to find the relevant evidence because of:

* Vocabulary mismatch
* Poor indexing
* Ambiguous queries
* Missing domain coverage
* Incorrect ranking

In such cases, the generator may either fabricate an answer or under-answer/abstain.

### 5. More retrieval is not always better

Naive RAG can retrieve irrelevant passages and thereby reduce answer quality. Self-RAG was specifically designed to address this problem through adaptive retrieval and reflection.

### 6. Legal and medical domains behave differently

Legal research is particularly compatible with retrieval because statutes and case holdings are discrete, authoritative, and identifiable documents.

Medical questions often require synthesis across guidelines, patient context, and evolving evidence, meaning retrieval alone is insufficient.

---

## Grounded vs. Ungrounded Comparison

| Dimension                    | Ungrounded LLM                   | Grounded / RAG LLM                                   |
| ---------------------------- | -------------------------------- | ---------------------------------------------------- |
| Knowledge source             | Static parametric weights        | Parametric weights + retrieved external evidence     |
| Main error                   | Fabricated facts/citations       | Misattribution or misapplication of real evidence    |
| Long-tail facts              | Performance declines with rarity | More stable with retrieval                           |
| Provenance                   | No intrinsic source provenance   | Partial provenance through retrieved evidence        |
| Recency                      | Limited by training/update cycle | Can access current indexed information               |
| Retrieval failure            | Not applicable                   | Important additional failure mode                    |
| Generator failure            | Hallucination/confabulation      | Evidence misinterpretation or unsupported generation |
| Legal hallucination evidence | ~58–88%                          | ~17–33% in audited RAG tools                         |
| Main quality dependency      | Model/training data              | Retriever + corpus + generator + prompting           |
| Verification requirement     | High                             | Still high                                           |

This comparison is synthesized directly from the paper's Table 1 and surrounding analysis.

---

## Current Approaches

### Self-Reflective Retrieval

Self-RAG allows a model to determine whether retrieval is needed, evaluate retrieved passages, and assess whether generated material is supported.

### Advanced and Modular RAG

Modern RAG pipelines can incorporate:

* Query rewriting
* Query decomposition
* Retrieval
* Re-ranking
* Filtering
* Compression
* Iterative retrieval
* Multi-hop retrieval

These approaches aim to improve the quality of evidence supplied to the generator.

### Atomic Factuality Evaluation

FActScore represents a move away from binary “hallucinated/not hallucinated” evaluation toward evaluating individual factual claims and their supporting evidence.

### Independent Product Auditing

The legal-domain audit methodology demonstrates the importance of independently testing commercial systems rather than relying solely on vendor claims.

---

## Research Challenges

### Benchmark-Domain Mismatch

TruthfulQA, HaluEval, and FActScore were largely developed around general or encyclopedic knowledge. Their results may not transfer directly to professional research domains.

### Closed Commercial Systems

Commercial RAG systems often expose neither their retrievers nor indexes, prompts, ranking methods, or system configurations, making independent reproduction difficult.

### Confounding Variables

Grounded-versus-ungrounded comparisons may also differ in:

* Model size
* Fine-tuning
* Prompting
* Guardrails
* System engineering

Consequently, the independent causal contribution of grounding can be difficult to isolate.

### Self-Assessment Is Not Enough

LLMs can fail to recognize their own hallucinations, even when relevant evidence is present. Independent verification therefore remains important.

### Binary Evaluation Is Too Coarse

A response containing one minor citation problem and a response containing a completely false conclusion may both be classified as “hallucinated.” Atomic evaluation methods such as FActScore provide a more informative alternative.

### Static Evaluations Become Outdated

Models, retrieval indexes, and commercial products change rapidly, so an accuracy measurement represents a particular system version at a particular point in time.

---

## Research Gaps and Future Directions

### Cross-Domain Auditing

Extend the rigorous legal audit methodology to:

* Medicine
* Scientific research
* Finance
* Engineering

### Provenance-Aware Metrics

Develop benchmarks combining atomic factual precision with authoritative domain-specific sources such as:

* Case-law databases
* Statutory databases
* Clinical guidelines
* Peer-reviewed literature indexes

### Retriever vs. Generator Evaluation

Future experiments should independently measure:

* Retriever recall
* Retriever precision
* Evidence relevance
* Generator faithfulness
* End-to-end accuracy

### Longitudinal Evaluation

Track system accuracy and hallucination rates across different versions of models and commercial retrieval products rather than relying on one-time evaluations.

### Calibration and Abstention

Future systems should provide mechanisms such as:

* Confidence calibration
* Mandatory citations
* Structured abstention
* Evidence display

These mechanisms can help professionals avoid treating fluent answers as automatically verified.

### Task-Conditioned Accuracy

Accuracy should be separated into dimensions such as:

1. Citation existence
2. Citation/content characterization
3. Applicability to the facts

This is particularly important in law and medicine, where different errors have different consequences.

---

## Citation Integrity Audit

The repository should maintain a separate audit documenting whether each major claim is supported by:

* The original research paper
* The cited academic publication
* An authoritative publisher or conference source
* An official implementation
* A dataset or benchmark repository

Recommended audit fields:

| Claim                                  | Source               | Source Type         | Verified? | Notes                           |
| -------------------------------------- | -------------------- | ------------------- | --------- | ------------------------------- |
| RAG improves factual generation        | Lewis et al. (2020)  | Foundational paper  | ✅         | Original RAG study              |
| Retrieval benefits long-tail knowledge | Mallen et al. (2023) | Empirical study     | ✅         | PopQA / EntityQuestions         |
| Ungrounded legal hallucination         | Dahl et al. (2024)   | Legal audit         | ✅         | 58–88% reported range           |
| Grounded legal hallucination           | Magesh et al. (2025) | Preregistered audit | ✅         | 17–33% reported range           |
| Self-RAG improves factuality           | Asai et al. (2024)   | ICLR paper          | ✅         | Adaptive retrieval + reflection |
| Atomic factuality evaluation           | Min et al. (2023)    | EMNLP paper         | ✅         | FActScore                       |

The uploaded paper itself provides the complete reference list underlying these claims.

---

## References

1. Asai, A., Wu, Z., Wang, Y., Sil, A., & Hajishirzi, H. (2024). *Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection*. ICLR 2024.

2. Dahl, M., Magesh, V., Suzgun, M., & Ho, D. E. (2024). *Large Legal Fictions: Profiling Legal Hallucinations in Large Language Models*. Journal of Legal Analysis, 16(1), 64–93.

3. Gao, Y., et al. (2023). *Retrieval-Augmented Generation for Large Language Models: A Survey*.

4. Ji, Z., et al. (2023). *Survey of Hallucination in Natural Language Generation*. ACM Computing Surveys, 55(12).

5. Lewis, P., et al. (2020). *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*. NeurIPS 2020.

6. Li, J., et al. (2023). *HaluEval: A Large-Scale Hallucination Evaluation Benchmark for Large Language Models*. EMNLP 2023.

7. Lin, S., Hilton, J., & Evans, O. (2022). *TruthfulQA: Measuring How Models Mimic Human Falsehoods*. ACL 2022.

8. Magesh, V., et al. (2025). *Hallucination-Free? Assessing the Reliability of Leading AI Legal Research Tools*. Journal of Empirical Legal Studies, 22(2), 216–242.

9. Mallen, A., et al. (2023). *When Not to Trust Language Models: Investigating Effectiveness of Parametric and Non-Parametric Memories*. ACL 2023.

10. Manakul, P., Liusie, A., & Gales, M. J. F. (2023). *SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models*. EMNLP 2023.

11. Min, S., et al. (2023). *FActScore: Fine-Grained Atomic Evaluation of Factual Precision in Long Form Text Generation*. EMNLP 2023.

12. Shuster, K., et al. (2021). *Retrieval Augmentation Reduces Hallucination in Conversation*. Findings of EMNLP 2021.

13. Singhal, K., et al. (2023). *Large Language Models Encode Clinical Knowledge*. Nature, 620, 172–180.

---

## License

This repository is intended for **educational and research purposes**.

Individual papers, datasets, source code, and external resources remain subject to their respective licenses and terms of use.
