# Capital Bike Sharing Data Analytics & Machine Learning Regression Analysis
*Purwadhika JCDSVL07 Final Project - Epsilon Squad*

Disusun oleh:
- Muhammad Adhi Raihanto
- Juan Josua Nainggolan
- Yudhapratama Nugraha Aryaputra

Pada akhir Program Job Connector Data Science di Purwadhika, kami diharuskan untuk melakukan analisa terkait data dari Capital Bike Sharing yaitu data demand persewaan sepeda dengan fitur-fitur lainnya seperti kondisi cuaca, kelembaban udara, data suhu, dan banyak fitur-fitur lainnya. Data yang digunakan adalah data time-series dimana setiap row mewakili satuan waktu tertentu dan dalam satuan waktu tersebut, terdapat record fitur-fitur yang ada.

# Contents
1. Business Problem Understanding
2. Data Understanding
3. Exploratory Data Analysis
4. Data Preprocessing & Cleaning
5. Data Analytics
6. Feature Engineering
7. Modeling
8. Conclusion & Suggestion

# Business Problem Understanding

**Capital Bikeshare** adalah sebuah sistem *bikesharing* di Amerika Serikat yang memungkinkan pengguna untuk meminjam dan mengembalikan sepeda di berbagai lokasi di kota. Sistem ini dikelola oleh Motivate, sebuah perusahaan yang mengelola berbagai sistem *bikesharing* di seluruh dunia. Sistem ini memungkinkan pengguna untuk meminjam sepeda di suatu lokasi dan mengembalikannya di lokasi lain dan ditujukan untuk memberikan solusi bagi orang-orang yang ingin bersepeda namun tidak memiliki sepeda pribadi atau tidak memiliki tempat untuk menyimpannya.

Bisnis *bike sharing* merupakan bisnis yang memiliki impact yang luas terhadap masyarakat. Selain berimplikasi positif terhadap gaya hidup dan kesehatan masyarakat, *bike sharing* juga berkontribusi dalam mengurangi emisi karbon. Namun, tidak sedikit perusahaan yang gagal dan tidak dapat bertahan dalam waktu yang lama. Contoh yang dapat kita ambil adalah 'bicycle graveyards' di China dan beberapa kasus di kota-kota besar di Amerika. Kegagalan yang dialami oleh *bikesharing company* kebanyakan karena **oversupply**, **biaya maintenance yang mahal** dan **masalah dalam manajemen**. 

Dari beberapa literatur yang kami temukan, dapat kami simpulkan bahwa awal mula kegagalan berasal dari perencanaan yang salah. Dengan perencanaan yang baik, perusahaan akan mengetahui apa yang *customer* butuhkan dan seperti apa komposisi teknis yang harus dipersiapkan. Analisis permintaan penyewaan dari sepeda berdasarkan situasi tertentu dan **prediksi demand yang akurat** akan membantu perusahaan dalam **menambah profit dan meminimalisir resiko** sehinga bisa terus memberikan impact terhadap masyarakat. 

Dalam analisa ini, kami sebagai Tim Data Science dari Capital Bike Sharing Company diberikan tugas untuk mencari dan menganalisa apa saja informasi yang bisa didapatkan dari data yang diberikan serta apa saja improvement atau rekomendasi yang dapat diberikan baik kepada Team Operational Capital Bike Share atau Team Manajemen.

Berdasarkan dari latar belakang dan konteks permasalahan yang telah dijabarkan di atas, dapat ditarik sebuah pernyataan masalah yaitu:
*   Dengan menggunakan *data analytics*, seperti apa program atau sistem yang sesuai dengan behavior konsumen dari segmen yang berbeda serta dalam situasi apa program yang dijalankan dapat meningkatkan revenue?
*   Dengan menggunakan *machine learning*, dapatkah perusahaan memprediksi banyaknya demand penyewaan sepeda sehingga dapat meminimalisir stock sepeda yang berlebih atau kehilangan konsumen karena stock sepeda tidak tersedia? 

# Data Understanding
*   Dataset merupakan data jumlah penyewaan sepeda pada tahun 2011-2012 di Amerika
*   Setiap baris data merepresentasikan informasi terkait penyewaan sepeda per hari
**Attributes Information**
| **Attribute** | **Data Type** | **Description** |
| --- | --- | --- |
| dteday | Datetime | date |
| hum | Float | Normalized humidity. The values are divided to 100 (max) |
| weathersit | Integer |  weather  <br>1 =  Clear, Few clouds, Partly cloudy, Partly cloudy<br>2 = Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist<br>3 = Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain +   Scattered clouds<br>4 = Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog|
| holiday | Integer | holiday or not |
| season | Integer | season <br>1: winter<br>2: spring<br>3: summer<br>4: fall |
| atemp | Float | Normalized feeling temperature in Celsius. The values are derived via (t-tmin)/(tmax-tmin), tmin=-16, t_max=+50 (only in hourly scale) |
| temp | Float | Normalized temperature in Celsius. The values are derived via (t-tmin)/(tmax-tmin), tmin=-8, t_max=+39 (only in hourly scale) |
| hr | Integer | hour (0 to 23) |
| casual | Integer | count of casual users |
| registered | Integer | count of registered users |
| cnt | Integer | count of total rental bikes including both casual and registered |

# Data Preprocessing
* Menambah fitur month, year, weekday yang diambil dari dteday untuk memperudah analisis
* Menghapus feature atemp, dteday, casual, dan registered karena tidak akan digunakan pada Machine Learning
* Menghapus nilai-nilai dari fitur yang bersifat tidak wajar
* Menghapus data-data outlier
* Melakukan encoding pada feature weathersit, season, dan weekday

# Conclusion & Recommendation
*   Berdasarkan pemodelan yang telah dilakukan, jam merupakan fitur yang paling berpengaruh terhadap jumlah rental sepeda, dilanjutkan dengan tahun dan hari.
*   Metrik evaluasi yang digunakan pada model adalah nilai RMSE, MAE & MAPE. Jika ditinjau dari nilai RMSE yang dihasilkan oleh model, yaitu sebesar 42.9, kita dapat menyimpulkan bahwa bila nanti model yang kita buat ini digunakan untuk memperkirakan jumlah rental sepeda baru pada rentang nilai seperti yang dilatih terhadap model (maksimal jumlah rental sepeda 645), maka perkiraan jumlah rental sepedanya rata-rata akan meleset kurang lebih sebesar 42.9 dari jumlah rental sepeda yang mungkin seharusnya. Tetapi, tidak menutup kemungkinan juga prediksinya meleset lebih jauh karena bias yang dihasilkan model masih cukup tinggi bila dilihat dari visualisasi antara jumlah rental sepeda aktual dan prediksi.
