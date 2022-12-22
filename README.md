# Capital Bike Sharing Data Analytics & Machine Learning Regression Analysis
*Purwadhika JCDSVL07 Final Project - Epsilon Squad*

Disusun oleh:
- Muhammad Adhi Raihanto
- Juan Josua Nainggolan
- Yudhapratama Nugraha Aryaputra

Pada akhir Program Job Connector Data Science di Purwadhika, kami diharuskan untuk melakukan analisa terkait data dari Capital Bike Sharing yaitu data demand persewaan sepeda dengan fitur-fitur lainnya seperti kondisi cuaca, kelembaban udara, data suhu, dan banyak fitur-fitur lainnya. Data yang digunakan adalah data time-series dimana setiap row mewakili satuan waktu tertentu dan dalam satuan waktu tersebut, terdapat record fitur-fitur yang ada.

# Business Problem Understanding

**Capital Bikeshare** adalah sebuah sistem *bikesharing* di Amerika Serikat yang memungkinkan pengguna untuk meminjam dan mengembalikan sepeda di berbagai lokasi di kota. Sistem ini dikelola oleh Motivate, sebuah perusahaan yang mengelola berbagai sistem *bikesharing* di seluruh dunia. Sistem ini memungkinkan pengguna untuk meminjam sepeda di suatu lokasi dan mengembalikannya di lokasi lain dan ditujukan untuk memberikan solusi bagi orang-orang yang ingin bersepeda namun tidak memiliki sepeda pribadi atau tidak memiliki tempat untuk menyimpannya.

Bisnis *bike sharing* merupakan bisnis yang memiliki impact yang luas terhadap masyarakat. Selain berimplikasi positif terhadap gaya hidup dan kesehatan masyarakat, *bike sharing* juga berkontribusi dalam mengurangi emisi karbon. Namun, tidak sedikit perusahaan yang gagal dan tidak dapat bertahan dalam waktu yang lama. Contoh yang dapat kita ambil adalah 'bicycle graveyards' di China dan beberapa kasus di kota-kota besar di Amerika. Kegagalan yang dialami oleh *bikesharing company* kebanyakan karena **oversupply**, **biaya maintenance yang mahal** dan **masalah dalam manajemen**. 

Dari beberapa literatur yang kami temukan, dapat kami simpulkan bahwa awal mula kegagalan berasal dari perencanaan yang salah. Dengan perencanaan yang baik, perusahaan akan mengetahui apa yang *customer* butuhkan dan seperti apa komposisi teknis yang harus dipersiapkan. Analisis permintaan penyewaan dari sepeda berdasarkan situasi tertentu dan **prediksi demand yang akurat** akan membantu perusahaan dalam **menambah profit dan meminimalisir resiko** sehinga bisa terus memberikan impact terhadap masyarakat. 

Dalam analisa ini, kami sebagai Tim Data Science dari Capital Bike Sharing Company diberikan tugas untuk mencari dan menganalisa apa saja informasi yang bisa didapatkan dari data yang diberikan serta apa saja improvement atau rekomendasi yang dapat diberikan baik kepada Team Operational Capital Bike Share atau Team Manajemen.

Berdasarkan dari latar belakang dan konteks permasalahan yang telah dijabarkan di atas, dapat ditarik sebuah pernyataan masalah yaitu:
*   Dengan menggunakan *data analytics*, seperti apa program atau sistem yang sesuai dengan behavior konsumen dari segmen yang berbeda serta dalam situasi apa program yang dijalankan dapat meningkatkan revenue?
*   Dengan menggunakan *machine learning*, dapatkah perusahaan memprediksi banyaknya demand penyewaan sepeda sehingga dapat meminimalisir stock sepeda yang berlebih atau kehilangan konsumen karena stock sepeda tidak tersedia? 

# Data Understanding
*   Dataset merupakan data jumlah penyewaan sepeda pada tahun 2011-2012 dari perusahaan Capital Bike Share di Washington DC, Amerika Serikat
*   Setiap baris data merepresentasikan informasi terkait penyewaan sepeda dalam satuan waktu (untuk database hour per jam dan untuk database day per hari)


**Attributes Information**
1. **instant** : Record index
2. **dteday** : Tanggal
3. **season** : Season / Musim (1:spring, 2:summer, 3:fall, 4:winter)
4. **yr** : Tahun (0: 2011, 1:2012)
5. **mnth** : Bulan (1 to 12)
6. **hr** : Jam (0 to 23) 
7. **holiday** : merepresentasikan pada hari tersebut libur selain weekend(data hasil ekstraksi dari Holiday Schedule Washington D.C)
8. **weekday** : Day of the week, hari sabtu dan minggu adalah 6 & 0
9. **workingday** :  Bila hari tersebut bukan hari libur atau weekend maka : 1, Selain itu is 0.
10. **weathersit** : (data di-extract dari situs Freemeteo)
    *   1: Clear, Few clouds, Partly cloudy, Partly cloudy
    *   2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
    *   3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
    *   4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog
11. **temp** : Temperature dalam Celsius yang telah melalui proses Normalisasi. The values are derived via (t-tmin)/(tmax-tmin), tmin=-8, t_max=+39 (only in hourly scale)
12. **atemp** : feels-like temperature dalam skala Celsius. The values are derived via (t-tmin)/(tmax-tmin), tmin=-16, t_max=+50 (only in hourly scale)
13. **hum** : Kelembaban yang telah melalui proses Normalisasi. The values are divided to 100 (max)
14. **windspeed** : Kecepatan angin. The values are divided to 67 (max)
15. **casual** : Jumlah dari user non-member
16. **registered** : Jumlah dari user member
17. **cnt** : Total dari jumlah user casual dan registered

# Data Preprocessing & Cleaning
* Menambah fitur month, year, weekday yang diambil dari dteday untuk memperudah analisis
* Menghapus feature atau kolom atemp, dteday, casual, dan registered karena tidak akan digunakan pada Machine Learning
* Melihat apakah ada missing values
* Melakukan correcting data types

# Data Analytics
* Persentase Kategori User
* Analisa Trend
* Analisa Durasi Bersepeda
* Hubungan Musim & Kondisi Cuaca dengan Jumlah Penyewaan
* Analisa Penyewaan per-Hari
* Analisa Penyewaan per-Bulan
* Analisa Hubungan Temperatur dengan Penyewaan
* Analisa Hari Libur Nasional & Libur Negara Bagian
* Analisa Stasiun & Dock

# Conclusion & Recommendation
**Data Analytics Executive Summary**

* Terdapat bukti yang kuat bahwa user dari layanan Capital Bikeshare di Washington D.C terbagi menjadi dua segmen dengan behavior yang berbeda dimana 81% user adalah Member atau Registered User sedangkan sisanya adalah Casual User. 
* Registered user menggunakan layanan sebagai sarana commuter untuk daily basis sedangkan casual user menggunakannya untuk sarana olahraga / rekreasi.
* Casual user berjumlah lebih sedikit namun memiliki durasi bersepeda lebih tinggi. 
* Casual user kebanyakan akan berkumpul di beberapa titik ketika hari libur / weekend.
* Terdapat korelasi yang kuat antara suhu yang dirasakan dengan jumlah penyewaan. User lebih prefer untuk bersepeda di kondisi hangat. 
* Terdapat ketimpangan antar dock yang terbangun. 

**Modelling Results Executive Summary**

*   Apabila diasumsikan perusahaan dalam keadaan business-as-usual menerapkan model linear regression dengan nilai RMSE 112, lalu perusahaan menggunakan model kami dengan nilai RMSE 79. Maka, perusahaan akan menerima benefit dengan selisih 33 unit. Jika diasumsikan kerugian dengan melihat median durasi rental yaitu selama 10 menit, dengan harga dasar 0,05 dollar/menit. Maka opportunity cost setiap sepedanya adalah 3 dollar/perjam. Sehingga, 33 X 3 dolar adalah 99. Perusahaan bisa menghindari kerugian sebesar 99 dolar/jamnya. Maka dalam sehari (dengan mempertimbangkan jam sibuk 10 jam/hari) perusahaan akan menghindari kerugian sebesar 990 dollar.
*   Berdasarkan feature importance, fitur 'hour' dan 'temp' dan 'workingday' menjadi hal yang paling berpengaruh terhadap total demand.
* Metrik evaluasi yang digunakan pada model adalah nilai RMSE & MAPE. Jika ditinjau dari nilai RMSE setelah  hyperparameter tuning, didapatkan hasil sebesar ~79, dapat disimpulkan bahwa bila nanti model ini digunakan untuk memperkirakan demand sepeda di washington d.c atau daerah degnan kondisi yang serupa pada rentang nilai maksimal 1000 demand/jam, maka perkiraan demand rata-rata akan meleset kurang lebih sebesar 79 buah sepeda dari demand seharusnya. Tetapi, tidak menutup kemungkinan juga prediksinya meleset lebih jauh.

**Rekomendasi Berdasarkan Hasil Analisa**

* Meningkatkan *registered user* dengan menjalin kerjasama dengan perusahaan di sekitar dock dengan program bike to work. Peningkatan awareness melalui kampanye perubahan iklim bisa diterapkan. 
* Menarik *registered user* baru menggunakan skema level beserta bonusnya (Silver, Gold, Platinum) berdasarkan jarak tempuh, waktu tempuh, dll sebagai Marketing Initiative oleh Team Marketing. 
* Melakukan pengembangan dock di titik titik teramai yang memiliki potensi untuk meningkatkan pengguna baru.
* Melakukan perubahan harga *basic rental* sesuai dengan fluktuasi *peak hour* atau ketika adanya *event* tertentu pada tanggal tertentu dengan tetap memperhitungkan *financial sensitivity analysis*
* Mempertimbangkan adanya iklan dalam aplikasi bagi pelanggan *casual* dan melakukan analisa harga *advertisement* sesuai dengan *traffic* aplikasi (perusahaan yang mengiklankan produk atau jasa-nya di kisaran *peak hour* akan terkena rate lebih mahal dibandingkan dengan *usual hour*). Hal ini akan berguna juga untuk menarik pelanggan *casual* menjadi *registered user*.
* Pemberian promo ketika Summer time, bisa menjadi opsi yang dijalankan. Ada promo yang diadakan dalam peak hour juga akan membantu dalam menambah user baru. Hour menjadi fitur yang berpengeruh signifikan. Maka dari itu pemberian promo ketika peak hour sebagai contoh ketika pagi dan sore di hari kerja dan pagi hari saat hari libur akan memberikan benefit.
* Menurut Shi & Sten (2020), *planning* merupakan hal yang sangat krusial dalam bike sharing. Hal yang paling penting adalah mengerti keperluan konsumen, supply dan realokasi sepeda. Terdapat ketimpangan antar dock yang terbangun. Maka dari itu, kami sarankan untuk Divisi Operasional agar memfokuskan alokasi sepeda pada stasiun dengan kebarangkatan yang tinggi. Serta menfokuskan armada untuk mengambil sepeda dari dock kedatangan tertinggi setiap pergantian weekend&weekday. Hal ini dilakukan untuk menghemat biaya operasional untuk redistribusi sepeda.

**Rekomendasi Perbaikan atau Pengembangan Model**

Kami sadar bahwa model yang kami buat memiliki keterbatasan. Maka dari itu, hal-hal yang dapat dilakukan untuk mengembangkan model agar lebih baik lagi adalah sebagai berikut:
* Menggunakan data terbaru yang dimiliki Capital Bike Share dimana data yang kami gunakan merupakan hasil observasi tahun 2011 - 2012 sehingga apabila dipakai untuk memprediksi tahun terkini akan lebih baik jika menggunakan data yang lebih dekat. Karena, situasi dan kondisi akan berbeda. Terlebih karena gap rentang waktu yang jauh.
* Jika memungkinkan, penambahan fitur yang lebih detail seperti jarak dock/station dengan moda transportasi massl lain. Seperti yang diketahui bahwa pengguna layanan sebagian besar melakukan aktifitas commuter. Informasi seperti itu akan sangat berharga bila kita ingin melakukan planning
* Penambahan banyak data, perlu dicoba untuk test set menggunakan data terbaru pada kurun waktu satu tahun. Training set dan test set yang diatur secara berkesniambungan akan memperlihatkan performa model yang lebih mendekati dengan prediksi aktual.
* Model yang sudah dibangun ini bisa dimanfaatkan untuk pengembangan pembuatan model lainnya. Contohnya seperti pembuatan model untuk memprediksi demand per-Dock/Station. Sehingga,  Pembuatan model ini dapat dipakai untuk melihat scope yang lebih kecil lagi. Dimana, hal tersebut akan menjadi meningkatkan efisiensi biaya. Distribusi sepeda akan jauh lebih baik dengan cost redistribusi yang dapat ditekan
* Model dapat berguna untuk perencanaan program apabila perusahaan ingin melakukan expansi ke wilayah dengan kondisi iklim yang mendekati lokus penelitian 
