# 🎓 AI Academic Assistant: Layanan Informasi Tugas Akhir (n8n Workflow)

[![n8n](https://img.shields.io/badge/n8n-Workflow-orange)](https://n8n.io/)
[![Model-GPT4o--mini-blue](https://img.shields.io/badge/AI-GPT--4o--mini-blue)](https://openai.com/)
[![Model-Gemini--Flash-green](https://img.shields.io/badge/OCR-Gemini--Flash-green)](https://deepmind.google/technologies/gemini/)

Workflow ini adalah solusi otomasi administrasi Tugas Akhir (TA) yang mengintegrasikan **Telegram Bot**, **AI OCR**, dan **RAG (Retrieval-Augmented Generation)**. Dirancang khusus untuk membantu Program Studi dalam mengelola data mahasiswa dan menjawab pertanyaan akademik secara otomatis.

---

## 🌟 Fitur Utama

### 1. 📂 Registrasi Dokumen via OCR
Mahasiswa dapat mengirimkan foto formulir (Pendaftaran Sempro, BAP, Undangan, dll). Workflow akan:
* Mengekstrak data secara otomatis menggunakan **Gemini 2.0 Flash**.
* Memvalidasi kelayakan gambar.
* Menyimpan data terstruktur langsung ke **Google Sheets**.

### 2. 🤖 Asisten Tanya Jawab (RAG)
Menjawab pertanyaan seputar regulasi TA (misal: syarat sidang, aturan revisi) berdasarkan dokumen PDF panduan resmi yang tersimpan di **Supabase Vector Store**. Jawaban dijamin akurat karena berbasis data (*grounded on facts*).

### 3. 🔍 Cek Status Real-Time
Cukup dengan perintah `/cekstatus`, mahasiswa akan mendapatkan ringkasan progres TA mereka yang diambil langsung dari database spreadsheet.

### 4. 🧠 Conversational Memory
Menggunakan **Postgres Chat Memory** sehingga bot dapat mengingat konteks percakapan sebelumnya untuk pengalaman interaksi yang lebih manusiawi.

---

## 🏗️ Arsitektur Sistem

Workflow ini terdiri dari beberapa jalur logika utama:
1.  **Entry Point**: Telegram Trigger memilah pesan (Text, Image, atau Command).
2.  **Processing Path**: Analisa gambar biner menjadi JSON terstruktur.
3.  **Knowledge Path**: Penarikan konteks dari Vector Store untuk menjawab query user.
4.  **Logging**: Pencatatan riwayat chat ke Google Sheets untuk audit admin.

---

## 🛠️ Persyaratan & Instalasi

### 🔑 Kredensial yang Diperlukan:
* **Telegram Bot API**: Sebagai interface pengguna.
* **OpenAI API**: Untuk AI Agent & Embedding model.
* **Gemini API**: Digunakan pada node HTTP Request untuk proses OCR.
* **Google Cloud**: Akses ke Google Sheets (Database) & Drive (Knowledge Base).
* **Supabase**: Sebagai Vector Database.
* **Postgres**: Untuk database memori chat.

### 🚀 Cara Penggunaan:
1.  **Import**: Masukkan file `Workflow_Utama.json` ke dashboard n8n Anda.
2.  **Setup Sheets**: Siapkan Google Sheets dengan kolom sesuai kebutuhan (Nama, NIM, Status, dll).
3.  **Setup Supabase**: Pastikan tabel vektor sudah terkonfigurasi.
4.  **Konfigurasi Node**: Update ID Spreadsheet dan ID Folder Drive pada masing-masing node terkait.
5.  **Aktifkan**: Tekan tombol **Execute** untuk testing, lalu **Activate**.

---

## 📊 Manfaat bagi Admin Prodi
* **Efisiensi Waktu**: Mengurangi tanya jawab repetitif dengan mahasiswa.
* **Digitalisasi Otomatis**: Formulir fisik langsung masuk ke database digital tanpa input manual.
* **Transparansi**: Mahasiswa mendapatkan informasi status administrasi secara mandiri dan cepat.

---
*Dibuat oleh [Nama Anda/Prodi Anda]. Terinspirasi dari kebutuhan administrasi Program Studi Sains Data ITERA.*
