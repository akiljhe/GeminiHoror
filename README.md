Gema Penderitaan (Echo of Suffering)

Gema Penderitaan adalah sebuah pengalaman horor psikologis 3D berbasis web yang dibangun menggunakan Vanilla JavaScript dan Three.js. Game ini dirancang untuk memberikan atmosfer yang mencekam dalam satu file tunggal tanpa memuat aset eksternal.

🎮 Cara Bermain

Anda terjebak di "Fasilitas 09", sebuah labirin gelap yang ditinggalkan.

Cari Kunci Berkarat (Kotak Merah) yang tersembunyi secara acak di dalam peta.

Setelah mendapatkan kunci, cari Pintu Keluar (Kotak Hijau/Metalik) untuk melarikan diri.

Hindari "Dia". Sosok bermata merah yang mengintai di kegelapan.

Sistem Kontrol

Tombol

Aksi

W, A, S, D

Bergerak (Jalan)

SHIFT

Lari (Sprint) - Menguras Stamina

Mouse

Melihat sekeliling

E

Interaksi (Ambil kunci / Buka pintu)

✨ Fitur Utama

1. Massive Procedural Map Generation

Peta Raksasa 75x75: Setiap kali permainan dimulai, algoritma Recursive Backtracker akan membuat labirin baru yang unik dan sangat luas. Tidak ada dua permainan yang sama.

Optimasi Rendering: Menggunakan InstancedMesh dari Three.js untuk merender ribuan dinding dalam satu draw call, menjaga frame rate tetap tinggi meski peta sangat besar.

2. Advanced Enemy AI ("The Stalker")

Auditory Sensitivity: Musuh memiliki mode Roaming (berkeliaran acak) dan Chasing (mengejar). Jika Anda berlari (Sprint), musuh akan mendengar langkah Anda dan langsung mengejar ke posisi Anda.

Teleportasi: Untuk mencegah pemain memprediksi posisi, musuh akan melakukan teleportasi acak setiap 15 detik ke lokasi yang valid di peta (tidak menembus tembok, tidak terlalu dekat dengan spawn pemain).

Pathfinding: Menggunakan algoritma BFS (Breadth-First Search) untuk mencari jalur terpendek menuju pemain di dalam labirin yang kompleks.

3. Procedural Audio Engine

Tanpa File MP3: Game ini tidak memuat aset suara eksternal. Semua suara (langkah kaki, detak jantung, jumpscare scream, ambience, static noise) dihasilkan secara real-time menggunakan Web Audio API.

Dynamic Sound: Frekuensi detak jantung dan intensitas suara berubah berdasarkan kedekatan dengan musuh.

4. Immersive Gameplay Mechanics

Sistem Stamina: Pemain tidak bisa berlari selamanya. Manajemen stamina diperlukan untuk kabur di saat genting.

Wall Sliding Physics: Sistem kolisi yang mulus memungkinkan pemain "meluncur" saat menabrak dinding miring, mencegah karakter tersangkut (stuck).

Radar/Minimap: Radar di pojok kanan atas membantu navigasi di peta yang luas, menunjukkan posisi pemain dan musuh (jika dalam jangkauan).

5. Atmosfer & Visual

Story Intro: Cutscene berbasis teks yang membangun narasi sebelum permainan dimulai.

Procedural Textures: Tekstur dinding dan lantai dibuat menggunakan Canvas API (noise & gradient) secara otomatis.

Post-Processing: Efek Vignette dan Film Grain untuk memberikan kesan visual horor jadul (VHS style).

🏆 Keunggulan Teknis

Single File Application: Seluruh game (HTML, CSS, JS, Audio, Texture) berada dalam satu file HTML. Sangat mudah dibagikan dan dijalankan secara offline.

Zero External Assets: Tidak ada gambar (JPG/PNG) atau audio (MP3/WAV) yang perlu diunduh, membuat waktu loading hampir instan.

Cross-Browser: Berjalan di browser modern apa pun (Chrome, Firefox, Edge) yang mendukung WebGL.

⚠️ Peringatan

Game ini mengandung lampu berkedip (flashing lights) dan suara keras tiba-tiba (jumpscares). Harap gunakan headphone untuk pengalaman terbaik.

Dibuat dengan kode, ditenagai oleh ketakutan.
