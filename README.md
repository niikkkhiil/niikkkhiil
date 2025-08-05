
#  Ayna ML Assignment — Polygon Color Filler (UNet + PyTorch)

This project was built as a response to the Ayna ML Internship Assignment. The objective was to implement a UNet model from scratch that takes:
- A grayscale image of a polygon (e.g., triangle, square, octagon)
- A color name as input (e.g., "red", "blue")

The model outputs a filled polygon image in the specified color.

---

##  Prompt-Based Development Log

This project was built incrementally based on detailed prompts and collaborative feedback. Here's a step-by-step summary reflecting the development process:

### ✅ Initial Problem Understanding
The assignment required:
- A custom UNet in PyTorch
- Dataset parsing from a provided JSON structure
- Conditioning the model on the color input
- Inference and visualization in a Colab-compatible notebook
- Integration with Weights & Biases (wandb)

###  Notebook Workflow
1. **Environment Setup** — Installed required packages including `wandb`.
2. **Dataset Preparation** — Downloaded from the provided Google Drive link and unzipped into a `dataset/` folder.
3. **Custom Dataset Loader** — Built a PyTorch `Dataset` class to:
    - Load polygon grayscale image
    - Convert color name to RGB tensor
    - Stack grayscale + color into a 4-channel input
4. **UNet Model** — Designed a lightweight UNet with 4-channel input and 3-channel output (RGB).
5. **Training Loop** — Implemented using L1 loss and Adam optimizer. Integrated logging to `wandb` with image samples.
6. **Inference Module** — Created a helper function to predict color-filled polygons given an image path and color name.
7. **Final README Report** — Summarized model structure, hyperparameters, learnings, and inference examples.

---

## Architecture Overview

- **Input shape**: `4 x 64 x 64` (1 grayscale + 3 color channels)
- **Output shape**: `3 x 64 x 64` (RGB)
- **Model**: UNet with encoder-decoder, skip connections
- **Loss**: L1 Loss (Mean Absolute Error)
- **Activation**: Sigmoid (for RGB output in [0,1] range)

---

##  Sample Inference

You can run inference by providing:
- Polygon image path from validation set
- A valid color name (from defined color map)

```python
gray, prediction = predict(model, "inputs/sample1.png", "blue", transform, device)
```

It returns the input grayscale polygon and predicted color-filled output.

---

## wandb Logging

Training and validation losses along with image samples were logged using [Weights & Biases](https://wandb.ai/). Sample visualizations per epoch helped verify the model’s learning progress.

---

## Learnings & Observations

- Learned how to condition vision models using non-image input (color as a vector)
- Understood the benefit of keeping model inputs simple yet effective
- Gained experience implementing custom PyTorch UNet from scratch
- Practiced collaborative and prompt-driven development

---

## Dataset Structure

```
dataset/
├── training/
│   ├── inputs/
│   ├── outputs/
│   └── data.json
└── validation/
    ├── inputs/
    ├── outputs/
    └── data.json
```

---

##  To Run

1. Clone repo or open in Google Colab.
2. Run all cells step-by-step.
3. Use the final cell to run inference and visualize output.

---

##  Submission Summary

- ✅ UNet model implemented
- ✅ Trained on custom dataset
- ✅ Integrated with wandb
- ✅ Inference notebook complete
- ✅ README included

---

### Author: Nikhil Ganorkar
_Aspiring ML Intern at Ayna_
