# Roblox Model Uploader

Tool lokal untuk upload file **Model Roblox (.rbxm / .rbxmx)** langsung ke Roblox Creator lewat **Open Cloud Assets API**, tanpa perlu buka Studio.

Kenapa ada server kecil (Node.js), bukan HTML murni? Karena API Roblox tidak mengizinkan pemanggilan langsung dari JavaScript di browser (dibatasi CORS). Server ini berjalan **di komputermu sendiri** dan hanya meneruskan permintaan ke Roblox — API Key kamu tidak pernah dikirim ke server pihak ketiga mana pun.

## 1. Persiapan

- Node.js versi 18 ke atas.
- API Key Open Cloud dari [Creator Hub](https://create.roblox.com/dashboard/credentials) dengan izin:
  - **Access Permissions** → centang `Assets` (Read + Write / Create)
  - Jika untuk grup, key harus dibuat oleh akun yang punya izin di grup tersebut.

## 2. Menjalankan

```bash
cd roblox-model-uploader
npm install
npm start
```

Lalu buka `http://localhost:3000` di browser.

## 3. Pakai

1. Pilih file `.rbxm` atau `.rbxmx`.
2. Isi nama & deskripsi aset.
3. Pilih tujuan: **User** (akun pribadimu) atau **Group**, lalu isi ID-nya.
4. Masukkan API Key.
5. Klik **Upload ke Roblox** — tool akan menunggu sampai Roblox selesai memproses dan menampilkan link asetnya.

## Batasan dari Roblox (bukan dari tool ini)

- Ukuran file maksimum **20 MB** per aset.
- `.rbxm`/`.rbxmx` yang diedit di luar Roblox Studio (misalnya lewat tools eksternal) kadang ditolak atau tidak berfungsi normal.
- Ada kuota upload asosiasi ID-verifikasi (cek halaman [Usage guide for assets](https://create.roblox.com/docs/cloud/guides/usage-assets) untuk angka terbaru — kebijakan Roblox bisa berubah sewaktu-waktu).
- Fitur upload Model lewat Open Cloud ini masih tergolong baru dari pihak Roblox, jadi ada kemungkinan formatnya berubah di masa depan.

## Struktur file

```
roblox-model-uploader/
├── server.js         # proxy lokal ke Roblox Open Cloud API
├── public/
│   └── index.html    # antarmuka web
├── package.json
└── README.md
```
