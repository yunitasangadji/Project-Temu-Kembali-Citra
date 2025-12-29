# Project-Temu-Kembali-Citra

## 📑 Table of Contents
1. [Deskripsi Proyek](#deskripsi-proyek)  
2. [Tujuan Penelitian](#tujuan-penelitian)  
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

📘 Deskripsi Proyek

Proyek ini mengembangkan sistem Retrieval-Augmented Generation (RAG) berbasis citra dengan memanfaatkan CLIP (Contrastive Language–Image Pretraining) sebagai visual encoder dan Flan-T5 Base sebagai text generator. Sistem ini dirancang untuk melakukan pencarian gambar berbasis kemiripan visual sekaligus menghasilkan deskripsi teks yang relevan berdasarkan hasil retrieval.

🎯 Tujuan Penelitian

Mengembangkan sistem RAG berbasis citra

Mengimplementasikan CLIP untuk ekstraksi fitur visual

Menggunakan FAISS untuk pencarian vektor secara efisien

Menghasilkan deskripsi gambar yang informatif menggunakan Flan-T5

🧠 Arsitektur Sistem

Sistem terdiri dari beberapa tahap utama:

Image Encoding
Menggunakan CLIP (ViT-B/32) untuk menghasilkan embedding 512 dimensi.

Vector Indexing & Retrieval
Embedding disimpan dalam FAISS dan digunakan untuk pencarian berbasis similarity.

Re-ranking
Mengurutkan ulang hasil pencarian berdasarkan skor kemiripan tertinggi.

Text Generation
Caption dari hasil retrieval digunakan sebagai konteks bagi Flan-T5.

📂 Dataset
Flickr30k Dataset

Dataset Flickr30k terdiri dari ±30.000 gambar, masing-masing disertai 5 deskripsi teks yang dibuat oleh manusia. Dataset ini mencakup berbagai aktivitas manusia, interaksi objek, dan konteks visual.

Digunakan untuk:

Image Retrieval

Image Captioning

Multimodal Learning

🔗 Dataset: https://www.kaggle.com/datasets/eeshawn/flickr30k

🔍 Metodologi
Image Retrieval

Ekstraksi embedding menggunakan CLIP

Normalisasi vektor (L2)

Pencarian berbasis FAISS

Evaluasi menggunakan Recall@K dan mAP

Generative Stage

Caption hasil retrieval dijadikan konteks

Flan-T5 menghasilkan deskripsi teks

Evaluasi menggunakan BLEU dan ROUGE

📊 Evaluasi
Evaluasi Retrieval

Recall@5 dan Recall@10 menunjukkan performa tinggi

Sistem mampu menemukan gambar relevan secara konsisten

Evaluasi Generatif

Teks yang dihasilkan koheren dan informatif

Relevan dengan konteks visual gambar

📈 Hasil dan Pembahasan

CLIP efektif menangkap kesamaan visual dan semantik

RAG meningkatkan kualitas deskripsi dibanding metode generatif murni

Sistem stabil pada berbagai jenis citra

Kinerja menurun pada citra dengan konteks sangat kompleks

⚙️ Analisis Waktu dan Penyimpanan

FAISS memungkinkan pencarian cepat (milidetik)

Embedding disimpan sebagai vektor 512 dimensi

Proses inferensi efisien dan scalable

🧩 Kesimpulan

Sistem Image-Based Retrieval-Augmented Generation (RAG) berhasil dikembangkan dengan mengintegrasikan CLIP, FAISS, dan Flan-T5. Sistem ini mampu melakukan pencarian gambar secara efektif dan menghasilkan deskripsi teks yang informatif serta kontekstual. Pendekatan ini sangat potensial untuk aplikasi di bidang computer vision dan multimodal AI.
