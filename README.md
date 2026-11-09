# Stable Diffusion Image Generation Experiments

A Google Colab project created as a course submission, exploring image generation and editing with pretrained Stable Diffusion pipelines from Hugging Face Diffusers. It uses pretrained models for inference and compares generation settings through visual experiments.

## Implemented Experiments

| Experiment | What the notebook does |
| --- | --- |
| Text-to-image | Generates images from a prompt and a negative prompt, with a fixed seed. |
| Guidance scale | Compares values of **5, 7, 12, and 15**. |
| Inference steps | Compares **10, 30, and 50** denoising steps, with a separate 75-step example. |
| Batch generation | Produces four image variations from one prompt. |
| Schedulers | Compares Euler Ancestral, DPMSolverMultistep, and DDIM schedulers. |
| Manual inpainting | Draws an elliptical mask with Pillow and edits that area using a text prompt. |

An outpainting section constructs an image canvas with an additional **256 pixels on the right**, creates a mask for the new area, and calls the inpainting pipeline to generate content there.

The example prompt describes an astronaut in a white spacesuit on the moon, with Earth and a star-filled sky in the background, in a 2D illustration style.

## Tools and Models

- **Tools:** Python, PyTorch, Diffusers, Transformers, Accelerate, Safetensors, NumPy, Pillow, and Matplotlib.
- **Text-to-image model ID in the notebook:** `runwayml/stable-diffusion-v1-5`.
- **Inpainting model ID in the notebook:** `runwayml/stable-diffusion-inpainting`.
- **Environment:** Google Colab with a CUDA GPU; the saved notebook metadata specifies a T4.

## Run in Google Colab

1. Open `stable_diffusion_experiments.ipynb` in Colab.
2. Select a **GPU** runtime. The current code uses `cuda` directly.
3. Run the dependency installation cell and load the text-to-image pipeline. Model weights are downloaded from Hugging Face.
4. Run the text-to-image examples and parameter comparisons in order. Keep the same prompt and seed within each comparison.
5. Load the inpainting pipeline before running the masking and editing cells. It replaces the earlier `pipe` variable.

No separate training dataset is required for the implemented experiments. The inpainting input is generated earlier in the notebook.

## Results and Limitations

- **Saved results:** the current notebook contains text-to-image outputs, guidance-scale and inference-step comparisons, four image variations, and a scheduler comparison. Inpainting and outpainting code is included, but their generated image outputs are not saved in this version.
- **Outpainting dimensions:** the canvas is expanded before generation. The generation call does not explicitly set its output width and height, so the final image dimensions should be checked when rerunning this section.
- **Evaluation:** comparisons are visual and exploratory. No numerical quality metrics or systematic benchmark are included, and observations apply to the displayed examples.
- **Reproducibility:** dependency versions are not pinned; outputs may vary across library versions, hardware, and settings.

## References

- [Diffusers text-to-image documentation](https://huggingface.co/docs/diffusers/api/pipelines/stable_diffusion/text2img)
- [Diffusers inpainting documentation](https://huggingface.co/docs/diffusers/api/pipelines/stable_diffusion/inpaint)

## Author

Akhtar Maulana A — [Doddlet](https://github.com/Doddlet)
