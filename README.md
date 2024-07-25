# Proyek AB Testing Mengoptimalkan Sistem Rekomendasi di Platform Belanja Online Internasional
# Pendahuluan <a id='intro'></a>

Suatu peristiwa pada 7 Desember 2020, sebuah eksperimen A/B diluncurkan oleh toko online internasional untuk menguji perubahan terkait penyempurnaan sistem rekomendasi. Nama eksperimen ini adalah "recommender_system_test" dimana sistem terbagi menjadi dua kelompok: Kelompok A sebagai kontrol dan Kelompok B yang melibatkan pengenalan cara melakukan pembayaran baru.

# Tujuan <a id='GoalSet'></a>

- Tujuan Uji Coba: Meneliti dampak perubahan dalam menghadirkan sistem rekomendasi yang lebih unggul dan efektif serta ditingkatkan.
    - Hasil yang Diharapkan: Dalam waktu 14 hari sejak pendaftaran, pengguna akan menunjukkan peningkatan konversi ke tampilan halaman produk (event product_page), tampilan kartu produk (event product_card), dan pembelian (event purchase). Setiap tahap dari funnel product_page → product_card → purchase harus mengalami peningkatan minimal 10%.
    
# Tahapan yang dilakukan<a id='StepbyStep'></a>

Tahapan-tahapan yang akan dilakukan adalah sebagai berikut:

**1. Mengeksplorasi Data:**

   - Konversi Tipe Data: cek semua type data apakah ada yang dikonversi tipe data pada setiap file data yang diberikan.
   - Data Hilang dan Duplikat: Menemukan adanya nilai hilang atau duplikat dalam dataset. Jika ditemukan, buat penjelasan sifat dan dampaknya terhadap analisis.

**2. Melakukan analisis data eksploratif (EDA):**

   - Distribusi jumlah event per pengguna: menelaah lebih dalam apakah jumlah event per pengguna didistribusikan secara merata diantara sampel A dan sampel B.
   - Pengguna yang masuk didalam kedua sampel: mengidentifikasi apakah ada pengguna yang masuk dikedua sampel tersebut, dan jika ada, mengevaluasi dampaknya terhadap hasil uji coba.
   - Distribusi jumlah event per hari: menganalisis cara distribusi jumlah event berdasarkan hari.
   
**3. Menganalisis Konversi diBerbagai Tahap Funnel:**

   - Mengidentifikasi dan menganalisis tingkat konversi pengguna pada setiap tahapan funnel, mulai dari tampilan halaman produk (product_page) ke tampilan kartu produk (product_card) hingga pembelian (purchase)
   
**4. Evaluasi Hasil A/B Test:**

   - Interpretasi hasil A/B test: menyajikan temuan dan kesimpulan dari hasil uji coba A/B, apakah terdapat perbedaan yang signifikan diantara kelompok A (kontrol) dan B (cara melakukan pembayaran baru).
   - Penggunaan Z-Criterion: menggunakan z-criterion untuk memeriksa perbedaan statistik antara proporsi pada kedua kelompok.
   
**Deskripsi Teknis**

1. Test Name: `recommender_system_test`
2. Kelompok: A (kontrol), B (cara melakukan pembayaran baru)
3. Tanggal Peluncuran: 7 Desember 2020
4. Tanggal Berhenti Menerima Pengguna Baru: 21 Desember 2020
5. Tanggal Berakhir: 1 Januari 2021
6. Audience: 15% dari pengguna baru dari wilayah UE (Uni Eropa)
7. Tujuan Uji Coba: Menguji perubahan terkait pengenalan sistem rekomendasi yang ditingkatkan.
8. Hasil yang Diharapkan: Dalam waktu 14 hari sejak pendaftaran, pengguna akan menunjukkan peningkatan konversi ke tampilan halaman produk (event product_page), tampilan kartu produk (event product_card), dan pembelian (event purchase). Setiap tahap dari funnel product_page → product_card → purchase harus mengalami peningkatan minimal 10%.
9. Jumlah Peserta yang Diharapkan: 6000 orang.

**Deskripsi Data**

* `ab_project_marketing_events_us.csv` — kelendar event marketing untuk tahun 2020
* `final_ab_new_users_upd_us.csv` — seluruh pengguna yang mendaftar pada toko online dari tanggal 7 Desember - 21 Desember tahun 2020
* `final_ab_events_upd_us.csv` — seluruh event untuk pengguna baru pada periode 7 Desember 2020 hingga 1 Januari 2021.
* `final_ab_participants_upd_us.csv` — tabel terdiri dari test partisipasi

**field record dari dataset `ab_project_marketing_events_us.csv`:**

* `name` — nama marketing event
* `regions` — wilayah mana yang akan diselenggarakan(ad campaign)
* `start_dt` — tanggal mulai
* `finish_dt` — tanggal berakhir(ad campaign)

**field record dari dataset `final_ab_new_users_upd_us.csv`:**

* `user_id`
* `first_date` — tanggal daftar
* `region`
* `device` — perangkat yang digunakan untuk daftar

**field record dari dataset `final_ab_events_upd_us.csv`:**

* `user_id`
* `event_dt` — tanggal dan waktu event
* `event_name` — jenis event
* `details` — data tambahan terhadap event (contohnya seperti: order total dalam kurs dollar untuk kolom event purchase)

**field record dari dataset `final_ab_participants_upd_us.csv`:**

* `user_id`
* `ab_test` — nama test
* `group` — kelompok test yang dimiliki
