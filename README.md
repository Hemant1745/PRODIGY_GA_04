# PRODIGY_GA_04
 📘 Pix2Pix (Conditional GAN for Image-to-Image Translation) - 

#### **1. Overview**

Pix2Pix is a deep learning method based on **Conditional GANs (cGANs)** for **image-to-image translation**. It learns to map an input image to a corresponding output image, such as:

* Sketch → Photo
* Black & White → Color
* Map → Satellite view

---

#### **2. Key Components**

* **Generator (G)**: A U-Net-based model that converts the input image to the output domain.
* **Discriminator (D)**: A PatchGAN that determines if the generated image is real or fake by analyzing small patches of the image.

---

#### **3. Loss Functions**

* **Adversarial Loss**: Makes generated images look real.
* **L1 Loss (Mean Absolute Error)**: Keeps output close to the ground truth.

The total loss:

```
L_total = L_cGAN(G, D) + λ * L1(G)
```

---

#### **4. Dataset Format**

Pix2Pix needs **paired images**. Usually, each image is one file where:

* Left half = input
* Right half = expected output

The model splits them automatically during loading.

---

#### **5. U-Net Generator**

U-Net is an encoder-decoder with **skip connections**. It helps retain fine details and structure while transforming the image.

---

#### **6. PatchGAN Discriminator**

Instead of checking the whole image, PatchGAN checks small **70×70 patches** for realness. This helps the model focus on **texture and sharpness**.

---

#### **7. Training Process**

1. Load side-by-side images and split into input/target.
2. Generator tries to create a fake output image.
3. Discriminator checks if the input + generated image looks real.
4. Both models are optimized with loss functions.

---

#### **8. Applications**

* Colorization of grayscale images
* Edge maps → photos
* Maps ↔ Satellite images
* Labels → street views

---

 **9. Limitations**

* Needs **paired datasets**, which are harder to get than unpaired data.
* Doesn't generalize well to completely new domains.
* Can produce blurry results without L1 loss or enough data.



