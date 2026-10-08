---
license: apache-2.0
pipeline_tag: zero-shot-classification
tags:
- gguf
- quantized
- decision-model
- system-one
base_model:
- vllm-sr/Decision-2.0-Lux-9B
base_model_relation: quantized
---

# Decision-2.0-Lux-9B

GGUF versions of [Decision-2.0-Lux-9B](https://huggingface.co/vllm-sr/Decision-2.0-Lux-9B), part of [Decision 2.0](https://huggingface.co/collections/vllm-sr/decision-20) by vLLM Semantic Router. The model answers choice, yes/no and score questions about text or JSON in one forward pass, returning probabilities for the supplied options.

Requires the [Decision 2.0 development branch of llama.cpp](https://github.com/Xunzhuo/llama.cpp/tree/decision2-gguf), which adds conversion of the `Decision2Model` package and the candidate-head runtime. Upstream llama.cpp does not support this format yet. Build that branch using the [llama.cpp build guide](https://github.com/Xunzhuo/llama.cpp/blob/decision2-gguf/docs/build.md), then run:

```bash
./build/bin/llama-server -hf __owner__/Decision-2.0-Lux-9B-GGUF:Q8_0 -c 8192 -b 8192 -ub 8192 -ngl 99
```

Use the `/v1/systemone` API for text or JSON input. The batch and microbatch must accommodate a question's option and query suffix together; the example sets both to the context size. BF16, Q8_0 and Q4_K_M versions are provided; the small candidate head remains float32 in all three.

### Jev Decision Index

Lux 9B scores 48.21, numerically above Clef Flash 9B at 47.61 (+0.60). The difference is within the Index's 0.9-point tie tolerance.

These are **source-model Full scores**, not measurements of these GGUF files, from [Jev Decision Index 0.3](https://huggingface.co/spaces/multimodalart/jev-decision-index), snapshot `2026-10-07T18:25:58Z`. [Score data](https://huggingface.co/spaces/multimodalart/jev-decision-index/blob/960c70899ef5da38d39b2c645b83f46e198e1a6a/data/v03.json) · [Model metadata](https://huggingface.co/spaces/multimodalart/jev-decision-index/blob/960c70899ef5da38d39b2c645b83f46e198e1a6a/data/index.json).

### Source model

- https://huggingface.co/vllm-sr/Decision-2.0-Lux-9B

> [!IMPORTANT]
> This model is automatically converted using https://github.com/ggml-org/convert.
