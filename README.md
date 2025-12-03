# ✋🏻 SiLa – Sign Language Application

**SiLa** adalah aplikasi berbasis web untuk menerjemahkan bahasa isyarat secara **real-time** menggunakan kamera, serta menyediakan fitur **terjemahan video** untuk konten prarekaman. Dirancang dengan antarmuka pengguna yang responsif dan intuitif.

---

## 🚀 Fitur Utama

- 📱 **UI Responsif** – Desain antarmuka yang menyesuaikan berbagai perangkat.
- 🤳 **Real-time Gesture Translation** – Menggunakan kamera pengguna untuk menerjemahkan gerakan bahasa isyarat secara langsung.
- 🎥 **Video Translation** – Mendukung terjemahan dari konten video yang sudah direkam sebelumnya.

---

## 🧰 Teknologi yang Digunakan

- **React.js** – Library JavaScript untuk membangun antarmuka pengguna berbasis komponen.
- **Bootstrap** – Framework Library CSS untuk mempercepat pengembangan UI yang responsif dan konsisten.
- **Vite** – Build tool modern untuk frontend yang sangat cepat.
- **ESLint** – Linter untuk menjaga konsistensi dan kualitas kode JavaScript.

---

## 💻 Cara Menjalankan Aplikasi Secara Lokal

Download Node.Js pada link berikut
```bash
https://nodejs.org/en/download
```

### 1. Clone repositori
```bash
git clone https://github.com/SiLa-Sign-Language-Application/sila-frontend.git
cd sila-frontend
```

### 2. Install dependensi
```bash
npm install
```

### 3. Jalankan aplikasi
```bash
npm run dev
```

Aplikasi akan berjalan di:
```
http://localhost:5173/
```

---

## ⚙️ Koneksi dengan Backend Lokal

Untuk menjalankan aplikasi dengan backend FastAPI lokal, **pastikan kamu sudah menjalankan backend di `http://127.0.0.1:8000`**, lalu **ubah URL API pada file berikut**:

### ✏️ Ubah di `GestureComponent.jsx`
```js
// Sebelumnya:
const API_URL = "https://sila-backend-production.up.railway.app/predict";

// Ubah menjadi:
const API_URL = "http://127.0.0.1:8000/predict";
```

### ✏️ Ubah di `VideoComponent.jsx` *(jika ada endpoint untuk video)*
```js
// Contoh jika kamu menggunakan endpoint predict untuk video:
const API_URL = "http://127.0.0.1:8000/predict";
```

> ⚠️ Pastikan CORS di backend sudah diatur untuk mengizinkan akses dari `http://localhost:5173`.

---

## 📜 Skrip NPM

- `npm run dev` – Menjalankan aplikasi dalam mode pengembangan.
- `npm run build` – Membangun aplikasi untuk produksi.
- `npm run preview` – Melihat hasil build produksi secara lokal.
- `npm run lint` – Menjalankan linter untuk memeriksa dan menjaga kualitas kode.

---

## 📁 Struktur Proyek

```bash
sila-frontend/
├── public/
│   └── images/
├── src/
│   ├── api/
│   ├── assets/
│   │   ├── css/
│   │   └── images/
│   ├── components/
│   │   ├── GestureComponent.jsx
│   │   └── VideoComponent.jsx
│   ├── data/
│   └── pages/
├── .gitignore
├── index.html
├── package.json
├── README.md
├── vite.config.js
└── vercel.json
```

---

## 📁 api/feedbackApi.js

## 📡 API Endpoint: Feedback Submission

Aplikasi ini menggunakan layanan **[SheetBest](https://sheet.best/)** sebagai backend sederhana untuk menyimpan data feedback pengguna ke dalam Google Sheets. Data dikirim ke endpoint API menggunakan metode `POST`.

### 🔗 API Endpoints

#### Feedback

**POST** `https://api.sheetbest.com/sheets/b7dbf6d5-3a56-4566-98e3-ec3210f0f13b`: Submit user feedback data to Google Sheets via SheetBest API

### 📤 Data yang Dikirim

Setiap kali pengguna mengirimkan feedback, aplikasi akan mengirim data ke endpoint dalam format JSON dengan struktur berikut:

```json
{
  "name": "userXXXX",
  "feedback": "Teks feedback dari pengguna",
  "rating": "Nilai rating (misal: 4 atau 5)",
  "timestamp": "Waktu pengiriman dalam format ISO (YYYY-MM-DDTHH:MM:SSZ)"
}
```

#### Penjelasan Field:

* `name`: ID pengguna acak yang digenerate otomatis (misalnya, `user1234`)
* `feedback`: Isi feedback dari pengguna
* `rating`: Nilai rating (biasanya berupa angka, misalnya 1–5)
* `timestamp`: Tanggal dan waktu pengiriman dalam format ISO 8601
