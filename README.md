# ReACT+CRAG: Enhancing Reasoning-Acting Agents with Coherence-Ranked Generation

### Objective

This project aims to **reproduce and extend** two advanced prompting techniques for language models:

* **ReACT** (Yao et al., ICLR 2023), which combines **reasoning and acting** within prompts,
* **CRAG** (Yan et al., arXiv 2024), which improves **logical coherence** by **ranking** multiple candidate generations.

We combine these techniques to reduce hallucinations and improve reasoning reliability on complex multi-hop tasks.

---

## Target Task

The focus is on generating **logically coherent multi-step answers** from already retrieved documents.
This is **not** a retrieval improvement task — the goal is to **strengthen generation coherence** in settings requiring multiple reasoning steps.

---

## Project Structure

### Datasets (`/data/`)

* **HotpotQA**:

  * `hotpot_train_v1.1_simplified.json`
  * `hotpot_dev_v1_simplified.json`
  * `hotpot_test_v1_simplified.json`
* **Other data**:

  * `val.json`, `val_rl.json`, `paper_dev.jsonl`
  * `quantum.txt` (raw text sample)
* **Results**: `reward_plot.png`

### Prompts (`/prompts/`)

* `prompts_naive.json`, `alfworld.json`, `fever.json`, `alfworld_3prompts.json`: variants for different datasets or reasoning styles.

### Notebooks

* `Exploring_ReAct_on_Langchain.ipynb`: manual ReACT pipeline using Langchain
* `hotpotqa_GPT3.ipynb`: ReACT applied to HotpotQA using GPT-3
* `hotpotQA_crag_GPT3.ipynb`: integration of CRAG into ReACT for better coherence
* `crag.ipynb`: standalone CRAG scoring and reranking

### Scripts

* `wikienv.py`, `wrappers.py`: environment simulation and helper functions
* `base_config.yaml`: configuration for experiments

---

## Evaluation Metrics

* **EM (Exact Match)**: measures whether the generated answer exactly matches the ground truth
* **(Optional)**: coherence or logical reliability score (under development using CRAG ranking)

---

## Preliminary Results

| Method                       | HotpotQA EM | FEVER EM |
| ---------------------------- | ----------- | -------- |
| GPT-3.5-turbo + CRAG (ReACT) | **25.0**    | **51.0** |
| GPT-3.5-turbo (ReACT only)   | 19.2        | 45.4     |

---

## References

```bibtex
@inproceedings{yao2023react,
  title = {{ReAct}: Synergizing Reasoning and Acting in Language Models},
  author = {Yao, Shunyu et al.},
  booktitle = {ICLR},
  year = {2023},
  url = {https://arxiv.org/abs/2210.03629}
}

@article{yan2024corrective,
  title={Corrective Retrieval Augmented Generation},
  author={Yan, Shi-Qi et al.},
  journal={arXiv preprint arXiv:2401.15884},
  year={2024},
  url = {https://arxiv.org/abs/2401.15884}
}
```