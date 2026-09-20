# Mahasense (CUKIMAI)

## 1. Tajuk Projek & Ringkasan
**Mahasense (CUKIMAI - Konsultasi Mahasiswa dengan AI)**
Mahasense adalah satu aplikasi berasaskan kecerdasan buatan (AI) yang berfungsi sebagai medium perundingan khusus untuk pelajar dan mahasiswa. Melalui penggunaan Pemprosesan Bahasa Asli (NLP) dan integrasi LLM (Large Language Model), sistem berupaya mengenal pasti kategori masalah, menilai tahap keseriusan, serta mencadangkan solusi berserta 'To-Do List' yang praktikal.

## 2. Teknologi yang Digunakan (Tech Stack)
- **Frontend**: Streamlit (Framework Web Python)
- **Backend**: Python 3, Pandas, Scikit-Learn
- **Model Pembelajaran Mesin**: TF-IDF Vectorizer, Logistic Regression (untuk klasifikasi berbilang output)
- **Kecerdasan Buatan (LLM)**: Groq API (`groq_client.py`) untuk menjana solusi berstruktur berdasarkan masalah pelajar.

## 3. Ciri-Ciri Utama & Logik Perniagaan
- **Klasifikasi Masalah Automatik**: Model AI dapat mengenal pasti:
  1. Kategori Utama (Contoh: Akademik, Kewangan, dll).
  2. Kategori Pendukung.
  3. Tahap Masalah (Severity level).
- **Penjanaan Solusi Berstruktur**: Menggunakan keupayaan Groq LLM untuk menyusun satu jawapan bermakna berserta senarai tugasan (To-Do List) sebagai penyelesaian.
- **Latihan Model Kendiri**: Terdapat modul skrip untuk melatih semula model klasifikasi teks berasaskan set data CSV.

## 4. Struktur Direktori Projek
- `app.py`: Titik mula (entry point) utama untuk antara muka pengguna berasaskan web Streamlit dan aliran logik aplikasi.
- `train_model.py` / `auto_train.py`: Skrip untuk membersihkan teks, menghasilkan ciri (TF-IDF), melatih model (Logistic Regression), dan menyimpannya (sebagai `pkl`).
- `groq_client.py`: Modul penghubung klien untuk berinteraksi dengan API Groq LLM bagi tujuan penjanaan teks respon.
- `*.pkl`: Fail model terlatih (seperti `model_utama.pkl`, `vectorizer.pkl`, `encoder.pkl`).
- `dataset.csv`: Repositori data rawatan bagi latihan algoritma pemisah teks masalah pelajar.

## 5. Panduan Pemasangan & Cara Menjalankan Projek
Untuk menjalankan aplikasi analitik AI ini pada pelayan tempatan:

1. **Sediakan Persekitaran Virtual Python (Virtual Environment)** (Disyorkan):
   ```bash
   python -m venv venv
   # Di Windows:
   venv\Scripts\activate
   ```
2. **Pasang Dependensi Python**:
   Pasang pustaka asas berikut (bergantung kepada keperluan skrip):
   ```bash
   pip install streamlit pandas scikit-learn groq
   ```
3. **Tetapkan Groq API Key**:
   Pastikan kunci API Groq diletakkan dalam environment anda (contoh: pembolehubah `GROQ_API_KEY`) atau dikonfigurasikan di dalam kod.
4. **Jalankan Aplikasi Web**:
   ```bash
   streamlit run app.py
   ```
   Aplikasi akan dimuatkan di pelayar web, biasanya pada alamat `http://localhost:8501`.

## 6. Endpoint API / Skema Pangkalan Data
- Tidak melibatkan pengkalan data tradisional/SQL (menggunakan model yang telah dilatih `.pkl` dan data `.csv`).
- Menggunakan endpoint integrasi API luaran untuk mengakses model pengolahan LLM menerusi API Groq.
