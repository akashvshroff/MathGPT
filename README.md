# Overview
- MathGPT is a project wherein I finetune open-source LLMs to perform better at solving mathematical problems. I intend to use this as a sandbox to experiment with datasets and finetuning approaches to understand the amount of finetuning required to observe a significant improvement in the mathematical capabilities of any model.

## Mistral-7b LoRA
- First, I finetuned the mistral-7b model on a subset of TIGER-Lab's [MathInstruct dataset](https://tiger-ai-lab.github.io/MAmmoTH/) which uses data that "uniquely focuses on hybrid use of chain-of-thought (CoT) and program-of-thought (PoT) rationales". They have done remarkable work in curating this vast dataset and some of their finetuned models outperform GPT-4 at competition-level math problems.
- Owing to computational limitations, I could only use a small subset of their CoT rational, around 5000 datapoints.
- I employed the LoRA or Low-Rank Adaptation approach to make the finetuning process more efficient, implemented through the peft module by HuggingFace.
- The training and some testing notebooks are found in this repository whereas my finetuned model can be found on HuggingFace through this [link](https://huggingface.co/akashvshroff/mistral-7b-math).
- Below, you can see a few basic examples of how the finetuning improved the mathematical reasoning ability of the model vis-a-vis the base model. While there may not be much merit in checking the computational ability of the model, the difference in reasoning is noticeable. Coupling this finetuning with a general instruction dataset could lead to a truly capable math model.

  ![model result 2](https://github.com/akashvshroff/MathGPT/assets/63399889/c758aa19-81bb-46fb-b408-6863b9b2e3e3)


  ![image](https://github.com/akashvshroff/MathGPT/assets/63399889/9302afb1-12ee-4297-95b1-9b4ae7f786cd)

- In terms of improvement, I think the most important thing to do would be to perform more fine-tuning, using a larger subset of the MathInstruct dataset as well as more training epochs. Moreover, since this is finetuning done on the base model, we could also couple this with other finetuned versions of the base model - perhaps with a general instruction set to improve its conversational ability.
