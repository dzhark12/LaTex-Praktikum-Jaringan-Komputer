# Template LaTeX Laporan Praktikum Jaringan Komputer (IF25-21008)

Template LaTeX untuk laporan praktikum **Jaringan Komputer IF25-21008**, Program Studi Teknik Informatika, Institut Teknologi Sumatera (ITERA).

Template ini dibuat semirip mungkin dengan berkas resmi `Template Laporan Praktikum Jarkom IF25-21008 (2026).docx`. Tata letak, ukuran font, warna, dan posisi setiap elemen diukur langsung dari hasil render dokumen Word, lalu disamakan hingga selisihnya hanya beberapa piksel.

## Tujuan Fork

Struktur repo ini disederhanakan agar lebih praktis digunakan. Isi laporan, termasuk langkah-langkah dokumentasi, digabung dalam satu `template.tex`, jadi pengguna tidak perlu membuat file baru setiap kali menambah langkah. Folder gambar sudah disediakan untuk menyimpan aset laporan. Data utama dan daftar referensi juga mudah disesuaikan untuk setiap laporan. Dengan struktur ini, satu salinan repo dapat digunakan kembali untuk mengerjakan laporan berikutnya tanpa perlu meng-clone repo berulang kali.

## Daftar Isi

- [Tujuan Fork](#tujuan-fork)
- [Kontributor](#kontributor)
- [Cara Memakai](#cara-memakai)
- [Menambah Referensi dan Sitasi](#menambah-referensi-dan-sitasi)
- [Kompilasi](#kompilasi)
- [Font](#font)
- [Struktur Proyek](#struktur-proyek)
- [Catatan](#catatan)

## Kontributor

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/hanungdata-prog">
        <img src="https://github.com/hanungdata-prog.png" width="90" alt="Hanung Akbar Pramusintho"><br>
        <b>Hanung Akbar Pramusintho</b>
      </a><br>
      <sub>Penggagas proyek</sub>
    </td>
    <td align="center">
      <a href="https://github.com/Jeremi16">
        <img src="https://github.com/Jeremi16.png" width="90" alt="Jeremi Pison Efrat Sianturi"><br>
        <b>Jeremi Pison Efrat Sianturi</b>
      </a><br>
      <sub>Pengembang lanjutan &amp; penyempurnaan tampilan</sub>
    </td>
  </tr>
</table>

- **Hanung Akbar Pramusintho** ([@hanungdata-prog](https://github.com/hanungdata-prog)) mencetuskan ide membuat versi LaTeX dari template laporan resmi.
- **Jeremi Pison Efrat Sianturi** ([@Jeremi16](https://github.com/Jeremi16)) melanjutkan pengembangannya dan menyempurnakan tampilan sampul, halaman judul, header, kotak rangkuman, hingga warna, sampai identik dengan template Word.

## Cara Memakai

| Berkas | Yang diisi |
|---|---|
| `main.tex` | Kerangka dokumen dan urutan pemanggilan isi laporan |
| `config.sty` | Identitas peserta/kelompok, kelas, asisten, data praktikum, serta gaya dokumen |
| `chapters/template.tex` | Rangkuman, dokumentasi, alat dan bahan, serta tugas. Tambahkan langkah dokumentasi langsung di daftar langkah. |
| `Referensi.bib` | Entri sumber pustaka dalam format BibTeX, diproses oleh Biber |
| `figure/` | Simpan logo dan gambar umum di sini; gambar dokumentasi disimpan di subfolder sesuai pertemuan |

### Mengisi Data Utama

Data utama setiap laporan diisi di bagian `Data laporan` dalam `config.sty`. Ganti nilai contoh dengan data laporan, misalnya:

```latex
\newcommand{\namapeserta}{Jane Doe}
\newcommand{\nim}{124140xxx}
\newcommand{\kelas}{RA}
\newcommand{\pertemuan}{1}
\newcommand{\judul}{Cabling dan FTP}
\newcommand{\bulantahun}{September 2026}
```

Nama asisten, anggota kelompok, dan catatan anggota juga diatur di bagian yang sama. Untuk laporan individu, isi `\daftaranggota` dengan satu nama dan NIM saja, misalnya `Jane Doe (124140xxx)`. Untuk laporan kelompok, tulis setiap anggota pada baris baru dan pisahkan dengan `\\`. Kosongkan `\catatananggota` jika catatan tambahan tidak diperlukan. Judul panjang boleh dipecah dengan `\\` di `\judul`.

Isi laporan tidak dipecah menjadi file untuk setiap langkah. Salin blok `\item` di bagian dokumentasi dalam `chapters/template.tex` untuk menambahkan langkah baru.

Simpan gambar dokumentasi di subfolder sesuai pertemuan, yaitu `figure/1/` sampai `figure/12/`. Logo dan gambar umum berada langsung di `figure/`.

### Menambah Referensi dan Sitasi

Tambahkan setiap sumber sebagai entri di `Referensi.bib`. Contoh buku:

```bibtex
@book{namaKunci,
  author    = {Nama Belakang, Nama Depan},
  title     = {Judul Buku},
  year      = {2024},
  publisher = {Nama Penerbit},
  location  = {Kota Terbit}
}
```

`namaKunci` harus unik. Untuk mengutip sumber dalam isi laporan, tulis `\cite{namaKunci}` di `chapters/template.tex`, misalnya `Menurut \cite{forouzan2007}, ...`. Saat ini `main.tex` memakai `\nocite{*}`, jadi semua entri di `Referensi.bib` tetap tercetak, termasuk sumber yang belum dikutip di isi.

Daftar referensi memakai format author–year tanpa nomor. Setelah mengubah berkas `.bib`, kompilasi ulang dengan `latexmk -xelatex main.tex` agar Biber memperbarui daftar tersebut.

## Kompilasi

Template ini wajib dikompilasi dengan **XeLaTeX** (misalnya lewat MiKTeX di Windows).

**Cara 1: manual.** Jalankan XeLaTeX, Biber, lalu XeLaTeX lagi agar daftar referensi diperbarui.

```bash
xelatex main.tex
biber main
xelatex main.tex
```

**Cara 2: sekali perintah dengan `latexmk` (disarankan).**

```bash
latexmk -xelatex main.tex
```

**Cara 3: kompilasi otomatis setiap kali berkas disimpan.**

```bash
latexmk -xelatex -pvc main.tex
```

## Font

Template memakai font Garamond, Arial, Arial Black, Bernard MT Condensed, dan Cambria. Ringkasan berikut mengikuti ukuran yang diatur di `main.tex` dan `config.sty`.

| Bagian | Font dan ukuran |
|---|---|
| Isi laporan | Garamond 12 pt, `\linespread{1.5}` |
| Caption gambar dan tabel | Garamond 8 pt |
| Header | Arial Black 7 pt di kiri dan 8,05 pt di kanan; nomor halaman 8 pt |
| Sampul | Cambria 14 pt; Garamond 12,3, 18,5, dan 14 pt; Bernard MT Condensed 24 pt; Arial Black 10 dan 52 pt |
| Halaman judul dalam | Arial Black 23,5 pt warna abu-abu; teks anggota dan alamat Garamond 9,6 pt |
| Kotak rangkuman | Judul Arial Bold Italic 12 pt, pengantar 10 pt, isi Garamond 9,6 pt |
| Judul bagian | Garamond Bold 20 pt; subbagian 11 pt Bold |
| Referensi | Judul Arial Black 15 pt; entri Garamond 11 pt, tanpa miring dan tanpa nomor |

Font tersebut perlu tersedia pada sistem yang digunakan untuk kompilasi. Ketersediaan font dapat berbeda di Windows, Linux, dan Overleaf.

## Struktur Proyek

```text
.
├── main.tex                 # Kerangka dokumen
├── config.sty               # Data laporan dan pengaturan gaya
├── Referensi.bib            # Sumber pustaka
├── chapters/
│   └── template.tex         # Seluruh isi laporan
└── figure/
    ├── contoh-gambar.png    # Gambar umum
    ├── logo-fti.png
    ├── logo-if.png
    ├── logo-itera.png
    ├── logotera.png
    ├── 1/                   # Gambar pertemuan 1
    ├── 2/                   # Gambar pertemuan 2
    ├── ...
    └── 12/                  # Gambar pertemuan 12
```

Folder pertemuan berisi `.gitkeep` agar tetap tersedia di Git saat masih kosong.

## Catatan

- Gambar dokumentasi memakai perintah `\gambarpengganti`. Jika berkas gambarnya belum ada, yang tampil adalah kotak bertuliskan "Gambar dokumentasi belum tersedia", sehingga kompilasi tidak gagal.
- Helper opsional: `\gbr{nama-file}{caption}` menyisipkan `figure/<nama-file>.png` dari folder utama. Untuk gambar di subfolder pertemuan, gunakan `\gambarpengganti{figure/<nomor-pertemuan>/<nama-file>.png}`. Perintah `\topik{judul}` membuat subjudul tebal kecil di dalam langkah.
- Langkah kedua dalam `chapters/template.tex` memiliki `\newpage` agar mulai di halaman baru seperti di template Word. Hapus baris itu jika tidak diperlukan.
