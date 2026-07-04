# Task 05 – Neural Style Transfer

## What this project does
This project applies the artistic style of one image (e.g., a famous painting) onto the content of another image (e.g., a photo) using **Neural Style Transfer (NST)**.

The result is a new image that keeps the shapes/objects of the content photo, but is "painted" using the colors, textures, and brush strokes of the style image.

---

## How it works (short explanation)
1. A pretrained **VGG19** neural network is used only to extract features from images (it is not trained further).
2. **Content features** are taken from a deep layer of VGG19 — these represent the shapes/objects in the photo.
3. **Style features** are taken from multiple layers using a **Gram matrix**, which captures textures and patterns while ignoring their exact position.
4. A new image is created by starting with the content image and slowly updating its pixels so that:
   - its content stays close to the content image, and
   - its style (Gram matrices) becomes close to the style image.
5. This is done using gradient descent (the same core idea used to train neural networks, but here we update the image instead of the model weights).

---

## Tools & Libraries Used
- Python
- TensorFlow / Keras
- VGG19 (pretrained on ImageNet)
- NumPy
- Matplotlib
- Google Colab (T4 GPU)

---

## How to Run
1. Open the notebook in Google Colab.
2. Set the runtime to **GPU (T4)**.
3. Run all cells in order.
4. When prompted, upload:
   - a **content image** (the photo)
   - a **style image** (the painting)
5. The notebook will run the optimization loop and display the stylized image after every epoch.
6. The final result is saved as `stylized_output.jpg` and downloaded automatically.

---

## Parameters You Can Tune
| Parameter | Effect |
|---|---|
| `style_weight` | Higher = output looks more like the painting |
| `content_weight` | Higher = output stays closer to the original photo |
| `epochs` / `steps_per_epoch` | More steps = sharper result, but slower |

---

## Output
The final output is a single stylized image (`stylized_output.jpg`) that blends:
- **Content** → from the uploaded photo
- **Style** → from the uploaded painting/artwork

---

## Reference Material
- Towards Data Science – How Neural Style Transfer Works
- GeeksforGeeks – Neural Style Transfer with TensorFlow
- TensorFlow Official Tutorial – Neural Style Transfer
