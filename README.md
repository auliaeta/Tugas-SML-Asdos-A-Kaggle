# Tugas-SML-Asdos-A-Kaggle
Tugas ini merupakan tugas praktikum matakuliah statistik machine learning dari kelompok dengan NRP 009, 019, dan 139

## Penjelasan Dataset :
Dataset yang digunakan berisi data karyawan perusahaan yang mencerminkan berbagai aspek personal, pekerjaan, dan kepuasan kerja untuk memprediksi apakah seorang karyawan akan keluar dari perusahaan (attrition) atau tidak. Setiap baris mewakili satu individu dengan informasi seperti usia, tingkat pendidikan, jabatan, pendapatan, pengalaman kerja, hingga kepuasan terhadap lingkungan dan hubungan kerja. Selain itu, terdapat pula variabel kategorikal seperti jenis kelamin, status pernikahan, frekuensi perjalanan dinas, serta kebiasaan lembur yang mencerminkan gaya kerja dan keseimbangan hidup. Melalui kombinasi data demografis, profesional, dan psikologis ini, analisis dilakukan untuk memahami faktor-faktor yang berpengaruh terhadap keputusan karyawan dalam bertahan atau meninggalkan perusahaan

## Bussines Understanding
tujuan utama dari analisis ini adalah untuk memahami faktor-faktor yang memengaruhi tingkat attrition atau keluarnya karyawan dari perusahaan. Dalam dunia kerja modern, tingginya tingkat pergantian karyawan dapat menimbulkan kerugian besar bagi perusahaan, baik dari segi biaya rekrutmen, pelatihan, maupun penurunan produktivitas. Oleh karena itu, analisis ini berfokus pada bagaimana berbagai aspek seperti usia, kepuasan kerja, keseimbangan hidup, gaji, dan kebiasaan lembur berperan dalam keputusan seorang karyawan untuk bertahan atau meninggalkan pekerjaannya. Dengan memahami pola-pola tersebut melalui data, perusahaan dapat merancang strategi yang lebih tepat untuk meningkatkan retensi karyawan, memperbaiki lingkungan kerja, serta menciptakan sistem manajemen sumber daya manusia yang lebih efektif dan berkelanjutan

## Prepocessing
<img width="644" height="455" alt="image" src="https://github.com/user-attachments/assets/0ec03449-5c56-4a0e-aea4-f044756c4404" />
beberapa kolom yang tidak relevan seperti id, EmployeeCount, dan StandardHours dihapus karena tidak memberikan informasi berarti. Selanjutnya, data dipisahkan antara fitur (X) dan target (y), di mana Attrition menjadi variabel target. Kolom kategorikal diubah menjadi format numerik menggunakan one-hot encoding agar bisa diproses oleh algoritma machine learning. Kemudian, data numerik di-scaling menggunakan StandardScaler agar setiap fitur memiliki skala yang seragam. Selain itu, dilakukan deteksi dan pembatasan outlier untuk mencegah nilai ekstrem memengaruhi hasil model. Dengan tahapan ini, data menjadi lebih bersih, dan terstandarisasi

## Train Split data dan SMOTE Balencing 
<img width="405" height="94" alt="image" src="https://github.com/user-attachments/assets/49bb6d5e-6d99-44fa-a230-8102768454c1" />
<img width="186" height="70" alt="image" src="https://github.com/user-attachments/assets/b2587058-c1b7-405a-a557-f410de82615d" />
SMOTE Balancing digunakan untuk mengatasi masalah ketidakseimbangan kelas pada variabel target Attrition (misalnya, jumlah karyawan yang keluar jauh lebih sedikit daripada yang bertahan). Hasil output Setelah SMOTE: 0 = 788, 1 = 788 menunjukkan bahwa setelah proses ini, kedua kelas memiliki jumlah sampel yang sama, yaitu 788. Hal ini membantu model agar tidak bias terhadap kelas mayoritas dan dapat mengenali pola pada kelas minoritas dengan lebih baik

## Analisis Model
<img width="777" height="451" alt="image" src="https://github.com/user-attachments/assets/c22f749c-29ce-4449-b40e-9444278ae58c" />
Berdasarkan grafik dan hasil evaluasi di atas, terlihat bahwa Logistic Regression (L2 Ridge) memiliki nilai ROC-AUC tertinggi sebesar 0.8352, menandakan bahwa model ini paling baik dalam membedakan antara karyawan yang akan keluar
<img width="328" height="115" alt="image" src="https://github.com/user-attachments/assets/aa749f8b-01d7-4388-86c2-375b09b98c2b" />
Secara keseluruhan, Logistic Regression yang sederhana justru memberikan performa paling stabil dan optimal setelah dilakukan optimasi. Hal ini bisa jadi karena dataset memiliki jumlah fitur yang tidak terlalu besar dan hubungan antar-variabel yang cukup linear, sehingga model linier mampu menangkap pola dengan efektif tanpa overfitting.

##C Implementasi Pada data test
<img width="135" height="100" alt="image" src="https://github.com/user-attachments/assets/857c3b7d-2f47-4556-8600-c1526041cfbe" />
ini digunkan untuk melakukan tahap akhir prediksi dan membuat file submission pada dataset test. Proses ini diawali dengan membaca data uji dan melakukan preprocessingyang sama seperti pada data latih, seperti menghapus kolom yang tidak relevan, melakukan *encoding* variabel kategorikal, serta menambahkan fitur hasil *feature engineering* baru seperti *YearsAtCompany_JobSat*, *Age_Squared*, dan *RoleTenureRatio* agar konsisten dengan data train. Setelah itu,bets model yang telah diperoleh dari proses evaluasi sebelumnya  digunakan untuk memprediksi probabilitas karyawan akan keluar dari perusahaan. Nilai probabilitas tersebut kemudian dikonversi menjadi label biner (0 = bertahan, 1 = keluar). Akhirnya, hasil prediksi digabungkan dengan kolom id dan disimpan dalam format yang sesuai untuk diunggah sebagai hasil submission


