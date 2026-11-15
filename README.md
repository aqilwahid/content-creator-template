# Content Creator Template (Agent Skill)

Skill untuk AI Agent yang menghasilkan **prompt siap pakai** (reverse prompting) bagi pembuat video pendek:

1. **Buat Skrip** — prompt ChatGPT untuk skrip padat sesuai durasi.
2. **Buat Storyboard** — prompt ChatGPT untuk storyboard 10 detik, 15 detik, 1 menit, atau custom.
3. **Buat Profil Karakter** — DNA Karakter + prompt gambar karakter dari beberapa sisi agar konsisten.
4. **Video Omni 1.2** — prompt untuk Gemini Omni Flash 1.2 di Google Flow (generate, extend, edit).

Setiap modul bertanya dulu, lalu hanya mengeluarkan prompt.

## Cara pasang

- **Agentic Skill Installer (VS Code):** tambahkan `https://github.com/aqilwahid/content-creator-template` sebagai source repository, lalu refresh katalog dan cari **content-creator-template**.
- **Claude Code / agen lain yang membaca Agent Skills:** salin folder `skills/content-creator-template/` ke direktori skills agen, mis. `~/.claude/skills/content-creator-template/`.
- **Claude (claude.ai / Cowork):** kompres isi folder `skills/content-creator-template/` menjadi ZIP dengan `SKILL.md` di root ZIP, lalu unggah melalui Settings → Capabilities → Skills.

## Cara pakai

Ketik misalnya: "Pakai content creator template, nomor 2, storyboard 15 detik."

## Catatan

- Fakta Omni Flash 1.2 dan fitur Flow dicek November 2026; batas durasi dan fitur bisa berubah, cek di aplikasi.
- Format mengikuti spesifikasi Agent Skills (https://agentskills.io/specification).
- Lisensi: CC BY 4.0.
