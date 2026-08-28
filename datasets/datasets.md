# Datasets and Benchmarks

The research paper identifies several benchmarks relevant to hallucination, factuality, long-tail knowledge, and domain-specific evaluation.

## TruthfulQA

TruthfulQA evaluates whether language models produce truthful answers to questions designed to expose common misconceptions.

- Paper: Lin, Hilton & Evans (2022)
- https://aclanthology.org/2022.acl-long.229/
- GitHub: https://github.com/sylinrl/TruthfulQA

The official repository includes benchmark questions, reference answers, evaluation code, and a newer multiple-choice setting.

## HaluEval

HaluEval is a large-scale benchmark containing machine-generated and human-annotated hallucination examples.

- Paper: Li et al. (2023)
- https://aclanthology.org/2023.emnlp-main.397/

## FActScore

FActScore evaluates factual precision at the atomic-claim level and verifies claims against explicit knowledge sources.

- Paper: Min et al. (2023)
- https://aclanthology.org/2023.emnlp-main.741/

## MultiMedQA

MultiMedQA combines multiple medical question-answering datasets and evaluates medical LLMs using both automated and clinician-oriented dimensions.

- Paper: Singhal et al. (2023)
- https://doi.org/10.1038/s41586-023-06291-2

## PopQA

PopQA is a long-tail question answering benchmark used to investigate when parametric memory is sufficient and when retrieval provides an advantage.

- Discussed in Mallen et al. (2023)
- https://aclanthology.org/2023.acl-long.546/

## Benchmarking Guidance

For domain-specific research, benchmark results should be interpreted carefully. The paper notes that many common factuality benchmarks were designed around general or encyclopedic knowledge and may not transfer directly to professional domains.
