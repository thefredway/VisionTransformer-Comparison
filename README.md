# 🍱 Vision Transformer vs DeiT — Food Image Classification (5-Fold Cross Validation)

Repository ini berisi implementasi dan laporan eksperimen untuk membandingkan dua arsitektur Vision Transformer, yaitu **ViT (Vision Transformer)** dan **DeiT (Data-Efficient Image Transformer)** pada tugas **klasifikasi citra makanan Indonesia**.

Eksperimen dilakukan menggunakan pendekatan **fine-tuning**, **5-Fold Stratified Cross-Validation**, dan evaluasi kecepatan inferensi untuk mengukur akurasi sekaligus efisiensi model dalam skenario deployment.

---

## 📌 Tujuan Penelitian

1. Menguji dan membandingkan performa ViT dan DeiT pada dataset makanan Indonesia.
2. Mengidentifikasi trade-off antara:
   - jumlah parameter model
   - akurasi
   - waktu inferensi
   - kelayakan untuk implementasi _real-time_.

---

## 📂 Dataset

Dataset berisi **5 kelas makanan Indonesia**:

| Kelas       |
| ----------- |
| bakso       |
| gado_gado   |
| nasi_goreng |
| rendang     |
| soto_ayam   |

Dataset terdiri dari berkas gambar dan file CSV (`train.csv`) yang berisi kolom:

- `filename`
- `label`

> File `test.csv` tidak berisi sampel sehingga evaluasi dilakukan menggunakan **5-Fold Cross-Validation**.

---

## 🔧 Tools & Dependensi

Model dilatih dan diuji menggunakan:

- Python 3.10
- PyTorch
- timm
- Albumentations
- scikit-learn
- matplotlib & seaborn
- torchinfo

Notebook dapat dijalankan di Google Colab.

---

## ⚙️ Konfigurasi Training

| Parameter     | Nilai           |
| ------------- | --------------- |
| Optimizer     | AdamW           |
| Learning Rate | 1e-4            |
| Batch Size    | 32              |
| Epoch         | 5               |
| Scheduler     | Tidak digunakan |
| Loss Function | Cross Entropy   |

---

## 🧪 Metode Evaluasi

- **5-Fold Stratified Cross-Validation**
- **Metrik performa**: Accuracy, Macro Precision, Macro Recall, Macro F1
- **Analisis runtime**:
  - rata-rata waktu inferensi (ms/gambar)
  - throughput (gambar/detik)
- **Visualisasi**:
  - Kurva Loss & Accuracy
  - Confusion Matrix
  - Classification Report

---

## 📊 Ringkasan Hasil

| Model | Total Params | Val Acc (Mean) | Macro F1 | Infer Time (ms/img) | Throughput (img/s) |
| ----- | ------------ | -------------- | -------- | ------------------- | ------------------ |
| ViT   | 85.8M        | 0.9597         | 0.9598   | 10.21               | 97.90              |
| DeiT  | 21.6M        | 0.9747         | 0.9747   | 2.83                | 353.93             |

**Kesimpulan:**  
🔹 **DeiT mengungguli ViT** pada seluruh metrik — akurasi lebih tinggi, shortcut runtime lebih cepat, dan ukuran model lebih kecil.  
🔹 **DeiT direkomendasikan untuk implementasi real-time** (mobile apps, camera-based food classification, kasir otomatis).

---

## 🖼 Dokumentasi Visual

Repositori ini mencakup:

- Kurva Loss & Accuracy (per model)
- Confusion Matrix
- Classification Report
- Summary Comparison

Semua visualisasi tersimpan di folder penyimpanan hasil.

---

## 🚀 Cara Menjalankan

1. Clone repositori
   ```bash
   git clone <repo-url>
   ```
2. Jalankan notebook dari cell awal hingga akhir
