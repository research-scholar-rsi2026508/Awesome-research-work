# Tools and Libraries

## Retrieval-Augmented Generation (RAG)

RAG systems combine a language model with external retrieval. The paper identifies retrieval as a key mechanism for improving access to recent and long-tail knowledge.

## Self-RAG

Self-RAG adds adaptive retrieval and reflection-based critique.

Official project:
https://selfrag.github.io/

Official implementation:
https://github.com/AkariAsai/self-rag

The implementation provides models, training data, inference code, retrieval setup, baselines, and evaluation scripts.

## FActScore

FActScore provides atomic-fact-level factuality evaluation.

Paper:
https://aclanthology.org/2023.emnlp-main.741/

## TruthfulQA Evaluation

TruthfulQA provides generation and multiple-choice evaluation of model truthfulness.

Repository:
https://github.com/sylinrl/TruthfulQA

## RAG Survey Resources

The RAG Survey repository collects academic papers, benchmarks, evaluation resources, toolkits, and RAG ecosystem information.

Repository:
https://github.com/Tongji-KGLLM/RAG-Survey

## Important Evaluation Principle

The existence of a retrieval layer does not by itself establish accuracy. Retrieval quality, evidence relevance, chunking, ranking, generator faithfulness, and source quality all affect final performance.
