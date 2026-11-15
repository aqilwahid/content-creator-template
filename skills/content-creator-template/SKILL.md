---
name: content-creator-template
description: "Generator prompt (reverse prompting) untuk konten video pendek: 1. Buat Skrip, 2. Buat Storyboard, 3. Buat Profil Karakter, 4. Video Omni 1.2 (Google Flow). Tanya kebutuhan dulu, lalu keluarkan prompt siap tempel ke ChatGPT atau Gemini Omni."
license: CC BY 4.0
metadata:
  version: "1.0.0"
  language: "id"
---

# Content Creator Template

Skill ini **tidak membuat kontennya langsung**. Skill ini mewawancarai pengguna, lalu menghasilkan **prompt yang sudah dipersonalisasi** untuk ditempel ke ChatGPT (modul 1–3) atau Gemini Omni Flash 1.2 di Google Flow (modul 4).

## Menu

Jika pengguna belum memilih, tampilkan menu ini persis:

```
1. Buat Skrip
2. Buat Storyboard
3. Buat Profil Karakter
4. Video Omni 1.2
```

Modul bisa dipakai terpisah atau berurutan: hasil skrip (1) → storyboard (2); profil karakter (3) → video (4).

## Aturan umum (semua modul)

1. **Tanya dulu, baru tulis prompt.** Satu putaran maksimal 4 pertanyaan. Jika tool tanya-jawab pilihan ganda tersedia (mis. AskUserQuestion), pakai tool itu dengan opsi siap pilih (opsi rekomendasi di urutan pertama). Jika tidak, tanyakan dalam satu daftar ringkas bernomor.
2. **Jangan tanya yang sudah diketahui.** Simpan jawaban dalam **Kartu Proyek** (topik, platform, durasi, rasio, gaya, tone, audiens, DNA Karakter). Pakai ulang di modul berikutnya; konfirmasi singkat saja.
3. **Jawaban kosong → pakai default yang wajar** dan tulis asumsinya di dalam prompt (bagian KONTEKS).
4. **Keluaran = hanya prompt** di dalam satu blok kode (atau beberapa blok bernomor bila memang perlu beberapa prompt). Setelah blok kode, paling banyak satu baris petunjuk (mis. "Tempel ke ChatGPT"). Tanpa pembuka, tanpa ringkasan.
5. **Prompt harus compact**: perintah jelas, batasan terukur (jumlah kata, detik, jumlah shot), format keluaran yang diminta tegas. Tidak ada kalimat hiasan.
6. Bahasa prompt: modul 1–3 dalam **Bahasa Indonesia**; modul 4 dalam **Bahasa Inggris** (Omni paling stabil dengan instruksi Inggris), dengan dialog tetap dalam bahasa yang dipilih pengguna dan dikutip persis.
7. Jangan membuat karakter yang meniru orang sungguhan, tokoh terkenal, atau karakter/merek berhak cipta. Jika diminta, tawarkan karakter orisinal. Foto pengguna sendiri boleh dipakai sebagai referensi.

## Patokan durasi → jumlah kata

Tempo bicara Indonesia untuk VO/talking head ±2,3–2,5 kata/detik.

| Durasi | Maks kata naskah | Struktur |
|---|---|---|
| 10 detik | 22 | hook 1 kalimat + 1 poin + CTA singkat |
| 15 detik | 35 | hook + 1–2 poin + CTA |
| 30 detik | 70 | hook + 2–3 poin + CTA |
| 60 detik | 140 | hook + 3–4 poin + CTA |
| custom | durasi × 2,3 | proporsional |

Hook selalu di 0–3 detik pertama.

---

## 1. Buat Skrip

**Tujuan:** prompt agar ChatGPT menulis skrip yang **fit**: padat, satu ide utama, tanpa bertele-tele.

**Tanyakan (pilih yang belum diketahui, maksimal 2 putaran):**
1. Topik/pesan inti (satu kalimat) dan produk/info wajib yang harus disebut.
2. Platform & durasi: TikTok/Reels/Shorts (10/15/30/60 detik) atau custom.
3. Format: talking head, voice-over + b-roll, skit/dialog 2 karakter, atau tutorial.
4. Audiens dan tujuan (edukasi, jualan, branding, ajakan follow).
5. Tone & bahasa: santai (gue/lu, aku/kamu) atau formal; ada gaya khas kreator?
6. CTA yang diinginkan.

**Template prompt keluaran:**

```
PERAN: Kamu penulis skrip video pendek yang hemat kata.

KONTEKS:
- Topik/pesan inti: [..]
- Wajib disebut: [..]
- Platform & durasi: [..] detik ([rasio])
- Format: [..]
- Audiens: [..] | Tujuan: [..]
- Tone & bahasa: [..]
- CTA: [..]
- Asumsi: [default yang dipakai, jika ada]

ATURAN:
1. Total maksimal [N] kata ucapan. Hitung dan tulis jumlahnya.
2. 0–3 detik: hook yang langsung ke masalah/manfaat. Dilarang pembuka basa-basi ("halo guys", "di video kali ini").
3. Satu kalimat = satu ide, 5–10 kata. Tidak ada pengulangan ide.
4. Hanya [jumlah] poin isi. Buang semua yang tidak mendukung pesan inti.
5. Tutup dengan CTA dalam satu kalimat.
6. Tulis angka, singkatan, dan istilah asing sesuai cara diucapkan.

FORMAT JAWABAN:
Tabel: Waktu | Ucapan/Dialog | Visual singkat | Teks layar (maks 5 kata)
Lalu: jumlah kata, dan 2 alternatif hook (masing-masing maks 10 kata).
Jangan beri penjelasan lain.
```

Untuk format skit, ganti kolom Ucapan menjadi `Karakter: dialog` dan tambahkan aturan "maksimal [n] baris dialog per karakter".

---

## 2. Buat Storyboard

**Tujuan:** prompt agar ChatGPT menyusun storyboard per shot yang siap diterjemahkan ke prompt video.

**Tanyakan:**
1. Durasi: **10 detik / 15 detik / 1 menit / custom** (wajib ditanya dengan opsi ini).
2. Rasio: 9:16 (vertikal) atau 16:9.
3. Sumber cerita: tempel skrip (hasil modul 1) atau ringkasan ide.
4. Gaya visual: fotorealistis sinematik, 3D animasi stylized, ilustrasi 2D, atau dokumenter handheld.
5. Karakter & lokasi: ambil DNA Karakter dari modul 3 jika ada; jika belum, minta deskripsi singkat.

**Patokan jumlah shot:**

| Durasi | Shot | Segmen Omni |
|---|---|---|
| 10 detik | 3–4 | 1 klip (10s) |
| 15 detik | 4–6 | 1 klip (15s) |
| 1 menit | 12–18 | 4 klip × 15s (atau 6 × 10s) |
| custom | ±1 shot per 2,5–4 detik | klip maks 15 detik |

**Template prompt keluaran:**

```
PERAN: Kamu sutradara dan storyboard artist untuk video pendek [platform].

KONTEKS:
- Durasi total: [..] detik | Rasio: [..] | Gaya visual: [..]
- Cerita/skrip: [tempel skrip atau ringkasan]
- Karakter (pakai deskripsi ini persis di setiap shot): [DNA Karakter]
- Lokasi: [..]

ATURAN:
1. Buat [n] shot. Timecode berurutan tanpa celah, total tepat [durasi] detik.
2. Kelompokkan shot menjadi segmen maksimal 15 detik (Segmen A, B, ...) untuk dibuat sebagai klip video terpisah.
3. Setiap shot: satu aksi utama yang jelas terlihat. Variasikan ukuran shot (wide, medium, close-up) dan sudut kamera.
4. Jaga kontinuitas: pakaian, properti, cahaya, dan arah pandang konsisten antar shot.
5. Hindari aksi fisik rumit atau gerakan sangat cepat.
6. Tandai akhir tiap segmen dengan pose/posisi akhir yang jelas (dipakai sebagai start frame segmen berikutnya).

FORMAT JAWABAN (tabel):
Segmen | Shot | Timecode | Ukuran shot & sudut | Gerak kamera | Visual & aksi | Dialog/VO | Audio (musik/SFX/ambience) | Teks layar | Transisi
Setelah tabel: catatan kontinuitas per segmen (maks 2 baris). Tanpa penjelasan lain.
```

---

## 3. Buat Profil Karakter

**Tujuan:** karakter konsisten di semua gambar dan video. Hasilnya: **DNA Karakter** (deskripsi tetap) + rangkaian prompt gambar untuk ChatGPT (pembuatan gambar).

**Tanyakan:**
1. Nama & peran (host, maskot, tokoh skit), usia kisaran, kesan gender.
2. Fisik: bentuk wajah, kulit, rambut (model & warna), mata, postur/tinggi, ciri khas (tahi lalat, kacamata, dll.).
3. Pakaian signature + palet warna + aksesori/properti tetap.
4. Kepribadian & ekspresi andalan.
5. Gaya visual (harus sama dengan storyboard/video) dan apakah ada foto referensi milik sendiri.

**Langkah keluaran:** tulis 3 blok berurutan.

**Blok A — DNA Karakter** (≤ 60 kata, bahasa Inggris, dipakai ulang persis di modul 2 dan 4):

```
[NAMA]: [usia]-year-old [kesan gender], [kulit], [bentuk wajah], [mata], [rambut], [ciri khas], [postur]. Wears [pakaian signature, warna]. [aksesori]. Style: [gaya visual]. Personality: [2–3 sifat].
```

**Blok B — Prompt master** (tempel pertama ke ChatGPT):

```
Buat satu gambar karakter orisinal, [gaya visual], full body tampak depan, berdiri netral, latar abu-abu polos, cahaya studio merata, rasio 2:3.
Karakter: [DNA Karakter]
Jangan tambahkan teks, logo, atau orang lain.
```

**Blok C — Prompt turunan** (dikirim satu per satu di chat yang sama, setelah gambar master jadi):

```
Pakai gambar master di atas sebagai acuan. Wajah, rambut, proporsi, pakaian, warna, dan gaya HARUS identik. Latar dan cahaya sama.
1. Turnaround full body: depan, samping kanan, belakang, 3/4 kiri, dalam satu lembar berjajar.
2. Close-up wajah tampak depan, ekspresi netral, bahu ke atas.
3. Close-up 3/4 tampak samping.
4. Lembar ekspresi 2x3: senang, tertawa, kaget, serius, bingung, sedih.
5. Medium shot (pinggang ke atas) dengan pose khas: [pose/properti].
6. Detail: tangan + properti, dan detail pakaian/aksesori.
Buat satu gambar per nomor. Tanpa teks.
```

Tutup dengan satu baris petunjuk: untuk Omni 1.2 di Flow, simpan **3 gambar terbaik per karakter** (full body depan, close-up wajah depan, 3/4) sebagai ingredients.

---

## 4. Video Omni 1.2

Target: **Gemini Omni Flash 1.2** (Google DeepMind), dipakai di **Google Flow**. Fakta model (dari dokumentasi bantuan Flow dan panduan pihak ketiga, Nov 2026; verifikasi di aplikasi bila angka berbeda):
- Durasi generate 3–15 detik (default 10). Video 1 menit = beberapa klip yang dirakit.
- Native audio: dialog dengan lip sync, SFX, ambience, musik. Tidak ada kolom negative prompt; audio dan larangan ditulis di prompt, diam pun harus diminta.
- Referensi: maks 3 gambar per karakter; sebutkan peran tiap referensi dalam kalimat biasa; lampirkan semua di awal.
- Teks layar bahasa Inggris stabil; bahasa lain bisa berantakan, jadi teks bahasa Indonesia lebih aman ditambahkan di editor.
- Kurang andal untuk aksi cepat dan fisika rumit. Tidak ada seed; buat beberapa take dan pilih terbaik.

### Alur di Google Flow

Set model ke **Omni Flash 1.2** di pengaturan generate. Fitur yang dipakai:
- **Ingredients**: lampirkan gambar karakter dari modul 3 (maks 3 per karakter) di awal.
- **Start/end frame**: di klip yang bagus, pause lalu *Save frame* pada frame terakhir, dan pakai sebagai start frame segmen berikutnya agar sambungan mulus.
- **Extend**: klik klip, pilih *Extend*, tentukan tambahan durasi, lalu jelaskan kelanjutan aksi (bisa tambah 3 gambar referensi). Klip hasil extend tidak bisa diedit insert/remove/kamera, jadi edit dulu baru extend. Batas total extend berbeda antarversi (30–40 detik); cek di aplikasi.
- **Edit & refine**: pilih segmen maks 10 detik (15 detik untuk AI Plus/Pro/Ultra), satu perubahan per prompt, maks 3 putaran. Ketersediaan tergantung negara.
- **Scenebuilder**: tambahkan klip lewat *More* lalu *Add to Scene*, urutkan, trim, preview, unduh.

Urutan kerja yang disarankan: generate tiap segmen dengan ingredients → pilih take terbaik → edit bila perlu → extend bila perlu → save frame terakhir → segmen berikutnya dengan start frame → rakit di Scenebuilder → teks layar bahasa Indonesia, musik akhir, dan caption di editor (CapCut/Premiere).

**Tanyakan:**
1. Mode: generate baru, extend klip, atau edit klip.
2. Segmen yang dibuat (tempel baris storyboard) atau deskripsi adegan; durasi 3–15 detik; rasio.
3. Karakter & referensi: DNA Karakter + berapa gambar referensi yang dilampirkan untuk tiap karakter; pakai start frame atau tidak.
4. Audio: dialog/VO (siapa, bahasa, kalimat persis), musik (genre + mood) atau tanpa musik, ambience/SFX.
5. Satu take kontinu atau multi-shot dengan cut; perlu teks layar?

**Template prompt keluaran — generate baru:**

```
Format: [9:16 vertical | 16:9], [N]s, [style].
References: Image 1–[k] show [NAMA]; keep face, hair, outfit and colors identical to them. [Image x is only a guide for the location.] [Start frame: the attached frame, last frame of the previous segment.]
Character: [DNA Karakter]
Scene: [lokasi, waktu, suasana].
Shots: [Single continuous shot, no scene cuts, camera ... | Shot 1 ... cut to Shot 2 ...].
Timeline:
[0-3s] [aksi + kamera]
[3-7s] [..]
[7-Ns] [..]
Lighting & look: [..].
Audio: [NAMA] says in [bahasa]: "[kalimat persis]". [Voiceover: a [jenis suara] says "..."; the on-screen person does not speak.] Music: [genre, mood | No music]. Background ambience: [..]. SFX: [..].
Exclusions: No subtitles. No on-screen text. No extra characters. No logos.
```

Aturan pengisian:
- Timecode berurutan dan berakhir tepat di N detik.
- Gerak kamera ditulis di kalimat yang sama dengan "single continuous shot"; untuk multi-shot pakai "cut to".
- Satu prompt = satu segmen storyboard. Untuk 1 menit, keluarkan 4 prompt bernomor (Segmen A–D, masing-masing 15s) dengan DNA Karakter, pakaian, cahaya, dan palet yang identik, serta baris `Continuity: continues from previous segment, [posisi/aksi terakhir].`
- Dialog maksimal ±2,3 kata per detik dari durasi bicara.
- Jika butuh teks layar Inggris, kutip persis dan sebutkan posisinya; jika bahasa Indonesia, tulis "No on-screen text" dan sarankan ditambah di editor.

**Template — extend:**

```
Continue the same shot for [n]s: [aksi lanjutan]. Keep character, outfit, lighting, camera style and audio mood identical. Audio: [..]. No on-screen text.
```

**Template — edit & refine (satu perubahan per giliran):**

```
Change only [satu hal yang diubah]. Keep everything else exactly the same: character, timing, camera, lighting, audio.
```

**Contoh keluaran modul 4** (segmen 10 detik, host orisinal "Raka", 3 ingredients):

```
Format: 9:16 vertical, 10s, photorealistic cinematic.
References: Images 1-3 show RAKA; keep face, hair, outfit and colors identical to them.
Character: RAKA: 27-year-old Indonesian man, warm brown skin, oval face, dark brown eyes, short wavy black hair, thin round glasses, slim build. Wears a mustard-yellow overshirt over a white tee. Silver wristwatch. Style: photorealistic. Personality: friendly, energetic, witty.
Scene: small home studio, late afternoon, warm and tidy.
Shots: single continuous shot, no scene cuts, camera slowly pushes in from medium shot to medium close-up.
Timeline:
[0-3s] Raka looks into the lens and raises his phone.
[3-7s] He taps the screen and nods.
[7-10s] He points at the camera and smiles.
Lighting & look: soft window light from the left, warm grade, shallow depth of field.
Audio: Raka says in Indonesian: "Kuota cepat habis? Matikan autoplay video sekarang." Music: light upbeat lo-fi, low volume. Background ambience: quiet room tone. SFX: soft tap on the phone screen.
Exclusions: No subtitles. No on-screen text. No extra characters. No logos.
```

---

## Contoh modul 1

Pengguna: "1, skrip 15 detik Reels soal tips hemat kuota, santai, CTA follow." Setelah 1 putaran tanya (format & audiens), keluaran:

```
PERAN: Kamu penulis skrip video pendek yang hemat kata.
KONTEKS:
- Topik: 3 tips hemat kuota HP
- Platform & durasi: Instagram Reels, 15 detik (9:16)
- Format: talking head
- Audiens: mahasiswa | Tujuan: edukasi + follow
- Tone: santai, aku/kamu
- CTA: follow untuk tips harian
ATURAN:
1. Maksimal 35 kata ucapan. Tulis jumlahnya.
2. 0–3 detik: hook langsung ke masalah. Tanpa basa-basi.
3. Satu kalimat = satu ide, 5–10 kata.
4. Hanya 2 tips paling berdampak.
5. CTA satu kalimat.
FORMAT JAWABAN: Tabel Waktu | Ucapan | Visual singkat | Teks layar (maks 5 kata). Lalu jumlah kata dan 2 alternatif hook. Tanpa penjelasan lain.
```
Tempel ke ChatGPT.
