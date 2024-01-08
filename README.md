# Overview
- MathGPT is a project wherein I finetune open-source LLMs to perform better at solving mathematical problems. I intend to use this as a sandbox to experiment with datasets and finetuning approaches to understand the amount of finetuning required to observe a significant improvement in the mathematical capabilities of any model.

## Mistral-7b LoRA
- First, I finetuned the mistral-7b model on a subset of TIGER-Lab's [MathInstruct dataset](https://tiger-ai-lab.github.io/MAmmoTH/) which uses data that "uniquely focuses on hybrid use of chain-of-thought (CoT) and program-of-thought (PoT) rationales". They have done remarkable work in curating this vast dataset and some of their finetuned models outperform GPT-4 at competition-level math problems.
- Owing to computational limitations, I could only use a small subset of their CoT rational, around 4000 datapoints.
- I employed the LoRA or Low-Rank Adaptation approach to make the finetuning process more efficient, implemented through the peft module by HuggingFace.
- The training and some testing notebooks are found in this repository whereas my finetuned model can be found on HuggingFace through this [link](https://huggingface.co/akashvshroff/mistral-7b-math).
- A very rudimentary (and perhaps, flawed) example of the model performing better at intermediate algebra is below. Here, the model represents my finetuned model whereas the base model represents the basic mistral-7b model that the finetuned model was based on. These outputs might be one-off cases, however, I found that the finetuned model seemed to reason through its working more clearly in most cases even if its computation weren't accurate.

  ![image](https://github.com/akashvshroff/MathGPT/assets/63399889/9bf8404d-cdb4-438c-9c22-82967b29c031)
  
- In terms of improvement, I think the most important thing to do would be to perform more fine-tuning, using a larger subset of the MathInstruct dataset as well as more training epochs.
