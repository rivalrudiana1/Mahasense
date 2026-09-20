# Mahasense

## 1. Judul Proyek & Ringkasan
**Mahasense (Consultation and Understanding og Campus Issues With Machine Learning and And Artificial Intelligence)**
Mahasense adalah sebuah aplikasi berbasis Artificial Intelligence (AI) yang berfungsi sebagai wadah konsultasi khusus untuk pelajar dan mahasiswa. Melalui penggunaan Natural Language Processing (NLP) dan integrasi LLM (Large Language Model), sistem mampu mengidentifikasi kategori masalah, menilai tingkat keseriusan, serta menyarankan solusi beserta 'To-Do List' yang praktis.

## 2. Teknologi yang Digunakan (Tech Stack)
- **Frontend**: Streamlit (Framework Web Python)
- **Backend**: Python 3, Pandas, Scikit-Learn
- **Model Machine Learning**: TF-IDF Vectorizer, Logistic Regression (untuk klasifikasi *multi-output*)
- **Artificial Intelligence (LLM)**: Groq API (`groq_client.py`) untuk men-*generate* solusi terstruktur berdasarkan masalah mahasiswa.

## 3. Fitur Utama & Logika Bisnis
- **Klasifikasi Masalah Otomatis**: Model AI dapat mengidentifikasi:
  1. Kategori Utama (Contoh: Akademik, Keuangan, dll).
  2. Kategori Pendukung.
  3. Tingkat Keparahan (Severity level).
- **Pembuatan Solusi Terstruktur**: Menggunakan kemampuan Groq LLM untuk merangkai jawaban bermakna beserta daftar tugas (To-Do List) sebagai penyelesaian.
- **Pelatihan Model Mandiri**: Terdapat modul *script* untuk melatih ulang model klasifikasi teks berbasis *dataset* CSV.

## 4. Struktur Direktori Proyek
- `app.py`: Titik masuk (*entry point*) utama untuk antarmuka pengguna berbasis web Streamlit dan alur logika aplikasi.
- `train_model.py` / `auto_train.py`: *Script* untuk membersihkan teks, membuat fitur (TF-IDF), melatih model (Logistic Regression), dan menyimpannya (sebagai `pkl`).
- `groq_client.py`: Modul penghubung klien untuk berinteraksi dengan API Groq LLM guna keperluan generasi teks respons.
- `*.pkl`: File model yang telah dilatih (seperti `model_utama.pkl`, `vectorizer.pkl`, `encoder.pkl`).
- `dataset.csv`: Repositori data mentah untuk pelatihan algoritma klasifikasi teks masalah mahasiswa.

## 5. Panduan Instalasi & Cara Menjalankan Proyek
Untuk menjalankan aplikasi analitik AI ini pada server lokal:

1. **Siapkan *Virtual Environment* Python** (Disarankan):
   ```bash
   python -m venv venv
   # Di Windows:
   venv\Scripts\activate
   ```
2. **Instal *Dependencies* Python**:
   Instal pustaka dasar berikut (tergantung pada kebutuhan *script*):
   ```bash
   pip install streamlit pandas scikit-learn groq
   ```
3. **Tetapkan Groq API Key**:
   Pastikan *API key* Groq diletakkan dalam *environment* Anda (contoh: variabel `GROQ_API_KEY`) atau dikonfigurasikan di dalam kode.
4. **Jalankan Aplikasi Web**:
   ```bash
   streamlit run app.py
   ```
   Aplikasi akan dimuat di peramban web, biasanya pada alamat `http://localhost:8501`.

## 6. Endpoint API / Skema Database
- Tidak melibatkan database tradisional/SQL (menggunakan model yang telah dilatih `.pkl` dan data `.csv`).
- Menggunakan endpoint integrasi API eksternal untuk mengakses model pemrosesan LLM melalui API Groq.
