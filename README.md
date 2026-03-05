# 🏆 WorldCupPredict

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)

**WorldCupPredict** adalah proyek *Machine Learning* dan Analisis Data yang dirancang untuk memprediksi hasil pertandingan sepak bola selama turnamen Piala Dunia. Repositori ini menggunakan data historis pertandingan, statistik pemain, dan peringkat FIFA untuk membangun model prediksi yang akurat.

---

## ✨ Fitur Utama

* **Prediksi Hasil Pertandingan:** Menghitung probabilitas Menang, Kalah, atau Seri untuk setiap laga.
* **Prediksi Skor Akhir:** Estimasi skor akhir berdasarkan metrik penyerangan dan pertahanan historis kedua tim.
* **Visualisasi Data:** Grafik dan *dashboard* performa tim, riwayat *head-to-head*, dan tren peringkat FIFA.
* **Pembaruan Real-Time:** Mudah diintegrasikan dengan API skor langsung untuk memperbarui prediksi selama turnamen berlangsung.

---

## 🛠️ Teknologi yang Digunakan

* **Bahasa Pemrograman:** Python 3.8+
* **Manipulasi Data:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn
* **Visualisasi:** Matplotlib, Seaborn, Plotly
* **Lainnya:** Scrapy (untuk *scraping* data)

---

## 1. Executive Summary

### 1.1 Project Overview
* **Tujuan Project:** Mengembangkan model *machine learning* untuk memprediksi hasil pertandingan sepak bola Piala Dunia 2026 serta penyajian data pertandingan FIFA World Cup 1930 - 2022 secara ringkas dan terstruktur dalam bentuk statistik deskriptif dan visualisasi sederhana.
* **Scope Project:** Pengolahan dan penyajian data pertandingan Piala Dunia dan liga besar yang mencakup informasi umum dan detail informasi seperti kapten tuan rumah, jumlah kartu merah, dll.
* **Expected Outcomes:** Prediksi hasil pertandingan dan ringkasan statistik utama, tabel dan grafik sederhana untuk visualisasi data, dokumentasi analisis data, dan *blueprint* pemanfaatan dataset.
* **Timeline:** 3 bulan (Februari - Mei 2026)

### 1.2 Stakeholders
* **Project Owner:** PT Rajawali Citra Televisi Indonesia (RCTI)
* **Team Members:**
  * Data Engineer: Muhammad Rosyid
  * Data Engineer: Muhammad Afif
  * Data Analyst: Erlangga Deanda CS
  * Project Manager: Alvina Nur
* **End Users:**
  * Tim Kreatif
  * Pengamat Sepak Bola

---

## 2. 📊 Data Source Analysis

Dokumen ini berisi rincian analisis sumber data yang digunakan dalam proyek **WorldCupPredict**. Data dikumpulkan dari berbagai sumber terpercaya untuk memastikan akurasi dan keandalan model prediksi.

### 2.1 Data Instansi (FIFA)
**Source Details:**
* **Dataset Name:** FIFA/Coca-Cola World Rankings
* **URL/Access Point:** [https://www.fifa.com/en/world-rankings](https://www.fifa.com/en/world-rankings)
* **Data Owner:** FIFA (Fédération Internationale de Football Association)
* **Update Frequency:** Bulanan

**Data Analysis:**
* **Format Data:** HTML
* **Volume Data:** 3 MB hingga 8 MB
* **Time Coverage:** 2018 - Sekarang
* **Data Quality:**
  * **Completeness:** 100%
  * **Accuracy:** *Very High* (diambil langsung dari website resmi)
  * **Consistency:** *Good* (format terstruktur)
  * **Timeliness:** Umumnya diperbarui setiap bulan. Frekuensi pembaruan ini sangat sinkron dengan kalender FIFA Matchday atau turnamen besar.

### 2.2 Dataset Kaggle
**Source Details:**
* **Dataset Name:** Football - FIFA World Cup, 1930 - 2022
* **URL/Access Point:** [Kaggle Dataset](https://www.kaggle.com/) *(Pencarian di Kaggle)*
* **Creator/Publisher:** Petro Ivaniuk
* **Last Update:** 2023

**Data Analysis:**
* **Format Data:** CSV
* **Size & Dimensions:** 174 KB
* **Data Fields:** Berisi informasi detail historis pertandingan Piala Dunia.
* **Quality Metrics:**
  * **Missing Values:** Null
  * **Data Types:** String, Integer, Float
  * **Consistency:** *High*
  * **Documentation Quality:** *High*

### 2.3 Public APIs
**Source Details:**
* **API Name:** API-Football
* **Endpoint URL:** [https://v3.football.api-sports.io/](https://v3.football.api-sports.io/)
* **Provider:** API-SPORTS
* **Authentication Method:** API Key melalui HTTP Headers

**API Analysis:**
* **Response Format:** JSON (JavaScript Object Notation)
* **Rate Limits:** Paket Gratis (*Free*) dibatasi maksimal 100 *request* per hari dan tidak boleh lebih dari 10 *request* per menit.
* **Reliability:** Sangat tinggi. Layanan ini dirancang untuk produksi skala besar dengan pembaruan data *livescore* setiap 15 detik.
* **Documentation Quality:** Sangat baik dan komprehensif.
* **Cost:** Menggunakan model *Freemium*.

### 2.4 Open Research Data
**Source Details:**
* **Dataset Name:** StatsBomb Open Data
* **Repository:** [https://github.com/statsbomb/open-data](https://github.com/statsbomb/open-data)
* **Research Institution:** StatsBomb (Perusahaan Analitik Data Olahraga yang secara resmi membuka sebagian database komersial mereka untuk tujuan riset akademik dan proyek portofolio *data science*).
* **Publication Date:** Pembaruan berkelanjutan (*Continuous Update*). Data Piala Dunia 2022 dirilis secara publik pada awal tahun 2023, sementara data liga historis ditambahkan secara berkala.

**Data Analysis:**
* **Format & Structure:** Terutama menggunakan format `.json` bersarang (*nested JSON*). Data dibagi menjadi tiga struktur hierarki utama: `competitions.json` (daftar liga/turnamen), `matches.json` (metadata pertandingan), dan `events.json`.
* **Data Volume:** Relatif besar untuk ukuran teks (ratusan Megabyte hingga lebih dari 1 Gigabyte).
* **Data Quality:** Kualitas *Enterprise* (Sangat Tinggi).
* **Citation Requirements:** * **Atribusi Terbuka:** Menggunakan lisensi khusus untuk penggunaan non-komersial dan riset. 
  * Peneliti atau *developer* diwajibkan mencantumkan teks pengakuan (*acknowledgement*) berbunyi: **"Data provided by StatsBomb"**. 
  * Jika data ini diubah menjadi antarmuka visual, pengguna diwajibkan untuk menyertakan logo StatsBomb di dalam grafik visual tersebut.

---

## 3. Data Flow Mapping

### 3.1 Data Integration Architecture
*(Catatan: Diagram ini telah disesuaikan agar alirannya selaras dengan sumber data yang Anda analisis di atas)*

```mermaid
graph TD
    A[FIFA World Rankings] --> D[Data Lake / Raw Data]
    B[Kaggle Dataset CSV] --> D
    C[API-Football JSON] --> D
    H[StatsBomb Open Data JSON] --> D
    D --> E[Data Warehouse / Processed Data]
    E --> F[Analytics & Machine Learning Layer]
    F --> G[Dashboard & Predictions]
