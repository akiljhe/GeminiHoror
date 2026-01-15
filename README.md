# 🎮 Gema Penderitaan (Echo of Suffering)

**Gema Penderitaan** adalah sebuah pengalaman **horor psikologis 3D berbasis web** yang dibangun menggunakan **Vanilla JavaScript** dan **Three.js**.  
Game ini dirancang untuk menciptakan atmosfer mencekam **dalam satu file HTML tunggal**, tanpa memuat aset eksternal apa pun.

> *Dibuat dengan kode, ditenagai oleh ketakutan.*

---

## 🏚️ Latar Cerita

Anda terjebak di **"Fasilitas 09"**, sebuah kompleks penelitian yang telah lama ditinggalkan.  
Lorong-lorong gelap, suara statis, dan sesuatu yang mengintai di balik bayangan menjadi satu-satunya teman Anda.

Satu tujuan utama: **melarikan diri**.

---

## 🎮 Cara Bermain

- Cari **Kunci Berkarat** 🔴 (Kotak Merah) yang tersembunyi secara acak di dalam peta.
- Setelah mendapatkan kunci, temukan **Pintu Keluar** 🟢 (Kotak Hijau/Metalik).
- **Hindari "Dia"** — sosok bermata merah yang mengintai dan mendengar setiap langkah Anda.

---

## ⌨️ Sistem Kontrol

| Tombol | Aksi |
|------|------|
| **W, A, S, D** | Bergerak (Jalan) |
| **SHIFT** | Lari (Sprint) – Menguras stamina |
| **Mouse** | Melihat sekeliling |
| **E** | Interaksi (Ambil kunci / Buka pintu) |

---

## ✨ Fitur Utama

### 1. Massive Procedural Map Generation
- **Peta Raksasa 75×75**  
  Setiap permainan menggunakan algoritma **Recursive Backtracker** untuk menciptakan labirin unik.  
  Tidak ada dua permainan yang sama.
- **Optimasi Rendering**  
  Menggunakan `InstancedMesh` dari Three.js untuk merender ribuan dinding dalam satu *draw call*, menjaga performa tetap stabil.

---

### 2. Advanced Enemy AI — *"The Stalker"*
- **Auditory Sensitivity**  
  Musuh memiliki dua mode:
  - *Roaming* (berkeliaran acak)
  - *Chasing* (mengejar pemain)  
  Berlari akan langsung memicu pengejaran.
- **Teleportasi Dinamis**  
  Setiap 15 detik, musuh akan berpindah ke lokasi acak yang valid (tidak menembus tembok, tidak dekat pemain).
- **Pathfinding BFS**  
  Menggunakan **Breadth-First Search** untuk menemukan jalur terpendek di labirin kompleks.

---

### 3. Procedural Audio Engine
- **Tanpa File MP3 / WAV**  
  Semua suara dihasilkan **real-time** menggunakan **Web Audio API**.
- **Audio Dinamis**  
  Detak jantung dan intensitas suara berubah berdasarkan jarak musuh.
- Termasuk:
  - Langkah kaki
  - Ambience
  - Static noise
  - Jumpscare scream

---

### 4. Immersive Gameplay Mechanics
- **Sistem Stamina**  
  Pemain tidak dapat berlari tanpa batas.
- **Wall Sliding Physics**  
  Kolisi halus mencegah karakter tersangkut di sudut dinding.
- **Radar / Minimap**  
  Menampilkan posisi pemain dan musuh (jika dalam jangkauan).

---

### 5. Atmosfer & Visual
- **Story Intro**  
  Cutscene berbasis teks sebelum permainan dimulai.
- **Procedural Textures**  
  Tekstur dinding dan lantai dibuat otomatis menggunakan **Canvas API**.
- **Post-Processing Effects**  
  Efek *Vignette* dan *Film Grain* untuk nuansa horor klasik ala VHS.

---

## 🏆 Keunggulan Teknis

- **Single File Application**  
  Seluruh game (HTML, CSS, JS, Audio, Texture) berada dalam **satu file HTML**.
- **Zero External Assets**  
  Tidak ada gambar atau audio eksternal → loading hampir instan.
- **Cross-Browser**  
  Berjalan di browser modern (Chrome, Firefox, Edge) yang mendukung **WebGL**.

---

## ⚠️ Peringatan

Game ini mengandung:
- Lampu berkedip (*flashing lights*)
- Suara keras mendadak (*jumpscares*)

🎧 **Sangat disarankan menggunakan headphone** untuk pengalaman terbaik.

---

## 🧠 Teknologi yang Digunakan

- Vanilla JavaScript
- Three.js
- Web Audio API
- Canvas API
- WebGL

---

## 🩸 Penutup

Jika Anda mendengar langkah kaki di belakang…  
**jangan menoleh.**
