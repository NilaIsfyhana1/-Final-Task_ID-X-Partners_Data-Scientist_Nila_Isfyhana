# Kredit Risk - Loan Default Prediction

## Project Overview

Proyek ini bertujuan untuk membangun model prediksi risiko gagal bayar pinjaman (loan default) yang dapat membantu lembaga keuangan dalam mengelola portofolio kredit secara lebih efisien. Dengan meningkatnya jumlah debitur, penting untuk dapat mengidentifikasi calon peminjam yang memiliki risiko tinggi terhadap gagal bayar sejak dini.

## Problem Statement

Kegagalan membayar pinjaman dapat berdampak signifikan terhadap stabilitas keuangan lembaga kredit. Tanpa sistem prediktif yang andal, sulit untuk mengklasifikasikan peminjam berdasarkan risiko mereka, yang pada akhirnya dapat menyebabkan peningkatan nilai Non-Performing Loan (NPL) dan kerugian finansial. Oleh karena itu, diperlukan solusi berbasis Machine Learning untuk memprediksi kemungkinan gagal bayar pinjaman dengan akurasi tinggi.

## Goals

* Mengembangkan model prediktif untuk mengklasifikasikan calon peminjam ke dalam kelompok "berisiko gagal bayar" dan "tidak berisiko gagal bayar".
* Meningkatkan akurasi pengambilan keputusan pemberian pinjaman.
* Mengurangi potensi kerugian akibat gagal bayar.
* Mengoptimalkan alokasi modal dan strategi mitigasi risiko.

## Data Sources

Dataset yang digunakan mencakup berbagai fitur terkait peminjam dan status pinjaman, antara lain:

* **Informasi Pekerjaan**: jabatan, pengalaman kerja.
* **Riwayat Kredit**: saldo saat ini, jumlah koleksi, saldo revolving credit.
* **Utilisasi Kredit**: revol\_util, total revolving high credit limit.
* **Tanggal Pembayaran Terakhir dan Tarikan Kredit Terakhir**: tanggal dan bulan.

## Analytic Approach

Beberapa model klasifikasi yang diuji dalam proyek ini meliputi:

* Logistic Regression
* Decision Tree
* Random Forest
* XGBoost (Model Terbaik)
* LightGBM
* Voting Classifier
* Stacking

Feature selection dilakukan untuk memilih fitur yang paling relevan terhadap risiko gagal bayar guna meningkatkan performa model.

## Model Evaluation

Metrik evaluasi yang digunakan:

* **Recall**: Fokus utama untuk memastikan model mendeteksi sebanyak mungkin calon peminjam yang berisiko gagal bayar.
* **Precision**: Untuk mengurangi false positive yang menyebabkan penolakan terhadap peminjam yang seharusnya layak.
* **F2-Score**: Digunakan karena memberikan bobot lebih pada recall.

Model dievaluasi menggunakan **confusion matrix**, **cross-validation**, dan **GridSearchCV** untuk tuning hyperparameter.

## Handling Imbalanced Data

Karena jumlah peminjam yang gagal bayar jauh lebih sedikit dibanding yang tidak, dilakukan penanganan imbalance data dengan:

* RandomOverSampler
* SMOTE
* Random UnderSampler
* Nearmiss 1

## Cost Simulation

Tanpa model:

* Jumlah nasabah yang benar-benar gagal bayar berdasarkan data historis: 50.207 orang
* Rata-rata kerugian per nasabah default (misalnya karena gagal ditagih): 1.000 USD
* Total Kerugian: 50.207 × 1.000 USD = 50.207.000 USD
* Total Penghematan: 0 USD


Dengan model:

* Biaya False Positive (FP) – kehilangan peluang keuntungan:Nasabah sebenarnya bisa membayar, tapi ditolak oleh model.
* Misal margin keuntungan yang hilang: 100 USD per nasabah
*  9 × 100 USD = 900 USD
* Biaya False Negative (FN) – gagal mendeteksi default:Nasabah yang gagal bayar tapi tidak terdeteksi oleh model.
* 19 × 1.000 USD = 19.000 USD
* Total Biaya dengan Model:900 USD (FP) + 19.000 USD (FN) = 28.000 USD



## How to Use

1. **Preprocessing Data**: Jalankan skrip preprocessing untuk membersihkan dan menyiapkan data.
2. **Training Model**: Gunakan pipeline yang telah dibuat untuk melatih model.
3. **Evaluasi Model**: Evaluasi performa model dengan confusion matrix dan metrik lainnya.
4. **Hyperparameter Tuning**: Optimasi parameter menggunakan GridSearch.
5. **Deployment**: Terapkan model ke dalam sistem kredit lembaga keuangan.

## Business Recommendations

### Modelling

* Evaluasi performa berdasarkan segmen risiko.
* Gunakan SHAP atau LIME untuk interpretasi fitur penting.
* Lakukan retraining model secara berkala.
* Gunakan skor risiko dinamis berbasis perilaku terbaru.

### Business

* Terapkan sistem early warning berbasis skor risiko.
* Sesuaikan suku bunga dan tenor berdasarkan profil risiko.
* Latih tim kredit dalam membaca hasil model.
* Otomatiskan proses kolektibilitas dan pengingat.
* Lakukan investigasi lebih lanjut terhadap FN (false negative).

## Conclusion

Dengan memanfaatkan machine learning, lembaga keuangan dapat memprediksi risiko gagal bayar dengan lebih efektif, sehingga meningkatkan kualitas kredit dan mengurangi potensi kerugian. Model yang dibangun terbukti mampu memberikan penghematan biaya yang signifikan dengan mendeteksi debitur berisiko lebih awal.
