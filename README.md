# aksty/promptgen: Prompt generation for Text-to-Image Models

Huggingface model : [aksty/promptgen](https://huggingface.co/aksty/promptgen)

![visitor badge](https://visitor-badge.glitch.me/badge?page_id=08318068.1e87.409b.93cf.c37ff4df6538gh)

This is a text generation model trained on data specifically designed to generate prompts for text-to-image models. It is based on the [EleutherAI/gpt-neo-125M](https://huggingface.co/EleutherAI/gpt-neo-125M) pre-trained model, which has been fine-tuned using the [Gustavosta/Stable-Diffusion-Prompts](https://huggingface.co/datasets/Gustavosta/Stable-Diffusion-Prompts) dataset.

### Notebook with promptgen + Stable Diffusion v2 
[![image](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)](https://colab.research.google.com/github/aksty/promptgen/blob/main/notebook/StableDiffusion_with_PromptGen.ipynb)

![image](https://huggingface.co/aksty/promptgen/resolve/main/image.jpg)



## Usage

To use this model, you will need to have `PyTorch` and the `transformers` library installed. You can then use the following code to generate text using the model:

```python
import torch
from transformers import GPT2Tokenizer, GPTNeoForCausalLM
tokenizer = GPT2Tokenizer.from_pretrained("aksty/promptgen")
model = GPTNeoForCausalLM.from_pretrained("aksty/promptgen")
def generate_text(prompt):
  input_ids = tokenizer(prompt, return_tensors="pt").input_ids
  outputs = model.generate(input_ids, do_sample=True, max_length=100)
  return tokenizer.batch_decode(outputs, skip_special_tokens=True)
```

Output :
```python
generate_text("A painting of an ancient city ")
```
```
['A painting of an ancient city  on the top of a cliff, a small sign charging through the sky, cinematic view, epic sky, detailed, concept art, low angle, high detail, warm lighting, volumetric, godrays, vivid, beautiful, trending on artstation, by jordan grimmer, huge scene, grass, art greg rutkowski']
```

## Disclaimer
It is important to note that the results generated by promptgen are not guaranteed to be accurate, complete, or suitable for any particular purpose. The model is intended for research and educational purposes only and should not be relied upon for any other purposes. The generated text may contain errors, omissions, or inappropriate language. The user of the model is solely responsible for any actions or decisions made based on the generated text.


