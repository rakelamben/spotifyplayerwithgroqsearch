# Cari Satu Lagu

Aplikasi web sederhana untuk mencari satu lagu berdasarkan deskripsi. Groq
memilih lagu yang paling sesuai, lalu Spotify API mencari lagu tersebut dan
aplikasi menampilkan pemutar Spotify.

## Fitur

- Menerima deskripsi lagu dalam bahasa bebas, misalnya: “lagu galau hujan malam
  hari”.
- Memilih satu lagu menggunakan Groq.
- Mencari lagu di Spotify dan menampilkan pemutar embed.

## Persiapan

- Python 3.10 atau lebih baru.
- API key Groq.
- Spotify Client ID dan Client Secret dari Spotify Developer Dashboard.

## Instalasi dan menjalankan

1. Clone repository dan masuk ke folder proyek.
2. Buat virtual environment dan pasang dependensi:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   pip install -r requirements.txt
   ```

3. Buat file `.env` di folder utama proyek:

   ```env
   GROQ_API_KEY=isi_api_key_groq
   SPOTIFY_CLIENT_ID=isi_spotify_client_id
   SPOTIFY_CLIENT_SECRET=isi_spotify_client_secret
   ```

   Jangan membagikan atau meng-commit file `.env`.

4. Jalankan aplikasi:

   ```powershell
   python app.py
   ```

5. Buka alamat lokal yang ditampilkan Flask di terminal (biasanya
   `http://127.0.0.1:5000`), lalu masukkan deskripsi lagu.

## Endpoint API

### `POST /api/play`

Request JSON:

```json
{
  "query": "lagu pop tentang jatuh cinta"
}
```

Jika lagu ditemukan, respons berisi `track_id`, `name`, `artists`,
`embed_url`, dan `spotify_url`. Input kosong menghasilkan status `400`; lagu
yang tidak ditemukan menghasilkan `404`; kegagalan dari layanan Groq atau
Spotify menghasilkan `502`.

## Dependensi utama

- Flask untuk server web.
- Groq SDK untuk memilih lagu berdasarkan deskripsi.
- Requests untuk mengakses Spotify Web API.
- python-dotenv untuk membaca konfigurasi dari `.env`.
