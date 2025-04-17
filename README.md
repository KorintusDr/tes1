# Laporan Proyek Machine Learning - Korintus Datu Rapang

## Domain Proyek - Kesehatan 

![Image](https://github.com/user-attachments/assets/d4fdca47-b2ab-4893-8c4d-3844a21af7ce)

Diabetes merupakan salah satu penyakit kronis yang paling umum di dunia. Menurut WHO, jumlah penderita diabetes meningkat setiap tahunnya. Oleh karena itu, deteksi dini terhadap potensi diabetes sangat penting agar pasien bisa segera mendapat penanganan medis yang tepat. Dengan menggunakan pendekatan machine learning, kita dapat memprediksi apakah seseorang berisiko mengidap diabetes berdasarkan parameter-parameter medis yang tersedia.

## Business Understanding

### Problem Statements
1. Bagaimana cara memprediksi apakah seseorang mengidap diabetes berdasarkan data medis yang tersedia?
2. Algoritma mana yang memberikan hasil prediksi paling akurat?

### Goals
1. Membangun model prediktif untuk menentukan apakah seorang pasien mengidap diabetes.
2. Mengevaluasi dan membandingkan performa beberapa algoritma machine learning.

### Solution Statements
- Menggunakan algoritma Logistic Regression, K-Nearest Neighbors, Decision Tree, Random Forest, dan Support Vector Machine.
- Melakukan evaluasi performa menggunakan Confusion Matrix, Precision, Recall, dan F1-Score.

## Data Understanding

### Sumber Data
- Dataset yang digunakan adalah **Pima Indians Diabetes Database** dari [UCI Machine Learning Repository](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)

### Uraian Fitur
| Nama Fitur                 | Deskripsi                                                         |
|---------------------------|-------------------------------------------------------------------|
| `Pregnancies`             | Jumlah kehamilan                                                  |
| `Glucose`                 | Kadar glukosa dalam darah                                         |
| `BloodPressure`           | Tekanan darah diastolik (mm Hg)                                   |
| `SkinThickness`           | Ketebalan lipatan kulit triceps (mm)                              |
| `Insulin`                 | Kadar insulin serum 2 jam                                         |
| `BMI`                     | Indeks massa tubuh (berat badan (kg) / tinggi badan² (m²))        |
| `DiabetesPedigreeFunction`| Riwayat diabetes berdasarkan silsilah keluarga                    |
| `Age`                     | Usia (dalam tahun)                                                |
| `Outcome`                 | Hasil (1: diabetes, 0: tidak diabetes)                            |


### Jumlah Data
- **Baris (Observasi):** 768
- **Kolom (Fitur):** 9 (8 fitur input dan 1 label/output)

### Kondisi Data

| Kondisi               | Deskripsi                                                                 | Gambar                                                                                                                                   |
|-----------------------|---------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Missing Value**      | Tidak ada nilai null, namun terdapat nilai 0 pada kolom yang seharusnya tidak bernilai nol seperti `BMI`, `Glucose`, `Insulin`, `BloodPressure`, dan `SkinThickness`.     | ![Image](https://github.com/user-attachments/assets/062ec92d-6d35-4533-b3b9-b4f0e93c4abd) ![Image](https://github.com/user-attachments/assets/cdbe68b2-f86f-4a6b-b4ab-dd00d33c86a7)                                                                                     |
| **Duplikat**           | Tidak ada duplikasi dalam dataset.                                        | ![Image](https://github.com/user-attachments/assets/96add838-7575-4beb-a4ba-ae527ee704ca)                                                                                           |
| **Outlier**            | Adanya outlier pada beberapa fitur numerik setelah mengganti nilai 0 di masing-masing kolom dengan rata-rata kolom tersebut, seperti nilai ekstrem pada Pregnancies, Age, Insulin, dan lain-lain.    | ![Image](https://github.com/user-attachments/assets/f872b75a-d425-4f5b-b07f-44d3258f1f43)                                                                                        |
| **Korelasi**            | Dalam dataset ini, korelasi antar fitur-fitur  memiliki hubungan yang kuat.     | ![Image](https://github.com/user-attachments/assets/53f4a221-47c6-4e03-82b2-9c0cc3c78780)                                                                                     |

---

## Data Preparation
- Mengecek Data (Missing Values dan Duplikasi)
- Mengisi nilai nol pada kolom medis seperti glucose, blood pressure, dll dengan nilai rata-rata.
- Penghapusan Outlier
- Memisahkan data menjadi fitur (X) dan target (y).
- Membagi data menjadi data latih dan data uji (80:20).
- Melakukan normalisasi agar semua fitur berada dalam skala yang sama.

## Modeling

Model dikembangkan menggunakan 5 algoritma machine learning populer yaitu:

### 🔹 1. Logistic Regression
- **Cara Kerja:** Menghitung probabilitas kelas dengan fungsi sigmoid yang menghasilkan nilai antara 0 dan 1. Model ini melakukan prediksi berdasarkan seberapa besar kemungkinan sebuah data masuk ke dalam kelas tertentu.
- **Parameter:** Default dari `sklearn`.

---

### 🔹 2. K-Nearest Neighbors (KNN)
- **Cara Kerja:** Algoritma ini bekerja dengan mengklasifikasikan sampel baru berdasarkan mayoritas label dari k tetangga terdekat.
- **Parameter:** Default dari `sklearn`. 

---

### 🔹 3. Decision Tree
- **Cara Kerja:** Membuat struktur pohon berdasarkan pemisahan fitur menggunakan kriteria (Gini atau Entropy).
- **Parameter:** Default dari `sklearn`.

---

### 🔹 4. Random Forest
- **Cara Kerja:** Menggabungkan banyak pohon keputusan dan melakukan voting mayoritas.
- **Parameter:** Default dari `sklearn`.

---

### 🔹 5. Support Vector Machine (SVM)
- **Cara Kerja:** Algoritma ini bekerja dengan mencari hyperplane optimal yang memisahkan 2 kelas.
- **Parameter:** Default dari `sklearn`.


---


## Evaluation

Pada tahap evaluasi, metrik yang digunakan untuk menilai performa model secara keseluruhan meliputi:

- **Confusion Matrix**: Digunakan untuk menganalisis kesalahan klasifikasi dengan cara menunjukkan jumlah prediksi yang benar dan salah berdasarkan kelas yang sebenarnya. 

- **Classification Report**: Menyediakan metrik penting seperti precision, recall, F1-score, dan akurasi untuk setiap kelas dalam model. 

- **Accuracy Score**: Mengukur seberapa sering model melakukan prediksi yang benar dibandingkan dengan total prediksi. 

- **Visualisasi Akurasi Model**: Untuk membandingkan akurasi dari berbagai model secara grafis. 

### Hasil Evaluasi:
Hasil evaluasi lima model yang diuji dan dibandingkan performanya, yaitu:

#### 1. Model 1: Logistic Regression

| Confusion Matrix | Classification Report |
|------------------|------------------------|
| ![Image](https://github.com/user-attachments/assets/b7fdb161-89d4-4468-acdd-56d79f517555) | ![Image](https://github.com/user-attachments/assets/0aef32ab-9a87-45f5-94d2-e6ef8066b0a8) |

Confusion Matrix menunjukkan bahwa model berhasil mengklasifikasikan 83 pasien non-diabetes dan 27 pasien diabetes dengan benar, sementara terdapat 9 kasus false positive (prediksi diabetes padahal tidak) dan 16 kasus false negative (tidak terdeteksi sebagai diabetes padahal sebenarnya positif). Sementara itu dari hasil Classification Report, model memiliki akurasi keseluruhan sebesar 81%, dengan precision 84% dan recall 90% untuk kelas non-diabetes (0), serta precision 75% dan recall 63% untuk kelas diabetes (1). Ini menunjukkan bahwa model cukup baik dalam mengenali pasien non-diabetes, namun masih memiliki kelemahan dalam mendeteksi pasien yang benar-benar menderita diabetes, yang terlihat dari recall yang lebih rendah pada kelas 1.

---

#### 2. Model 2: Decision Tree

| Confusion Matrix | Classification Report |
|------------------|------------------------|
| ![Image](https://github.com/user-attachments/assets/ec2d35c9-889b-4041-8db4-f7e5428a8146) | ![Image](https://github.com/user-attachments/assets/0635441e-e933-4302-9a66-adf54731a4cc) |

Model Decision Tree menghasilkan performa yang cenderung seimbang namun belum optimal, terutama dalam mendeteksi kasus diabetes. Confusion matrix menunjukkan bahwa dari 92 pasien non-diabetes, 76 berhasil diprediksi dengan benar, sementara 16 salah diklasifikasikan sebagai penderita diabetes. Di sisi lain, dari 43 pasien yang benar-benar mengidap diabetes, hanya 23 yang terdeteksi dengan benar, sedangkan 20 lainnya tidak terdeteksi oleh model. Hal ini mencerminkan ketidakseimbangan dalam kemampuan model mengenali kelas positif. Hasil classification report memperkuat hal tersebut, dengan precision kelas 1 (positif diabetes) hanya 0.59 dan recall sebesar 0.53. Meskipun akurasi keseluruhan sebesar 73% terdengar cukup baik, nilai recall yang rendah pada kelas positif menunjukkan bahwa model ini masih kurang sensitif terhadap pasien yang benar-benar memiliki diabetes.

---

#### 3. Model 3: Random Forest

| Confusion Matrix | Classification Report |
|------------------|------------------------|
| ![Image](https://github.com/user-attachments/assets/16ce6470-ad0e-493f-935a-39daf8c45b40) | ![Image](https://github.com/user-attachments/assets/827b8d6d-a4b5-4ebb-a654-c1a4593d89ff) |

Model Random Forest menunjukkan bahwa dari 92 pasien yang sebenarnya tidak menderita diabetes (kelas 0), sebanyak 79 pasien berhasil diklasifikasikan dengan benar, sementara 13 pasien keliru diklasifikasikan sebagai positif diabetes. Untuk kelas 1 (sebenarnya menderita diabetes), dari 43 pasien, model berhasil memprediksi 27 pasien dengan benar, dan 16 sisanya salah diklasifikasikan sebagai non-diabetes.

Dalam Classification Report, kita bisa lihat bahwa model ini memiliki akurasi keseluruhan sebesar 79%, yang berarti 79% dari seluruh prediksi cocok dengan label sebenarnya. Untuk kelas 0, nilai precision 0.83 dan recall 0.86 mengindikasikan bahwa model cukup baik dalam mengidentifikasi pasien non-diabetes. Namun, untuk kelas 1, precision-nya 0.68 dan recall 0.63, menunjukkan bahwa performa model dalam mengenali pasien yang benar-benar menderita diabetes masih kurang baik.

---

#### 4. Model 4: Support Vector Machine (SVM)

| Confusion Matrix | Classification Report |
|------------------|------------------------|
| ![Image](https://github.com/user-attachments/assets/d5690b91-e735-4b08-84ae-c3b57b1f18a6) | ![Image](https://github.com/user-attachments/assets/52ee2873-66a3-4a7c-9cfc-e2f65f18e3f9) |

Model Support Vector Machine (SVM) ini menunjukkan bahwa model sangat baik dalam mengenali pasien yang tidak menderita diabetes (kelas 0) — sebanyak 85 dari 92 pasien berhasil diprediksi dengan benar, hanya 8 yang salah diklasifikasikan. Namun, untuk pasien yang menderita diabetes (kelas 1), performa model masih kurang optimal, hanya 16 dari 43 yang terdeteksi dengan tepat, dan sebanyak 27 pasien salah diprediksi sebagai non-diabetes.

Dari laporan klasifikasinya, terlihat bahwa meskipun precision untuk kelas 1 adalah 0.67, recall-nya hanya 0.37, artinya banyak pasien diabetes yang tidak terdeteksi. Ini berkontribusi terhadap f1-score kelas 1 yang rendah, yaitu 0.48. Secara keseluruhan, model memperoleh akurasi sebesar 74%, namun distribusi kinerja antar kelas kurang seimbang.

---

#### 5. Model 5: K-Nearest Neighbors (KNN)

| Confusion Matrix | Classification Report |
|------------------|------------------------|
| ![Image](https://github.com/user-attachments/assets/ecd02731-ab1a-43d6-a65c-e8e53ede1fe4) | ![Image](https://github.com/user-attachments/assets/6f65f995-ee01-4af2-af5f-2eb4a9de4ef6) |

Confusion Matrix dari model K-Nearest Neighbors (KNN) menunjukkan bahwa model berhasil mengklasifikasikan 80 pasien non-diabetes dan 25 pasien diabetes dengan benar, namun terdapat 12 kasus false positive (pasien diprediksi diabetes padahal tidak) dan 18 kasus false negative (pasien tidak terdeteksi diabetes padahal sebenarnya positif). Berdasarkan Classification Report, model ini memiliki akurasi sebesar 78%. Untuk kelas non-diabetes (0), precision-nya 82% dan recall-nya 87%, menunjukkan bahwa model cukup handal dalam mendeteksi pasien yang tidak memiliki diabetes. Namun, performa pada kelas diabetes (1) masih kurang optimal, dengan precision 68% dan recall 58%, yang mengindikasikan model masih cukup sering salah mendeteksi pasien yang seharusnya positif diabetes. Secara keseluruhan, performa KNN sedikit di bawah Logistic Regression, terutama dalam mengenali kasus diabetes.

---

### Perbandingan Model 

![Image](https://github.com/user-attachments/assets/d2049815-8e4f-47a6-93d5-6844cc990e0e)

Grafik di atas menunjukkan bahwa Logistic Regression menjadi kandidat model terbaik secara akurasi, diikuti oleh Random Forest dan KNN.

Model seperti SVM dan Decision Tree masih menghadapi masalah dalam menangani kelas minoritas (pasien diabetes), meskipun mereka bekerja cukup baik pada kelas mayoritas.

---

## Kesimpulan
Dari hasil evaluasi lima model machine learning untuk memprediksi risiko diabetes berdasarkan dataset Pima Indians Diabetes, dapat disimpulkan bahwa masing-masing model memiliki kelebihan dan kekurangannya sendiri dalam mendeteksi pasien dengan diabetes. Model seperti Logistic Regression dan Random Forest menunjukkan performa yang cukup baik dalam hal akurasi dan precision, khususnya untuk mendeteksi pasien non-diabetes. Namun, performa recall terhadap kelas diabetes masih perlu ditingkatkan agar dapat digunakan secara efektif untuk deteksi dini.

Sebagian besar tujuan yang ditetapkan dalam tahap Business Understanding telah berhasil dicapai, seperti membandingkan performa antar model dan memahami perilaku masing-masing algoritma terhadap data. Namun demikian, goal utama yaitu deteksi dini pasien diabetes belum sepenuhnya tercapai, mengingat beberapa model seperti SVM dan KNN menunjukkan recall yang rendah terhadap pasien diabetes, yang justru merupakan target utama dalam konteks prediksi risiko.

Secara keseluruhan, solusi yang diterapkan telah memberikan dampak positif dalam membantu proses pemilihan model yang paling tepat untuk kasus ini. Meski demikian, hasil ini juga membuka ruang untuk peningkatan lebih lanjut.

---

> *Laporan ini dibuat sebagai bagian dari tugas proyek Machine Learning.*
