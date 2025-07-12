Tingkat Pengangguran Berdasarkan Umur 2021-2024

Notebook ini melakukan analisis dan pengelompokan (clustering) kelompok umur berdasarkan data pengangguran dari tahun 2021 hingga 2024 untuk mengidentifikasi pola pengangguran yang serupa antar usia

Project Overview

Tujuan Proyek: Menganalisis dan mengelompokkan (clustering) kelompok umur berdasarkan pola data pengangguran dari tahun 2021 hingga 2024 untuk mengidentifikasi segmen-segmen kelompok umur yang memiliki karakteristik pengangguran yang serupa. Hasil clustering ini bertujuan untuk memberikan pemahaman yang lebih mendalam mengenai dinamika pengangguran di berbagai rentang usia.

Latar Belakang & Permasalahan: Data pengangguran seringkali disajikan secara agregat atau hanya berdasarkan tahun. Namun, tingkat dan pola pengangguran dapat bervariasi signifikan antar kelompok umur karena faktor-faktor seperti tingkat pendidikan, pengalaman kerja, kondisi pasar kerja spesifik untuk usia tertentu, dan transisi kehidupan (misalnya, lulus sekolah, memasuki angkatan kerja, mendekati masa pensiun). Memahami perbedaan ini penting untuk perumusan kebijakan dan program ketenagakerjaan yang lebih tepat sasaran. Permasalahannya adalah bagaimana mengidentifikasi kelompok-kelompok umur yang menunjukkan tren atau tingkat pengangguran yang serupa secara objektif berdasarkan data historis.

Pendekatan: Proyek ini menggunakan pendekatan analisis data kuantitatif dengan fokus pada clustering data pengangguran berdasarkan kelompok umur. Langkah-langkah yang dilakukan meliputi:

Pengumpulan Data: Menggunakan data jumlah pengangguran per kelompok umur dari tahun 2021-2024.

Pra-pemrosesan Data: Melakukan standardisasi data numerik untuk memastikan setiap fitur (data tahunan) memiliki kontribusi yang setara dalam proses clustering.

Penentuan Jumlah Cluster Optimal: Menggunakan metode Elbow untuk membantu menentukan jumlah cluster (k) yang paling sesuai untuk data.

Implementasi K-Means Clustering: Menerapkan algoritma K-Means dengan jumlah cluster yang telah ditentukan pada data yang distandardisasi.

Analisis dan Interpretasi Hasil: Menganalisis karakteristik setiap cluster yang terbentuk, termasuk menghitung rata-rata pengangguran per tahun untuk setiap cluster, dan memvisualisasikan hasilnya untuk mendapatkan insight mengenai perbedaan pola pengangguran antar kelompok umur.

Analysis Process
Proses analisis dalam proyek ini dilakukan melalui serangkaian langkah sistematis untuk mencapai tujuan clustering kelompok umur berdasarkan data pengangguran. Setiap langkah menggunakan metode dan teknik spesifik dengan alasan yang jelas:

Pengambilan Data Numerik untuk Clustering:

Metode/Teknik: Seleksi kolom DataFrame.
Alasan: Algoritma clustering (seperti K-Means) beroperasi pada data numerik. Kolom yang berisi jumlah pengangguran per tahun ('Pengangguran_2021', 'Pengangguran_2022', 'Pengangguran_2023', 'Pengangguran_2024') adalah fitur yang relevan untuk mengukur pola pengangguran dari waktu ke waktu, sementara kolom 'Kelompok_Umur' bersifat kategorikal dan digunakan sebagai identifikasi kelompok.
Standardisasi Data:

Metode/Teknik: StandardScaler dari library scikit-learn.
Alasan: K-Means Clustering menggunakan perhitungan jarak (misalnya Euclidean distance) untuk menentukan kedekatan antar titik data. Jika fitur memiliki skala yang sangat berbeda (misalnya, jumlah pengangguran bisa jutaan, sementara fitur lain bisa puluhan), fitur dengan nilai yang lebih besar akan mendominasi perhitungan jarak, meskipun perubahannya secara proporsional mungkin tidak signifikan. Standardisasi mengubah data sehingga memiliki rata-rata 0 dan standar deviasi 1, memastikan bahwa setiap fitur memberikan kontribusi yang setara dalam perhitungan jarak dan proses clustering.
Penentuan Jumlah Cluster Optimal:

Metode/Teknik: Elbow Method.
Alasan: K-Means memerlukan penentuan jumlah cluster (k) di awal. Elbow Method adalah teknik heuristik yang populer untuk membantu memilih nilai k yang tepat. Metode ini melibatkan perhitungan inertia (sum of squared distances of samples to their closest cluster center) untuk berbagai nilai k. Plot antara k dan inertia biasanya menunjukkan penurunan inertia yang tajam pada awalnya, dan kemudian melambat membentuk "siku" (elbow). Titik siku ini sering dianggap sebagai jumlah cluster yang optimal, karena menambah lebih banyak cluster setelah titik ini tidak lagi memberikan pengurangan inertia yang signifikan.
Implementasi K-Means Clustering:

Metode/Teknik: Algoritma K-Means dari library scikit-learn.
Alasan: K-Means adalah algoritma clustering partisional yang efisien dan relatif mudah diinterpretasikan. Algoritma ini bertujuan untuk membagi n observasi menjadi k cluster, di mana setiap observasi termasuk ke dalam cluster dengan rata-rata terdekat. Ini sesuai dengan tujuan proyek untuk mengelompokkan kelompok umur berdasarkan kedekatan pola pengangguran mereka selama empat tahun terakhir. random_state digunakan untuk memastikan hasil yang konsisten setiap kali kode dijalankan.
Penambahan Hasil Clustering ke DataFrame:

Metode/Teknik: Membuat kolom baru dalam DataFrame.
Alasan: Menambahkan label cluster ke DataFrame asli memungkinkan pengaitan hasil clustering dengan informasi kelompok umur yang sesuai. Ini memfasilitasi analisis dan interpretasi karakteristik setiap cluster dalam konteks kelompok umur yang termasuk di dalamnya.
Analisis Karakteristik Cluster:

Metode/Teknik: Grouping (menggunakan groupby()) dan agregasi (menggunakan mean()), serta visualisasi (menggunakan matplotlib/seaborn).
Alasan: Setelah cluster terbentuk, penting untuk memahami apa yang membedakan satu cluster dari yang lain. Menghitung rata-rata nilai fitur (jumlah pengangguran per tahun) untuk setiap cluster memberikan ringkasan karakteristik numerik dari masing-masing kelompok. Visualisasi, seperti bar chart dari rata-rata cluster, membantu dalam membandingkan profil pengangguran antar cluster secara visual, mempermudah identifikasi tren dan perbedaan signifikan. Plot hasil clustering terhadap salah satu fitur (misalnya Pengangguran 2024) juga membantu melihat sebaran data dan bagaimana kelompok umur terdistribusi dalam cluster yang berbeda.
**Insight & Findings
**Berdasarkan hasil clustering dan analisis karakteristik setiap cluster, ditemukan beberapa insight dan temuan menarik mengenai pola pengangguran di berbagai kelompok umur dari tahun 2021 hingga 2024:

Identifikasi Tiga Pola Pengangguran Utama: Algoritma K-Means berhasil mengelompokkan kelompok umur ke dalam tiga cluster yang distinct, menunjukkan adanya tiga pola atau tingkat pengangguran yang berbeda selama periode 2021-2024:

Cluster 1 (Pengangguran Sangat Tinggi): Cluster ini didominasi oleh kelompok umur 20-24 tahun. Kelompok ini secara konsisten memiliki rata-rata jumlah pengangguran tertinggi dibandingkan semua kelompok umur dan cluster lainnya di setiap tahun dari 2021 hingga 2024. Ini mengindikasikan bahwa kelompok usia muda yang baru memasuki pasar kerja menghadapi tantangan pengangguran yang paling signifikan.

Cluster 2 (Pengangguran Tinggi): Cluster ini terdiri dari kelompok umur 15-19 tahun dan 25-29 tahun. Meskipun tidak setinggi Cluster 1, kelompok ini juga menunjukkan rata-rata jumlah pengangguran yang cukup tinggi, terutama di tahun-tahun awal data. Pola ini menunjukkan bahwa kelompok usia transisi dari pendidikan ke dunia kerja (15-19) dan kelompok usia awal karir (25-29) juga menghadapi tingkat pengangguran yang perlu perhatian serius.

Cluster 0 (Pengangguran Sedang hingga Rendah): Cluster terbesar ini mencakup kelompok umur 30-34, 35-39, 40-44, 45-49, 50-54, 55-59, dan 60+ tahun. Kelompok-kelompok ini secara umum memiliki rata-rata jumlah pengangguran yang jauh lebih rendah dibandingkan Cluster 1 dan 2. Meskipun ada fluktuasi antar tahun, tren pengangguran di cluster ini cenderung lebih stabil atau menurun, menunjukkan bahwa kelompok usia yang lebih matang dengan pengalaman kerja lebih banyak cenderung memiliki tingkat pengangguran yang lebih rendah.

Konsistensi Pola Pengangguran Kelompok Muda: Analisis rata-rata cluster per tahun menunjukkan bahwa perbedaan tingkat pengangguran antar cluster ini relatif konsisten dari tahun ke tahun. Kelompok usia muda (Cluster 1 dan 2) secara struktural memiliki jumlah pengangguran yang lebih tinggi dibandingkan kelompok usia yang lebih tua (Cluster 0) sepanjang periode analisis 2021-2024.

Dominasi Kelompok Usia 20-24 tahun dalam Total Pengangguran: Visualisasi persentase pengangguran per kelompok umur per tahun (stacked horizontal bar chart) mengkonfirmasi temuan clustering. Kelompok umur 20-24 tahun secara konsisten menyumbang persentase terbesar dari total jumlah pengangguran nasional di setiap tahun dari 2021 hingga 2024. Diikuti oleh kelompok umur 15-19 tahun dan 25-29 tahun. Ini memperkuat insight bahwa permasalahan pengangguran paling krusial berada pada segmen usia muda hingga awal dewasa.

Perubahan Proporsi Antar Kelompok Usia Lebih Tua: Meskipun menyumbang persentase yang lebih kecil dari total pengangguran, visualisasi persentase juga dapat menunjukkan pergeseran proporsi antar kelompok usia dalam Cluster 0 dari tahun ke tahun, meskipun perubahannya tidak sedramatis pada cluster usia muda.

Temuan-temuan ini memberikan bukti empiris bahwa data pengangguran di Indonesia dari 2021-2024 tidak merata di seluruh kelompok umur, melainkan terkonsentrasi secara signifikan pada usia muda (15-29 tahun), dengan puncaknya di usia 20-24 tahun. Insight ini penting untuk perumusan strategi dan kebijakan ketenagakerjaan yang lebih terfokus.

Conclusion & Recommendation

Analisis clustering data pengangguran berdasarkan kelompok umur dari tahun 2021 hingga 2024 dengan menggunakan algoritma K-Means secara jelas mengidentifikasi tiga segmen utama kelompok umur dengan pola pengangguran yang berbeda. Temuan kunci menunjukkan bahwa kelompok usia muda (15-29 tahun), khususnya usia 20-24 tahun, secara konsisten memiliki tingkat pengangguran yang jauh lebih tinggi dibandingkan kelompok usia yang lebih matang (30+ tahun). Ini mengindikasikan adanya tantangan struktural dalam transisi dari pendidikan ke dunia kerja dan di awal karir bagi generasi muda. Dominasi kelompok usia 20-24 tahun dalam kontribusi terhadap total pengangguran nasional sepanjang periode analisis memperkuat kesimpulan ini.

Rekomendasi:

Berdasarkan temuan di atas, berikut adalah beberapa rekomendasi yang konkret, dapat ditindaklanjuti (actionable), dan berpotensi memberikan dampak nyata terhadap permasalahan pengangguran, khususnya di segmen usia muda:

Program Ketenagakerjaan yang Sangat Terfokus pada Usia 20-24 Tahun: Mengingat kelompok usia ini memiliki tingkat pengangguran tertinggi, pemerintah dan lembaga terkait perlu merancang dan mengimplementasikan program ketenagakerjaan yang secara spesifik menargetkan kebutuhan mereka. Ini bisa meliputi:

Pelatihan Vokasi dan Keterampilan yang Relevan: Menyediakan pelatihan intensif sesuai dengan permintaan pasar kerja saat ini dan masa depan (misalnya, keterampilan digital, green jobs, kewirausahaan).

Program Magang dan Penempatan Kerja: Memfasilitasi transisi dari dunia pendidikan ke dunia kerja melalui program magang yang terstruktur dan bermitra dengan industri.
Layanan Konseling Karir yang Ditingkatkan: Memberikan bimbingan karir profesional untuk membantu kaum muda mengidentifikasi jalur karir yang sesuai dan strategi pencarian kerja yang efektif.

Insentif Bagi Perusahaan: Memberikan insentif (misalnya, pengurangan pajak) bagi perusahaan yang merekrut lulusan baru atau kaum muda tanpa pengalaman kerja yang relevan.

Penguatan Dukungan untuk Kelompok Usia 15-19 dan 25-29 Tahun: Meskipun tingkat penganggurannya sedikit di bawah usia 20-24, kelompok ini tetap memerlukan perhatian khusus.

Untuk 15-19 tahun: Fokus pada program yang mencegah putus sekolah dan mempersiapkan mereka untuk jalur pendidikan lanjutan atau pelatihan vokasi.

Untuk 25-29 tahun: Program yang mendukung pengembangan keterampilan lanjutan (upskilling dan reskilling) untuk meningkatkan daya saing di pasar kerja, serta dukungan bagi mereka yang ingin beralih karir atau memulai usaha.

Kolaborasi Kuat antara Institusi Pendidikan dan Industri: Mendorong kurikulum pendidikan yang lebih selaras dengan kebutuhan industri dan memfasilitasi lebih banyak interaksi (misalnya, job fair, kunjungan industri, proyek kolaboratif) antara mahasiswa/siswa dan calon pemberi kerja sejak dini.

Peningkatan Akses Informasi Pasar Kerja: Membangun platform atau pusat informasi yang mudah diakses oleh kaum muda mengenai lowongan kerja, tren pasar, dan sumber daya pelatihan.

Penelitian Lebih Lanjut: Melakukan penelitian kualitatif untuk menggali lebih dalam akar penyebab tingginya pengangguran di kalangan muda, seperti tantangan spesifik yang dihadapi lulusan baru, kesenjangan keterampilan, atau faktor geografis/sosial.

Dengan mengimplementasikan rekomendasi yang terfokus pada segmen kelompok umur yang paling terdampak, diharapkan upaya penanggulangan pengangguran dapat menjadi lebih efektif dan memberikan dampak positif yang signifikan terhadap angka pengangguran nasional, khususnya di kalangan generasi muda.

AI Support Explanation
Dalam proyek analisis data pengangguran per kelompok umur ini, Artificial Intelligence (AI) diimplementasikan melalui penggunaan algoritma K-Means Clustering.

Relevansi Penggunaan AI: K-Means Clustering digunakan secara relevan untuk mencapai tujuan proyek, yaitu mengelompokkan kelompok umur berdasarkan pola data pengangguran mereka dari tahun 2021 hingga 2024. Ini adalah tugas clustering, yang merupakan salah satu area utama dalam unsupervised learning (cabang dari AI/Machine Learning). Algoritma ini sangat cocok untuk mengidentifikasi pengelompokan alami dalam dataset berdasarkan kemiripan fitur numerik (dalam kasus ini, jumlah pengangguran di setiap tahun).

Cara Penggunaan AI (K-Means Clustering) dalam Notebook Anda:

Data Input: Algoritma K-Means menerima data numerik sebagai input. Dalam notebook Anda, data jumlah pengangguran untuk setiap kelompok umur dari tahun 2021, 2022, 2023, dan 2024 (X setelah seleksi kolom) digunakan sebagai fitur input.

Pra-pemrosesan (Standardisasi): Sebelum dimasukkan ke algoritma K-Means, data input di-standardisasi menggunakan StandardScaler. Ini adalah langkah pra-pemrosesan krusial dalam clustering berbasis jarak. StandardScaler mengubah data sehingga memiliki rata-rata 0 dan standar deviasi 1, memastikan bahwa setiap tahun data pengangguran berkontribusi secara proporsional pada perhitungan jarak dalam algoritma, terlepas dari skala absolut jumlah pengangguran.

Penentuan Jumlah Cluster (k): Meskipun K-Means memerlukan jumlah cluster (k) yang ditentukan sebelumnya, notebook Anda menggunakan metode Elbow (aN91UPCvM6Ll) sebagai teknik heuristik yang umum dalam AI/ML untuk membantu menginformasikan pilihan nilai k. Plot inertia vs k membantu visualisasi di mana penambahan cluster memberikan diminishing return.

Pelatihan Model (Fitting): Algoritma K-Means di-fit atau dilatih pada data yang telah di-standardisasi (X_scaled). Proses fitting ini melibatkan algoritma secara iteratif menugaskan setiap titik data ke cluster terdekat dan memperbarui pusat cluster hingga konvergensi tercapai.
Penugasan Cluster (Predicting): Setelah model dilatih, ia digunakan untuk memprediksi label cluster (cluster_labels) untuk setiap titik data (kelompok umur). Setiap kelompok umur ditugaskan ke salah satu dari k cluster yang ditemukan.
Output dan Interpretasi: Label cluster yang dihasilkan ditambahkan kembali ke DataFrame asli. Hasil clustering ini kemudian dianalisis (misalnya, menghitung rata-rata fitur per cluster di cell Mu3m8CZ8OQdk) dan divisualisasikan (di cell 06Al43mjNT75 dan Mu3m8CZ8OQdk) untuk menginterpretasikan karakteristik setiap cluster dan mendapatkan insight mengenai perbedaan pola pengangguran antar kelompok umur.
Dengan demikian, K-Means Clustering di sini berfungsi sebagai alat AI untuk secara otomatis mengidentifikasi struktur atau pengelompokan tersembunyi dalam data pengangguran, yang sulit dilakukan hanya dengan melihat data mentah atau statistik deskriptif sederhana. Ini membantu dalam mengkategorikan kelompok umur ke dalam segmen-segmen yang memiliki pola pengangguran serupa, yang menjadi dasar untuk analisis dan rekomendasi lebih lanjut.
