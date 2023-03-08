![Header](https://raw.githubusercontent.com/Maseshi/Animistatics/main/assets/header.png)

# Animistatics

Welcome to Animistatics - a latent diffusion model for weebs. This model is intended to produce high-quality, highly detailed anime style with just a few prompts. Like other anime-style Stable Diffusion models, it also supports danbooru tags to generate images.

e.g. **_girl, cafe, plants, coffee, lighting, steam, blue eyes, brown hair_** 

## Gradio

We support a [Gradio](https://github.com/gradio-app/gradio) Web UI to run Animistatics:

[![Open In Spaces](https://camo.githubusercontent.com/00380c35e60d6b04be65d3d94a58332be5cc93779f630bcdfc18ab9a3a7d3388/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f25463025394625413425393725323048756767696e67253230466163652d5370616365732d626c7565)](https://huggingface.co/spaces/Maseshi/Animistatics)

## Google Colab

We support a [Google Colab](https://github.com/gradio-app/gradio) to run Animistatics:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Maseshi/Animistatics/blob/main/animistatics.ipynb)

## 🧨 Diffusers

This model can be used just like any other Stable Diffusion model. For more information,
please have a look at the [Stable Diffusion](https://huggingface.co/docs/diffusers/api/pipelines/stable_diffusion).

You can also export the model to [ONNX](https://huggingface.co/docs/diffusers/optimization/onnx), [MPS](https://huggingface.co/docs/diffusers/optimization/mps) and/or [FLAX/JAX]().

```python
from diffusers import DiffusionPipeline, DPMSolverMultistepScheduler
import torch

repo_id = "Maseshi/Animistatics"
pipe = DiffusionPipeline.from_pretrained(repo_id, torch_dtype=torch.float16)

pipe.scheduler = DPMSolverMultistepScheduler.from_config(pipe.scheduler.config)
pipe = pipe.to("cuda")

prompt = "girl, cafe, plants, coffee, lighting, steam, blue eyes, brown hair"
image = pipe(prompt, num_inference_steps=25).images[0]
image.save("girl.png")
```

## Examples

Below are some examples of images generated using this model:

**Anime Girl:**
![Anime Girl](https://raw.githubusercontent.com/Maseshi/Animistatics/main/assets/girl.png)
```
girl, cafe, plants, coffee, lighting, steam, blue eyes, brown hair
Steps: 50, Sampler: DDIM, CFG scale: 12
```
**Anime Boy:**
![Anime Boy](https://raw.githubusercontent.com/Maseshi/Animistatics/main/assets/boy.png)
```
boy, blonde hair, blue eyes, colorful, cumulonimbus clouds, lighting, medium hair, plants, city, hoodie, cool
Steps: 50, Sampler: DDIM, CFG scale: 12
```
**City:**
![City](https://raw.githubusercontent.com/Maseshi/Animistatics/main/assets/city.png)
```
cityscape, concept art, sun shining through clouds, crepuscular rays, trending on art station, 8k
Steps: 50, Sampler: DDIM, CFG scale: 12
```

## License

This model is open access and available to all, with a CreativeML OpenRAIL-M license further specifying rights and usage.
The CreativeML OpenRAIL License specifies: 

1. You can't use the model to deliberately produce nor share illegal or harmful outputs or content 
2. The authors claims no rights on the outputs you generate, you are free to use them and are accountable for their use which must not go against the provisions set in the license
3. You may re-distribute the weights and use the model commercially and/or as a service. If you do, please be aware you have to include the same use restrictions as the ones in the license and share a copy of the CreativeML OpenRAIL-M to all your users (please read the license entirely and carefully)
[Please read the full license here](https://huggingface.co/spaces/CompVis/stable-diffusion-license)
