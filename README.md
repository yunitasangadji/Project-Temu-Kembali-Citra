<h1 align="center">Project - Temu Kembali Citra</h1>

<p align="center">
  Perancangan Sistem Retrieval-Augmented Generation (RAG)<br>
  Berbasis Citra Menggunakan CLIP dan Model Flan T5 Base pada flickr30k
</p>

<h2 align="center">Nama Kelompok</h2>

<table align="center">
  <tr>
    <th>No</th>
    <th>Nama Lengkap</th>
    <th>NIM</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Wulan Nuri Rahmawati</td>
    <td>202210370311315</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Yunita Sangadji</td>
    <td>202210370311332</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Nurlisa Safi</td>
    <td>202210370311337</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Annisaa Salsabila Shafiyyah Fitriyani</td>
    <td>202210370311352</td>
  </tr>
</table>


## 📑 Table of Contents
1. [Deskripsi Project](#deskripsi-project)  
2. [Tujuan ](#tujuan)  
3. [Arsitektur Sistem](#arsitektur-sistem)  
4. [Dataset](#dataset)  
   - [Flickr30k Dataset](#flickr30k-dataset)  
5. [Metodologi](#metodologi)  
   - [Image Retrieval](#image-retrieval)  
   - [Generative Stage](#generative-stage)  
6. [Evaluasi](#evaluasi)  
   - [Evaluasi Retrieval](#evaluasi-retrieval)  
   - [Evaluasi Generatif](#evaluasi-generatif)  
7. [Hasil dan Pembahasan](#hasil-dan-pembahasan)  
8. [Analisis Waktu dan Penyimpanan](#analisis-waktu-dan-penyimpanan)  
9. [Kesimpulan](#kesimpulan)  

## Deskripsi Project

Proyek ini mengembangkan sistem Retrieval-Augmented Generation (RAG) berbasis citra dengan memanfaatkan CLIP (Contrastive Language–Image Pretraining) sebagai visual encoder dan Flan-T5 Base sebagai text generator. Sistem ini dirancang untuk melakukan pencarian gambar berbasis kemiripan visual sekaligus menghasilkan deskripsi teks yang relevan berdasarkan hasil retrieval.

## Tujuan 
- Mengembangkan sistem RAG berbasis citra
- Mengimplementasikan CLIP untuk ekstraksi fitur visual
- Menggunakan FAISS untuk pencarian vektor secara efisien
- Menghasilkan deskripsi gambar yang informatif menggunakan Flan-T5

## Arsitektur Sistem
Sistem terdiri dari beberapa tahap utama:
- Image Encoding
  Menggunakan CLIP (ViT-B/32) untuk menghasilkan embedding 512 dimensi.
- Vector Indexing & Retrieval
  Embedding disimpan dalam FAISS dan digunakan untuk pencarian berbasis similarity.
- Re-ranking
  Mengurutkan ulang hasil pencarian berdasarkan skor kemiripan tertinggi.
- Text Generation
- Caption dari hasil retrieval digunakan sebagai konteks bagi Flan-T5.

## Dataset
### Flickr30k Dataset
Dataset Flickr30k terdiri dari ±30.000 gambar, masing-masing disertai 5 deskripsi teks yang dibuat oleh manusia. Dataset ini mencakup berbagai aktivitas manusia, interaksi objek, dan konteks visual.
   - Image Retrieval
   - Image Captioning
   - Multimodal Learning
     
🔗 Dataset: https://www.kaggle.com/datasets/eeshawn/flickr30k

## Metodologi
### Image Retrieval
- Ekstraksi embedding menggunakan CLIP
- Normalisasi vektor (L2)
- Pencarian berbasis FAISS
- Evaluasi menggunakan Recall@K dan mAP

### Generative Stage
- Caption hasil retrieval dijadikan konteks
- Flan-T5 menghasilkan deskripsi teks
- Evaluasi menggunakan BLEU dan ROUGE
  
Sistem menggunakan pendekatan Retrieval-Augmented Generation (RAG) yang terdiri dari dua tahap utama. Pada tahap image retrieval, embedding visual diekstraksi menggunakan CLIP dan dinormalisasi dengan L2 normalization, kemudian dilakukan pencarian berbasis FAISS. Evaluasi tahap ini dilakukan menggunakan metrik Recall@K. Pada tahap generative, hasil retrieval digunakan sebagai konteks untuk menghasilkan deskripsi teks menggunakan model Flan-T5. Kualitas teks dievaluasi menggunakan metrik BLEU dan ROUGE untuk mengukur kesesuaian semantik dan kelancaran bahasa.

## Evaluasi
### Evaluasi Retrieval
Evaluasi dilakukan menggunakan metrik Recall@K untuk mengukur kemampuan sistem dalam menemukan gambar yang relevan terhadap query yang diberikan. Hasil evaluasi menunjukkan bahwa nilai Recall@5 dan Recall@10 cukup tinggi, menandakan bahwa sistem mampu menempatkan gambar yang relevan pada posisi teratas hasil pencarian. Hal ini membuktikan bahwa penggunaan CLIP sebagai ekstraktor fitur visual dan FAISS sebagai mesin pencari vektor bekerja secara efektif dalam menangkap kesamaan visual antar gambar.
### Evaluasi Generatif
Pada tahap generatif, kualitas deskripsi teks dievaluasi berdasarkan tingkat koherensi, relevansi, dan kesesuaian dengan konten visual. Hasil menunjukkan bahwa teks yang dihasilkan oleh model Flan-T5 bersifat informatif, kontekstual, dan selaras dengan isi gambar. Hal ini menunjukkan bahwa integrasi hasil retrieval sebagai konteks mampu meningkatkan kualitas generasi teks dibandingkan pendekatan generatif tanpa retrieval.

## Hasil dan Pembahasan
Model CLIP mampu menangkap kesamaan visual dan semantik dengan baik. Pendekatan RAG meningkatkan kualitas deskripsi dibanding metode generatif biasa. Sistem bekerja stabil pada berbagai jenis citra, namun performa menurun pada gambar dengan konteks visual yang sangat kompleks.

## Analisis Waktu dan Penyimpanan
- FAISS memungkinkan pencarian cepat (milidetik)
- Embedding disimpan sebagai vektor 512 dimensi
- Proses inferensi efisien dan scalable

## Kesimpulan
Sistem Image-Based Retrieval-Augmented Generation (RAG) berhasil dikembangkan dengan mengintegrasikan CLIP, FAISS, dan Flan-T5. Sistem ini mampu melakukan pencarian gambar secara efektif dan menghasilkan deskripsi teks yang informatif serta kontekstual. Pendekatan ini sangat potensial untuk aplikasi di bidang computer vision dan multimodal AI.

Link Collab: https://colab.research.google.com/drive/1cS06fWKjaQoCqlrVmhwljmbh_q0I3R9c?usp=sharing#scrollTo=CmKNYr1ydd9f 
