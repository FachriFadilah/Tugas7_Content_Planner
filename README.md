# Tugas7_Content_Planner
# Tugas 7: Content Planner Bot (n8n + Telegram + AI)

Workflow n8n yang menerima perintah dari bot Telegram, lalu membuat rencana konten harian, gambar, atau video secara otomatis.

## Fitur

| Input di Telegram | Hasil |
|---|---|
| `/start <tanggal> <tema>` | Rencana konten harian (5 slot: `time_slot`, `title`, `focus`) |
| Teks biasa | Gambar dari prompt teks |
| Foto + caption `video` | Video animasi dari foto |

## Alur Workflow

- **Telegram Trigger → Switch**: memilah perintah menjadi cabang Ide, Gambar, dan Video.
- **Ide**: Basic LLM Chain (Gemini Chat Model) → Structured Output Parser → Code (format pesan) → Telegram.
- **Gambar**: KIE.ai text-to-image (buat task → Wait → cek status) → Telegram Send Photo.
- **Video**: Get a file → Code (Base64 ↔ Buffer) → upload ke KIE.ai → image-to-video → Wait → cek status → Telegram Send Video.

## Teknologi

n8n, Telegram Bot API, Google Gemini, KIE.ai (Grok Imagine), JavaScript.

## Cara Pakai

1. Import `Tugas7_Content_Planner.json` ke n8n (menu
