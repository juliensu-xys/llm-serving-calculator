# llm-serving-calculator

A single-page calculator that compares two GPU rigs for serving an LLM. You pick a GPU and a model for each rig from the presets, then enter the workload (prompt length, output length, number of users). It estimates:

- whether the model fits, and how many users the KV cache can hold
- tokens/s per user and total tokens/s at your user count
- time to first token (TTFT)
- total tokens/s with the KV cache full

**Live page:** https://juliensu-xys.github.io/llm-serving-calculator/

The decode model is roofline-style: max(memory time, compute time) + a fixed per-step overhead, with MoE expert coverage growing with batch size. The default efficiencies are tuned against NVIDIA's published DeepSeek-R1 results on 8× B200. Results are planning estimates (roughly ±30–50%), not benchmarks. All preset values can be overridden on the page.

Everything is in `index.html`, with no dependencies beyond Google Fonts.
