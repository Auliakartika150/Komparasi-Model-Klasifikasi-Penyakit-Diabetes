# Komparasi Metode Extreme Learning Machine, Support Vector Machine, dan Multi-Layer Perceptron untuk Prediksi Diabetes

---

## Dataset & Preprocessing
* **Sumber Data:** *Diabetes Prediction Dataset* dari Kaggle (100.000 data medis pasien dan 9 fitur klinis).
* **Masalah Data:** Terdapat ketidakseimbangan data (*data imbalance*) yang signifikan antara kelas non-diabetes (mayoritas) dan diabetes (minoritas).
* **Tahapan Preprocessing:**
  * Konversi variabel kategorikal menggunakan **One-Hot Encoding**.
  * Standarisasi fitur numerik menggunakan **Standard Scaler (Z-Score)**.
  * Pembagian data secara deterministik dengan proporsi **70% Data Latih** dan **30% Data Uji**.

---

## 🛠️ Metode yang Dibandingkan
1. **Extreme Learning Machine (ELM):** Jaringan saraf dengan *single hidden layer* yang unggul pada kecepatan pelatihan analitik tanpa iterasi panjang.
2. **Support Vector Machine (SVM):** Menggunakan **Kernel RBF** untuk menangani pemisahan pola keputusan non-linear berdimensi tinggi.
3. **Multi-Layer Perceptron (MLP):** Jaringan saraf tiruan multi-lapisan dengan optimasi *backpropagation* (Adam Optimizer) untuk mempelajari representasi fitur yang kompleks.

---

## Hasil Evaluasi dan Komparasi

Pengujian performa pada 30.000 sampel data uji menunjukkan hasil *trade-off* kinerja sebagai berikut:

### 1. Metrik Performa & Waktu Komputasi

| Metode | Akurasi Global | Recall (Kelas 1 - Diabetes) | F1-Score (Kelas 1 - Diabetes) | Waktu Pelatihan (Detik) |
| :--- | :---: | :---: | :---: | :---: |
| **Multi-Layer Perceptron (MLP)** | **97.15%** | **0.69** | **0.80** | 75.5635 s |
| **Support Vector Machine (SVM)** | 96.36% | 0.59 | 0.73 | 36.6104 s |
| **Extreme Learning Machine (ELM)** | 95.75% | 0.55 | 0.69 | **2.1130 s** |

### 2. Analisis Performa
* **Akurasi & Ketahanan Bias tertinggi:** **MLP** memperoleh akurasi tertinggi (**97,15%**). Model ini terbukti paling tangguh menghadapi *data imbalance* dengan mencatatkan nilai *Recall* kelas minoritas tertinggi (0,69), yang berarti hanya luput mendeteksi sekitar 31% kasus aktual diabetes.
* **Efisiensi Komputasi Terbaik:** **ELM** jauh unggul mutlak dari segi kecepatan komputasi dengan waktu pelatihan hanya **2,1130 detik**. Namun, ELM memiliki kerentanan yang sedikit lebih tinggi terhadap bias data kelas minoritas.

---

## Kesimpulan (Findings)

* **Model Paling Optimal:** **Multi-Layer Perceptron (MLP)** sangat direkomendasikan sebagai model terbaik untuk sistem skrining medis deteksi dini diabetes karena mampu memberikan keseimbangan akurasi agregat tertinggi serta performa prediksi paling stabil pada kelas pasien positif diabetes.
* **Pengembangan Selanjutnya:** Mengingat waktu latih MLP cenderung lama, implementasi masa depan disarankan mengeksplorasi teknik *resampling* tambahan seperti **SMOTE** untuk mendongkrak sensitivitas model SVM/ELM atau memanfaatkan akselerasi GPU pada arsitektur MLP.
