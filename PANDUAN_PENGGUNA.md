# Panduan Pengguna RAN Ticket Matcher

Panduan ini ditujukan untuk pengguna operasional yang perlu mengecek hubungan antara daftar Site ID, data RAN, current alarm, dan incident ticket. Bahasa dibuat non-teknis agar bisa dipakai untuk operasional harian tanpa perlu memahami kode program.

## Tujuan aplikasi

RAN Ticket Matcher membantu pengguna menjawab pertanyaan praktis berikut:

- Site ID mana saja yang sedang dicek.
- NE atau perangkat RAN apa saja yang terkait dengan Site ID tersebut.
- Alarm aktif apa yang sedang muncul pada Site ID atau NE terkait.
- Apakah alarm tersebut sudah memiliki ticket.
- Ticket mana yang masih berjalan, tertutup, atau perlu ditindaklanjuti.

## Data yang diperlukan

Siapkan data berikut sebelum menjalankan aplikasi:

- Daftar Site ID yang ingin dicek.
- Data RAN atau daftar NE kandidat.
- Data incident ticket terbaru.
- Data current alarm terbaru.

Untuk current alarm, gunakan format template yang diberikan admin aplikasi. Jangan gunakan data produksi pada template contoh atau dokumen publik.

## Aturan penggunaan data

- Pastikan Site ID ditulis konsisten, misalnya tanpa spasi tambahan.
- Gunakan data ticket dan current alarm yang paling baru.
- Jangan mengubah nama kolom pada file masukan kecuali ada arahan dari admin aplikasi.
- Jangan membagikan URL CSV current alarm ke dokumen publik, chat umum, atau tiket GitHub.
- Jika ada data kosong, tetap jalankan pengecekan tetapi tandai hasilnya sebagai perlu validasi manual.

## Cara membaca hasil

File hasil biasanya berisi beberapa bagian atau sheet berikut:

- `Input_SITE_ID`: daftar Site ID yang diminta pengguna.
- `NE_Candidates`: daftar kandidat NE yang ditemukan untuk setiap Site ID.
- `Output`: hasil gabungan Site ID, NE, alarm, dan ticket.
- `Current Alarm`: daftar alarm aktif yang cocok dengan Site ID atau NE.
- `Current Alarm Ticket Check`: pengecekan apakah current alarm sudah memiliki ticket yang sesuai.

Kolom penting yang perlu diperhatikan:

- `SITE_ID`: Site ID yang sedang dicek.
- `NE_NAME`: nama NE atau perangkat terkait.
- `Current Alarm`: alarm aktif dari data current alarm.
- `Collect alarm time`: waktu alarm dikumpulkan dari sumber data.
- `Ticket ID`: nomor ticket yang cocok, jika ada.
- `TYPE` dan `ALARM`: kategori ticket atau alarm pada ticket.
- `Ticket Status`: status ticket saat data diproses.

## Cara mengambil keputusan dari hasil

Gunakan panduan berikut saat membaca output:

- Ada current alarm dan ada ticket aktif: lanjutkan monitor ticket dan pastikan ticket menangani alarm yang sama.
- Ada current alarm tetapi tidak ada ticket: perlu eskalasi atau pembuatan ticket sesuai prosedur operasional.
- Ada ticket tetapi tidak ada current alarm: cek apakah alarm sudah clear atau data current alarm belum terbaru.
- Banyak NE kandidat untuk satu Site ID: validasi NE yang benar sebelum mengambil keputusan.
- Status ticket tertutup tetapi alarm masih aktif: perlu pengecekan ulang karena ada potensi ticket ditutup terlalu cepat.

## Checklist sebelum membagikan hasil

- Pastikan file input berasal dari periode yang benar.
- Pastikan current alarm sudah diperbarui.
- Cek apakah jumlah Site ID pada hasil sesuai dengan daftar input.
- Cek baris dengan current alarm tetapi tanpa ticket.
- Cek baris dengan ticket tertutup tetapi current alarm masih muncul.
- Simpan file hasil dengan nama yang menyertakan tanggal atau jam proses.

## Batasan yang perlu diketahui

- Aplikasi hanya sebaik data yang diberikan. Jika sumber ticket atau alarm belum terbaru, hasil juga bisa tertinggal.
- Site ID yang tidak ditemukan pada data RAN perlu dicek manual.
- Perbedaan penamaan NE dapat menyebabkan alarm dan ticket tidak cocok otomatis.
- Hasil aplikasi adalah alat bantu operasional, bukan pengganti validasi akhir oleh tim terkait.

## Dukungan

Untuk bantuan penggunaan, update, atau laporan masalah, hubungi:

- Developer: hadifauzanhanif@gmail.com
- Dukungan apresiasi: https://saweria.co/HDfauzan
