# Job-Market-Analysis using IBM Granite 3.3
# Project Overview
This project classifies jobs as:
- Sangat Menarik
- Layak Dipertimbangkan
- Kurang Menarik
Based on company rating & salary, powered by IBM Granite 3.3 (via Replicate).
# Dataset
- Source: Kaggle (https://www.kaggle.com/api/v1/datasets/download/princekhunt19/700-jobs-data-of-ai-and-data-fields-2025)
- Fields: positionName, salary, rating, company, etc.
# Insight and findings
Berdasarkan hasil klasifikasi terhadap 10 data pekerjaan menggunakan IBM Granite 3.3:
60% pekerjaan diklasifikasikan sebagai "Sangat Menarik"
    Umumnya berasal dari perusahaan dengan rating tinggi (≥4.2) dan gaji kompetitif, biasanya di atas $90.000. Posisi ini didominasi oleh perusahaan besar seperti Amazon dan AWS.
30% masuk dalam kategori "Layak Dipertimbangkan"
    Ditandai oleh gaji menengah ($60.000–$80.000) atau rating yang cukup baik (sekitar 3.8–4.1). Cocok untuk pelamar dengan toleransi terhadap sedikit kompromi, misalnya lokasi atau job scope.
10% diklasifikasikan sebagai "Kurang Menarik"
    Biasanya karena rating perusahaan rendah (<3.5), gaji tidak transparan, atau deskripsi pekerjaan tidak jelas. Ini menunjukkan potensi risiko atau ketidakjelasan dalam penawaran kerja.
# AI Support Explanation
Proyek ini menggunakan IBM Granite 3.3 – Instruct Model, yaitu model bahasa besar (Large Language Model / LLM) buatan IBM dengan 8 miliar parameter, yang diakses melalui Replicate API menggunakan pustaka langchain_community.
  - Prompt Engineering
      Setiap baris data pekerjaan diproses menjadi prompt berbahasa Indonesia yang menjelaskan posisi, gaji, rating, dan nama perusahaan. Contohnya:
Berdasarkan informasi berikut, berikan penilaian apakah pekerjaan ini termasuk:
- Sangat Menarik
- Layak Dipertimbangkan
- Kurang Menarik
Berikan alasan berdasarkan rating perusahaan dan gaji.
- Posisi: Data Scientist
- Perusahaan: Amazon
- Rating: 4.6
- Gaji: $120,000
  - Klasifikasi Otomatis oleh Granite 3.3
      Model memberikan output berupa deskripsi evaluatif, yang kemudian diekstraksi menjadi label seperti:
Sangat Menarik, Layak Dipertimbangkan, atau Kurang Menarik.
  - Pembersihan Hasil & Labeling
      Jawaban dari model diproses kembali agar dapat digunakan untuk visualisasi dan analisis. Jika model gagal merespons (contohnya karena error 429), label akan diberikan sebagai Error atau Tidak Terklasifikasi.
  - Analisis Insight & Visualisasi
      Label akhir digunakan untuk membuat pie chart dan bar chart, serta dianalisis untuk memahami distribusi daya tarik pekerjaan berdasarkan kriteria gaji dan rating.
