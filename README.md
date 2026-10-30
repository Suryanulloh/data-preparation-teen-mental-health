# Data Preparation dan Visualisasi BI: Dataset Kesehatan Mental Remaja

Proyek persiapan data (data preparation) dan visualisasi Business Intelligence pada dataset kesehatan mental remaja, dikerjakan terkait sertifikasi LSP Universitas Gunadarma (Data Preparation for Business Processes). Dataset awal sengaja berisi data yang rusak (duplikat, nilai kosong, penulisan tidak konsisten, dan nilai tidak wajar), sehingga fokus proyek ini adalah membersihkan, memvalidasi, dan menyiapkan data sebelum dianalisis.

## Tujuan
Menyiapkan data yang bersih dan siap analisis, lalu menggali hubungan antara penggunaan media sosial, kualitas tidur, stres, kecemasan, dan status depresi pada remaja.

## Isi repositori
| File | Keterangan |
| --- | --- |
| `teen-mental-health.ipynb` | Notebook data preparation dan visualisasi BI |
| `Teen_Mental_Health_Dataset_DIRUSAK.csv` | Dataset awal (1.260 baris, 13 kolom) yang disediakan untuk keperluan asesmen LSP |
| `power bi.pbix` | Laporan Power BI sederhana (latihan terpisah, lihat bagian Dashboard Power BI) |

## Data
- Data awal: 1.260 baris dan 13 kolom.
- Kolom utama: usia, jenis kelamin, jam media sosial per hari, platform yang dipakai, jam tidur, waktu layar sebelum tidur, performa akademik, aktivitas fisik, level interaksi sosial, level stres, level kecemasan, level kecanduan, dan label depresi (0 = tidak, 1 = ya).

## Tahapan persiapan data
| Tahap | Tindakan | Hasil |
| --- | --- | --- |
| 1. Duplikat | Menghapus baris yang identik di semua kolom | 60 baris dihapus, tersisa 1.200 |
| 2. Nilai kosong | Menghapus baris yang mengandung NaN (144 pada jam media sosial, 144 pada platform, 140 pada jam tidur, 144 pada performa akademik) | Tersisa 1.056 baris |
| 3. Standardisasi teks | Menyeragamkan penulisan kolom `platform_usage` (misalnya "Instgrm", "instagram!!!", "tik_tok") menjadi instagram, tiktok, dan both | 3 kategori konsisten |
| 4. Validasi rentang | Menghapus usia negatif dan jam tidur lebih dari 12 jam | Tersisa 972 baris |
| 5. Encoding | Ordinal (interaksi sosial), biner (gender), one-hot (platform) | Dataset akhir 972 baris dan 15 kolom |

Dataset akhir tidak memiliki nilai kosong maupun duplikat.

## Visualisasi (Business Intelligence)
Distribusi status depresi, rata-rata stres per level interaksi sosial, heatmap korelasi, jumlah pengguna per platform, tren stres dan kecemasan per durasi media sosial, pie chart depresi, word cloud platform, dan statistik deskriptif.

## Temuan utama
- **Profil responden:** usia 13-19 tahun (rata-rata 15,9), rata-rata 4,55 jam media sosial per hari dan 6,45 jam tidur.
- **Platform:** pengguna Instagram (333), TikTok (322), dan keduanya (317) hampir seimbang.
- **Status depresi:** 24 dari 972 responden (2,5%) terindikasi depresi, sehingga kelasnya sangat tidak seimbang.
- **Hubungan variabel:** korelasi label depresi dengan jam media sosial (0,18), stres (0,17), kecemasan (0,18), dan jam tidur (-0,19) tergolong lemah. Variabel lain mendekati nol.
- **Tren per durasi:** rata-rata stres naik dari 5,34 (0-2 jam) menjadi 5,83 (8+ jam), dan kecemasan dari 5,05 menjadi 6,00. Polanya naik tetapi tidak linier dan selisihnya kecil.

## Dashboard Power BI
File `power bi.pbix` adalah laporan Power BI sederhana dari latihan terpisah dan tidak memakai dataset kesehatan mental di atas. Laporan ini berisi satu halaman dengan dua grafik yang memakai data kemiskinan per provinsi (kemiskinan, umur harapan hidup, dan tingkat pengangguran terbuka). Data sudah tertanam di dalam file, jadi file ini bisa dibuka langsung dengan Power BI Desktop. Laporan ini masih berupa versi awal yang akan dikembangkan.

## Keterbatasan
- Hubungan antar variabel bersifat deskriptif dan tidak menunjukkan sebab-akibat.
- Korelasi antar kolom platform hasil one-hot encoding (sekitar -0,5) hanya akibat teknik encoding, bukan temuan.
- Baris dengan nilai kosong dihapus, bukan diisi (imputasi), sehingga sekitar 23% data awal tidak terpakai.
- Kelas depresi sangat tidak seimbang, sehingga perlu penanganan khusus bila dilanjutkan ke pemodelan.

## Teknologi
Python, Google Colab, pandas, NumPy, Matplotlib, Seaborn, WordCloud, Power BI

## Cara menjalankan
1. Buka notebook `teen-mental-health.ipynb` di Google Colab.
2. Unggah `Teen_Mental_Health_Dataset_DIRUSAK.csv` ke `/content/` (atau ubah jalur file di sel pertama).
3. Jalankan sel secara berurutan.

## Penulis
Ilham Suryanulloh, Universitas Gunadarma
