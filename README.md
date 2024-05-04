# Analisis Sentimen Menggunakan Model BERT (*Bidirectional Encoder Representations from Transformers*)

Proyek ini merupakan proyek *Natural Language Processing* (NLP) pertama yang dibuat oleh penulis. Judul lengkap proyek ini yaitu "Analisis Sentimen Menggunakan Model BERT dan *Matthews Correlation Coefficient* (MCC) untuk Mengklasifikasi Review Film Berbahasa Indonesia".

## Deskripsi Proyek
Proyek ini bertujuan untuk mengembangkan sistem analisis sentimen yang dapat mengklasifikasikan review film berbahasa Indonesia menggunakan model BERT. Model BERT telah terbukti efektif dalam berbagai tugas pemrosesan bahasa alami karena penerapan transformers yang memungkinkan model mampu memahami konteks kata dalam kalimat. Dalam proyek ini, kami akan melatih model BERT yang telah disesuaikan dengan data berbahasa Indonesia untuk menilai apakah review film yang diberikan bersifat positif atau negatif.

## Tujuan
1. Mengimplementasikan model BERT yang telah pra-dilatih untuk tugas analisis sentimen khusus teks berbahasa Indonesia.
2. Menilai kinerja model menggunakan *Matthew Correlation Coefficient*, sebuah metrik yang mengukur kualitas klasifikasi biner.

## Datasets
Dataset yang akan digunakan adalah kumpulan review film dari Twitter yang berbahasa Indonesia. Dataset terdiri dari 200 dokumen tweet terkait opini pada film. Dataset ini diambil dari github rizalespe yang sebelumnya pernah dilakukan klasifikasi menggunakan algortima Naïve Bayes, berikut link nya :
https://github.com/rizalespe/Dataset-Sentimen-Analisis-Bahasa-Indonesia

## Data Preparation
Pada tahapan data preparation dilakukan beberapa langkah, diantaranya:
1. Anotasi Data/Labelisasi Data
   Proses anotasi data diberikan label "1" untuk sentimen positif dan "0" untuk sentimen negatif".
   ![labelisasi data](https://github.com/azkafauzi/analisis-sentimen-BERT/assets/62132378/38ab697c-90b4-4447-8e1c-c9a62a7ad6d7)
2. Pembersihan Data
   Pembersihan data yang dilakukan yaitu *lowercase* pada teks, menghilangkan *whitespace* dan menghilangkan simbol-simbol tertentu pada kolom text_tweet.

   ![data cleansing](https://github.com/azkafauzi/analisis-sentimen-BERT/assets/62132378/3211cc20-ae98-491f-bed4-8b646c414ebd)
4. Tokenisasi BERT
   Menggunakan BERTTokenizer pada packages transformers, Tokenizer yang digunakan yaitu IndoBERT
   ![bert tokenizer 1](https://github.com/azkafauzi/analisis-sentimen-BERT/assets/62132378/74d62e49-73cb-4069-97a7-06e62309b6a5)
   ![bert tokenizer 2](https://github.com/azkafauzi/analisis-sentimen-BERT/assets/62132378/b68a4228-ee4b-4677-8139-548e43a309e2)
   
## Pembuatan Model
Data dibagi kedalam data training dan data testing dengan perbandingan 80% data training, 20% data testing dan 50% data validation diambil dari data training.
### Model Configuration

| Parameter                          | Value        |
|------------------------------------|--------------|
| `output_attentions`                | `False`      |
| `output_hidden_states`             | `False`      |

### Training Configuration

| Parameter             | Value      |
|-----------------------|------------|
| `epochs`              | `5`        |
| `batch size`          | `32`        |

### Optimizer Configuration: AdamW

| Parameter             | Value                  |
|-----------------------|------------------------|
| `learning rate (lr)`  | `2e-5`                 |
| `epsilon (eps)`       | `1e-8`                 |
| `num_warmup_steps`    | `0`                    |

## Evaluasi Model
* Accuracy = 90%
  
  ![image](https://github.com/azkafauzi/analisis-sentimen-BERT/assets/62132378/fba0125a-d737-4de2-a276-d5c5bb5c4570)
  
* MCC (*Matthews Correlation Coefficient*) = 0.814

## Kesimpulan
Analisis sentimen menggunakan model Bidirectional Encoder Representations from Transformers (BERT) dengan optimasi AdamW mendapatkan akurasi Matthew Correlation Coefficient (MCC) sebesar 81%. Hal ini berarti performa model bagus karena menunjukkan bahwa model telah melakukan pekerjaan yang efektif dalam membedakan antara kelas-kelas yang ada dalam konteks analisis yang dilakukan. Model ini dapat dikembangkan dengan menambahkan datasets dan melakukan banyak percobaan dengan mengkonfigurasi ulang parameter-parameter saat membangun model.
