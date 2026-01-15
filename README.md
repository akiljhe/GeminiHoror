🎮 Gema Penderitaan (Echo of Suffering)

Gema Penderitaan adalah game horor psikologis 3D berbasis web yang dibangun menggunakan Vanilla JavaScript dan Three.js. Game ini dirancang untuk menghadirkan atmosfer mencekam dalam satu file HTML tunggal, tanpa memuat aset eksternal apa pun.

Dibuat dengan kode, ditenagai oleh ketakutan.

🕯️ Deskripsi Singkat

Anda terjebak di Fasilitas 09, sebuah labirin penelitian yang telah lama ditinggalkan. Kegelapan menyelimuti setiap sudut, dan sesuatu mengintai Anda dari kejauhan.

Tugas Anda sederhana, tetapi tidak mudah:

Temukan Kunci Berkarat

Cari Pintu Keluar

Bertahan hidup dari “Dia”

Tidak ada peta yang sama. Tidak ada tempat yang benar-benar aman.

🎮 Cara Bermain

Anda akan muncul di dalam labirin gelap yang dihasilkan secara prosedural.

Cari Kunci Berkarat (ditandai dengan kotak merah).

Setelah kunci didapatkan, temukan Pintu Keluar (kotak hijau/metalik).

Hindari “Dia”, sosok bermata merah yang akan mengejar jika mendengar langkah Anda.

🎹 Sistem Kontrol
Tombol	Aksi
W, A, S, D	Bergerak
SHIFT	Lari (Sprint – menguras stamina)
Mouse	Melihat sekeliling
E	Interaksi (ambil kunci / buka pintu)
✨ Fitur Utama
1️⃣ Massive Procedural Map Generation

Peta 75x75 yang dihasilkan ulang setiap permainan menggunakan algoritma Recursive Backtracker

Tidak ada dua sesi permainan yang sama

Optimasi menggunakan InstancedMesh (Three.js) untuk menjaga performa tetap tinggi

2️⃣ Advanced Enemy AI – “The Stalker”

Mode Roaming & Chasing

Musuh dapat mendengar langkah kaki, terutama saat pemain berlari

Teleportasi acak setiap 15 detik untuk menghindari eksploitasi pemain

Pathfinding BFS (Breadth-First Search) untuk navigasi labirin yang kompleks

3️⃣ Procedural Audio Engine

Tanpa file audio eksternal (MP3/WAV)

Semua suara dihasilkan real-time menggunakan Web Audio API

Termasuk:

Langkah kaki

Detak jantung

Ambience

Static noise

Jumpscare scream

Intensitas suara berubah berdasarkan jarak dengan musuh

4️⃣ Immersive Gameplay Mechanics

Sistem stamina untuk sprint

Wall sliding physics untuk kolisi yang halus

Radar / minimap untuk membantu navigasi dan mendeteksi musuh dalam jangkauan

5️⃣ Atmosfer & Visual

Intro cerita berbasis teks

Tekstur dinding & lantai procedural (Canvas API)

Efek visual:

Vignette

Film grain

Nuansa horor VHS

🏆 Keunggulan Teknis

✅ Single File Application
Seluruh game berada dalam satu file HTML

✅ Zero External Assets
Tidak ada gambar atau audio eksternal

✅ Offline Ready
Cukup buka file HTML di browser

✅ Cross-Browser Support
Berjalan di Chrome, Firefox, Edge (WebGL)

⚠️ Peringatan

⚠️ Game ini mengandung:

Lampu berkedip (flashing lights)

Suara keras mendadak (jumpscare)

🎧 Disarankan menggunakan headphone untuk pengalaman terbaik.

🚀 Cara Menjalankan

Clone repository ini:

git clone https://github.com/username/gema-penderitaan.git


Buka file index.html langsung di browser

Mainkan dan bertahan hidup

🧠 Teknologi yang Digunakan

JavaScript (Vanilla)

Three.js

Web Audio API

Canvas API

WebGL
