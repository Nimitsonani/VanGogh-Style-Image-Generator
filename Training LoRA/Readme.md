# LoRA Training – Van Gogh Style

This project fine-tunes Stable Diffusion v1.5 using LoRA to learn and reproduce the artistic style of Vincent Van Gogh.

Instead of retraining the full diffusion model, LoRA adapts a small set of additional parameters on top of the base model. This makes training lightweight, memory-efficient, and much faster compared to full fine-tuning.

After training, the model is capable of generating new images in Van Gogh style using the learned LoRA weights.

---

## Dataset Structure

Before training, prepare the dataset in the following format:

training_data/  
└── 1_images/  
  ├── image1.jpg  
  ├── image1.txt  
  ├── image2.jpg  
  ├── image2.txt  
  └── ...

Each image must have a corresponding `.txt` file with the same name.  
The `.txt` file contains the caption describing the image.

Steps:
- Compress the `training_data` folder.
- Upload it to the Colab notebook.
- Extract it inside the runtime before starting training.

---

## Environment Requirement

Training was performed in Google Colab.

Before running the notebook:
- Set the runtime to GPU.
- Ensure CUDA is available.

Training without GPU will not run properly.

---

## Training Setup

The notebook uses:

- Stable Diffusion v1.5 as the base model  
- kohya-ss sd-scripts for LoRA training  
- Mixed precision (fp16) for better memory efficiency  

LoRA fine-tunes only a small set of parameters instead of modifying the entire diffusion model.

---

## Output

During training, a folder named `lora_output` is automatically created.

Since the model is configured to save weights after every epoch, multiple `.safetensors` files will be generated inside this folder.

After training completes, download the final `.safetensors` file (from the last epoch). This file contains the learned Van Gogh style weights and is used later for image generation in the deployment notebook.

---

This notebook focuses only on the fine-tuning process. Deployment and inference are handled separately in the deployment folder.
