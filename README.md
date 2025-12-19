# Virtual Try-On using Computer Vision  
**UAS IBDA4311 – Computer Vision**

## Anggota Kelompok
- Bill Hensen (222102329)  
- Hizkia Justine Hasan (22210xxxx)  
- Owen Theodore Yosephus (222101499)  
- Albert Teofilus Kusumajaya (222101457)  
- Gery Yulianto (222101862)  

---

## Latar Belakang
Industri e-commerce fashion menghadapi permasalahan utama berupa keterbatasan konsumen dalam mencoba pakaian sebelum membeli. Hal ini sering menyebabkan ketidaksesuaian ukuran dan tampilan pakaian saat dikenakan, yang berdampak pada tingginya tingkat pengembalian produk (*return rate*) serta menurunnya kepuasan pelanggan.

Teknologi **Virtual Try-On (VTON)** hadir sebagai solusi untuk mensimulasikan pemakaian pakaian secara digital. Namun, pendekatan VTON konvensional berbasis gambar 2D masih memiliki keterbatasan dalam merepresentasikan bentuk tubuh, tekstur kain, dan pencahayaan secara realistis.

Untuk mengatasi tantangan tersebut, sistem VTON memerlukan sinergi antara dua komponen utama dalam **Computer Vision**, yaitu **model diskriminatif** dan **model generatif**. Oleh karena itu, proyek ini bertujuan untuk membandingkan performa berbagai model diskriminatif dan generatif dalam konteks Virtual Try-On.

---

## Tujuan Proyek
Tujuan dari proyek ini adalah:
1. Mengevaluasi performa **model diskriminatif** dalam melakukan segmentasi pakaian.
2. Mengevaluasi performa **model generatif** dalam menghasilkan hasil Virtual Try-On yang realistis.
3. Membandingkan kelebihan dan keterbatasan masing-masing pendekatan dalam sistem VTON.

---

## Model yang Digunakan

### 🔹 Discriminative Models
- **SAM2**  
  Repository: https://github.com/facebookresearch/sam2  
  Digunakan sebagai model segmentasi berbasis prompt (bounding box).

- **HRNet**  
  Digunakan sebagai model supervised segmentation untuk human parsing.

### 🔹 Generative Models
- **CatVTON**  
  Model Virtual Try-On berbasis diffusion.  
  Link: https://huggingface.co/zhengchong/CatV2TON-V2  

- **OOTDiffusion**  
  Model diffusion-based Virtual Try-On dengan fokus pada struktur dan pose.  
  Repository: https://github.com/levihsu/OOTDiffusion  

---

## Dataset
Proyek ini menggunakan **VITON-HD Dataset**, yang berisi sekitar **11.000 pasangan gambar** berkualitas tinggi yang terdiri dari:
- Gambar orang berpakaian
- Gambar pakaian
- Parsing mask / segmentation mask

Dataset ini menyediakan variasi atasan dengan resolusi tinggi, sehingga cocok untuk evaluasi sistem Virtual Try-On.

Sumber dataset:  
https://github.com/shadow2496/VITON-HD

---

## Metodologi Evaluasi

### 🔹 Evaluasi Model Diskriminatif
- **Input:** Citra orang
- **Output:** Mask segmentasi pakaian
- **Metrik:** Intersection over Union (IoU)
- Evaluasi difokuskan pada segmentasi **upper clothes**.

### 🔹 Evaluasi Model Generatif
- **Input:** Citra orang, citra pakaian, dan mask
- **Output:** Gambar hasil Virtual Try-On
- **Metrik:** Structural Similarity Index (SSIM)
- Evaluasi dilakukan dengan membandingkan hasil generasi dengan ground truth pada dataset paired.

---

## Struktur Repository
```text
virtual-try-on-computer-vision/
├── README.md
└── notebooks/
    ├── discriminative/
    │   ├── sam2-fine-tuning.ipynb
    │   ├── sam2-eval.ipynb
    │   ├── hrnet-fine-tuning.ipynb
    │   └── hrnet-eval.ipynb
    │
    └── generative/
        ├── catvton-fine-tuning.ipynb
        ├── catvton-eval.ipynb
        ├── ootdiffusion-fine-tuning.ipynb
        └── ootdiffusion-eval.ipynb

