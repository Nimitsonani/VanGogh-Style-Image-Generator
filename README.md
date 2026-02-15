# VanGogh-Style-Image-Generator

This project fine-tunes Stable Diffusion v1.5 using LoRA on a dataset of Van Gogh paintings.

After training, the model can generate images in the style of Van Gogh from any given text prompt.

The repository is divided into two parts:

- **training/** → LoRA fine-tuning process  
- **deployment/** → loading the trained weights and generating images  

The final output of training is a `.safetensors` file containing the learned style weights.

---

## What This Project Does

1. Fine-tunes Stable Diffusion v1.5 using LoRA.
2. Learns stylistic patterns from Van Gogh paintings.
3. Saves the learned style as a lightweight `.safetensors` file.
4. Loads the base Stable Diffusion model during inference.
5. Applies the trained LoRA weights.
6. Generates new images in Van Gogh style from any text prompt.

The base model is not retrained entirely.  
LoRA adjusts specific layers, making the fine-tuning process efficient.

---

## Sample Outputs

### Prompt: `pirate`

[![Pirate Output](https://github.com/user-attachments/assets/ffb79f36-383f-4b4c-9658-c4febb2208be)](https://github.com/user-attachments/assets/ffb79f36-383f-4b4c-9658-c4febb2208be)

---

### Prompt: `Albert Einstein`

[![Einstein Output](https://github.com/user-attachments/assets/5e43ba6c-b554-43c8-97ec-b7baff7ee88c)](https://github.com/user-attachments/assets/5e43ba6c-b554-43c8-97ec-b7baff7ee88c)

---

## How Image Generation Works

- Stable Diffusion v1.5 is loaded.
- The trained LoRA `.safetensors` file is applied.
- A text prompt is provided.
- The model generates a new image influenced by the learned Van Gogh style.

Any prompt can be used — the learned style modifies the visual characteristics of the output.

---

## Deployment Overview

The notebook `VanGogh_Image_Generator.ipynb` inside the **deployment** folder:

- Loads the base model
- Loads the LoRA weights
- Runs a FastAPI server
- Uses ngrok to expose the interface (when running in Colab)

The server runs on port `8000` in Colab, and ngrok provides a temporary public URL.

---

## Required Folder Structure

Before running the deployment notebook, create:

VanGogh/  
├── image/  
├── lora/  
├── template/  
└── .env  

- **image/** → where generated images are saved  
- **lora/** → place the trained `.safetensors` file here  
- **template/** → place `index.html` here  
- **.env** → store your ngrok token  

Example `.env`:

```
TOKEN=your_ngrok_token_here
```

After setting up:

1. Compress the `VanGogh` folder to `.rar`.
2. Upload it to Colab.
3. Extract it.
4. Run the notebook.
5. Open the generated ngrok URL to generate styled images.

---

## Technologies Used

- Stable Diffusion v1.5
- LoRA (Low-Rank Adaptation)
- PyTorch
- FastAPI
- Google Colab
- ngrok



