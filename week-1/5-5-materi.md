# Hari 5 – Statistika Deskriptif Untuk Data Science
Statistika deskriptif berkaitan dengan bagaimana kita menjelaskan dan murumuskan suatu data. Umumnya digunakan dua metode pendekatan:

Pendekatan kuantitatif menjelaskan data secara numerik.
Pendekatan visual mengilustrasikan data menggunakan chart, plot, histogram, atau grafik lainnya.
Kita dapat menerapkan statistika deskriptif ke dalam satu atau banyak data. Ketika kita menjelaskan dan merumuskan suatu data tunggal, maka kita sedang melakukan analisa univariate. Ketika kita mencari hubungan statistika antara sepasang data, maka kita sedang melakukan analisa bivariate. Begitu juga dengan analisa multivariate yang berarti kita menerapkannya pada banyak data sekaligus.

Populasi dan Sampel
Dalam statistika, populasi merupakan sekumpulan elemen atau sesuatu yang ingin di amati, namun cakupan populasi biasa sangat besar sehingga akan sangat sulit untuk megumpulkan dan menganalisa datanya. Itulah mengapa ahli statistik biasanya mencoba mengambil kesimpulan mengenai suatu populasi dengan menguji dan memilih perwakilan dari populasi tersebut. Perwakilan dari populasi ini yang biasa kita sebut sampel. Secara ideal, sampel harus memiliki komponen penting statistik dari suatu populasi agar dapat mengggambarkan populasi secara nyata.

Outliers (pencilan)
Outlier merupakan sebuah data point yang jauh berbeda dengan mayoritas data pada suatu sampel atau populasi. Beberapa penyebab adanya outlier dalam data kita diantaranya:

Variasi alami dalam suatu data
Change atau perubahan perilaku pada sistem yang kita observasi
Error atau kesalahan saat pengumpulan data
Kesalahan saat pengumpulan data biasanya menjadi penyebab yang paling umum adanya outlier.

Jenis-jenis ukuran data
Central tendency (ukuran pemusatan data), biasanya kita lebih mengenal central tendency dengan Mean, Median, dan Modus. Salah satu hasil yang didapat dari pengukuran 3M ini adalah Skewness, yang nantinya kita bias tahu dimana data terkonsentrasi dan dimana letak outlier(pencilan) pada data tersebut. Negative skewed memiliki arti bahwa data terkonsentrasi di atas rata-rata dan outliernya berada pada data di bawah rata-rata, dapat dilihat bahwa pada kondis ini nilai mean lebih kecil dari median. Positif skew memiliki arti yang berkebalikan dengan negatif skew. Sedangkan jika nilai 3M-nya sama, maka data tersebut memiliki normal skew yang akan membentuk distribusi simetris.

https://miro.medium.com/max/575/1*0LNbEZu8vOe2hT5dxbpPUg.jpeg
Variability (ukuran sebaran data), cara yang paling umum untuk mengetahui ukuran sebaran data adalah dengan mengukur nilai range, interquartile range(IQR), variansi, kovariansi, dan standar deviasi dari data tersebut. Variansi adalah nilai ‘average’ dari kuadrat antara simpangan(deviasi) dengan rata-rata populasi. Bingung? Sama hehe. Mari kita lihat rumusan untuk menghitung variansi populasi berikut.

Missalkan X adalah variabel random dengan distribusi peluang f(x) dan rata-rata μ. Maka variansi dari X adalah:


Interpretasi dari rumusan di atas adalah nilai σ2 akan lebih kecil untuk kelompok nilai x yang dekat dengan μ dibandingkan dengan kelompok nilai x yang jauh dari μ. Dengan kata lain, jika nilai-nilai x cenderung terkonsentrasi di dekat rataannya, maka variansinya kecil, sedangkan jika jauh dari rataannya maka variansinya besar. Dapat dilihat pada gambar berikut:


Pada kenyataannya, kita jarang sekali dapat mengukur seluruh populasi, yang bisa kita ukur hanya sampel, misalnya kita bisa saja mengukur tinggi badan peserta training data science, tapi kita tidak dapat mengukur tinggi badan seluruh manusia di bumi, hal ini akan mengakibatkan bias terhadap pengukuran yang dilakukan, oleh karena itu, agar tidak bias dalam mengukur nilai varian, maka N sebagai pembagi penjumlahan kuadrat (sum of squares) diganti dengan N-1 (degree of freedom). Rumusan varian sampel menjadi:


Akar kuadrat dari variansi ini merupakan nilai dari standar deviasi (simpangan baku). Jika kita memili dua variabel random X dan Y, nilai kovariansi menunjukkan hubungan antara kedua variabel tersebut.


Jika kedua variabel tersebut bergerak ke arah yang sama (X membesar dan Y membesar) maka hasil kali (X – μX)(Y – μY) cenderung bernilai positif, sebaliknya jika kedua variabel bergerak ke arah berlawanan (X membesar dan Y mengecil), maka hasil kali (X – μX)(Y – μY)akan cenderung bernilai negatif. Tanda kovariansi (+ atau -) menunjukkan apakah hubungan antara kedua variabel positif atau negatif. Jika kovariansi bernilai positif maka ada hubungan antara dua variabel tersebut dan berbanding lurus, jika kovariansi bernilai negatif hubungannya berbanding terbalik, sedangkan jika bernilai nol maka tidak ada hubungan antara dua variabel tersebut.

Correlation coefficient atau hubungan variability menyatakan seberapa kuat hubungan antara dua variabel, koefisien korelasi dapat dihitung menggunakan persamaan:


Nilai koefisien korelasi berkisar antara (-1) hingga (+1) bergantung pada nilai kovariansinya. Jika nilai koefisien korelasi mendekati -1 atau mendekati +1 maka X dan y memiliki korelasi linier yang tinggi, jika nilai koefisien korelasinya -1 atau +1 kedua variabel tersebut memiliki korelasi sempurna, sedangkan jika nilai koefisien korelasinya nol maka X dan y tidak memiliki hubungan.

Library statistika pada python yang biasa digunakan yaitu:

statistics, merupakan built-in library pada python untuk statistika deskriptif. Kita dapat menggunakannya jika dataset yang kita miliki tidak terlalu besar, atau ketika kita tidak dapat meng-import library yang lain.
NumPy merupakan library pihak ketiga yang digunakan untuk perhitungan numerik, sangat baik untuk digunakan pada array tunggal atau multidimensi.
SciPy merupakan library pihak ketiga yang digunakan untuk perhitungan scientific. Dibuat dengan dasar library NumPy namun memiliki fungsi tambahan termasuk di dalamnya scipy.stats untuk analisa statistik.
Pandas merupakan library pihak ketiga untuk perhitungan numerik, pandas juga dibuat dengan dasar library NumPy. Sangat berguna untuk mengolah data 1D menggunakan objek Series, dan data 2D menggunakan objek DataFrame.
Menghitung statistika deskriptif menggunakan python
Kita hanya akan menggunakan library statistics, NumPy, dan SciPy untuk menghitung nilai-nilai yang dihasilkan dari statistika deskriptif, library Pandas akan dipelajari pekan depan. Kita mulai dengan meng-import librarynya:

>>> import math
>>> import statistics
>>> import numpy as np
>>> import scipy.stats
Kita buat suatu data berupa python list yang berisi data numerik secara random:

>>> x = [8.0, 1, 2.5, 4, 28.0]
>>> x_dgn_nan = [8.0, 1, 2.5, math.nan, 4, 28.0]
>>> x
[8.0, 1, 2.5, 4, 28.0]
>>> x_dgn_nan
[8.0, 1, 2.5, nan, 4, 28.0]
Sekarang kita punya dua list, x dan x_dgn_nan, keduanya hampir sama, bedanya yaitu x_dgn_nan memiliki nilai nan (not a number). Sangat penting bagaimana python menghadapi nilai nan ini. Dalam data science, missing value sangat sering terjadi, dan biasanya nilai yang hilang ini diganti dengan nan. Sekarang kita coba buat np.ndarray objek dari variabel x dan x_dgn_nan:

>>> y, y_dgn_nan = np.array(x), np.array(x_dgn_nan)
>>> y
array([ 8. ,  1. ,  2.5, 4. , 28. ])
>>> y_dgn_nan
array([ 8. ,  1. ,  2.5,  nan,  4. , 28. ])
Menghitung Ukuran Pemusatan Data
Kita akan nenpelajari bagaimana menghitung ukuran pemusatan data ini menggunakna python.

Mean (rataan) Kita dapat menghitung mean hanya dengan python tanpa meng-import library apapun menggunakan sum() dan len():

>>> mean_ = sum(x) / len(x)
>>> mean_
8.7
Kita juga bisa menggunakan fungsi bawaan dari library statistics python:

>>> mean_ = statistics.mean(x)
>>> mean_
8.7
>>> mean_ = statistics.fmean(x)
>>> mean_
8.7
Fungsi fmean() mulai dikenalkan pada python 3.8 sebagai alternatif untuk perhitungan yang lebih cepat dan selalu menghasilkan nilai float. Namun, fungsi mean() dan fmean() akan menghasilkan nilai nan jika di dalam variabel yang dihitungnya berisi nilai nan:

>>> mean_ = statistics.mean(x_dgn_nan)
>>> mean_
nan
>>> mean_ = statistics.fmean(x_dgn_nan)
>>> mean_ nan 
Jika kita ingin mengabaikan nilai nan yang ada pada variabel tersebut maka dapat menggunakan np.nanmean():

>>> np.nanmean(y_dgn_nan)
8.7
Weighted Mean atau rataan berbobot merupakan generalisasi dari rataan aritmatika sehingga kita dapat menentukan kontribusi relatif (bobot) dari setiap data point untuk penghitungan hasilnya. Kita dapat menghitung weighted mean menggunakan python dengan menggabungkan antara sum() dengan range() atau zip() seperti pada contoh berikut:

>>> x = [8.0, 1, 2.5, 4, 28.0]
>>> w = [0.1, 0.2, 0.3, 0.25, 0.15]
>>> wmean = sum(w[i] * x[i] for i in range(len(x))) / sum(w)
>>> wmean
6.95
>>> wmean = sum(x_ * w_ for (x_, w_) in zip(x, w)) / sum(w)
>>> wmean
6.95
Tetapi jika kita memiliki dataset yang cukup besar maka NumPy memberikan soolusi yang lebih baik untuk penghitungan weighted mean ini menggunakan np.average():

>>> y, w = np.array(x), np.array(w)
>>> wmean = np.average(y, weights=w)
>>> wmean
6.95
Hati-hati ketika melakukan perhitungan untuk data berisi nilai nan.

>>> w = np.array([0.1, 0.2, 0.3, 0.0, 0.2, 0.1])
>>> np.average(y_dgn_nan, weights=w)
nan
Harmonic Mean atau rataan harmonis dapat dirumuskan dengan 𝑛/Σᵢ(1/𝑥ᵢ) dimana i=1, 2, …, n dan n adalah jumlah data point pada dataset x. Kita bisa menghitungnya menggunakan python:

>>> hmean = len(x) / sum(1 / item for item in x)
>>> hmean
2.7613412228796843
Kita juga bisa menggunakan statistics.harmonic_mean():

>>> hmean = statistics.harmonic_mean(x)
>>> hmean
2.7613412228796843
Jika terdapat nilai nan, maka statistics.harmonic_mean() akan menghasilkan nilai nan, dan jika terdapat nilai negatif, maka akan terjadi error dalam perhitungannya:

>>> statistics.harmonic_mean(x_dgn_nan)
nan
>>> statistics.harmonic_mean([1, 0, 2])
0
>>> statistics.harmonic_mean([1, 2, -2])  #StatisticsError
Cara ketiga adalah dengan menggunakan scipy.stats.hmean():

>>> scipy.stats.hmean(y)
2.7613412228796843
Geometric Mean atau rataan geometris merupakan akar pangkat-n dari seluruh hasil perkalian elemen 𝑥ᵢ sejumlah n pada dataset x, dapat dirumuskan dengan ⁿ√(Πᵢ𝑥ᵢ), dimana dimana i=1, 2, …, n dan n adalah jumlah data point pada dataset x. Kita dapat menggunakan python untuk menghitung nilai rataan geometris ini sebagai berikut:

>>> gmean = 1
>>> for item in x:
...     gmean *= item
...
>>> gmean **= 1 / len(x)
>>> gmean
4.677885674856041
Pada python 3.8 kita dapat menggunakan statistics.geometric_mean(), yang akan mengubah semua nilai pada dataset menjadi float kemudian menghitung rataan geometrisnya:

>>> gmean = statistics.geometric_mean(x)
>>> gmean
4.67788567485604
Dengan menggunakan scipy.stats.gmean():

>>> scipy.stats.gmean(y)
4.67788567485604
Jika terdapat nilai nan pada dataset maka gmean() akan menghasilkan nan. Jika terdapat satu saja nilai 0, maka akan menghasilkan rataan geometris 0 disertai peringatan.

Median suatu sampel merupakan nilai tengah dari dataset yang telah diurutkan. Dataset tersebut dapat diurutkan secara naik atau turun. Jika jumlah elemen n dari dataset adalah ganjil maka median adalah elemen pada posisi 0.5(n+1). Jika n genap, maka mediannya adalah rataan aritmatika dari dua nilai tengah, yaitu yang berada pada posisi 0.5n dan 0.5n+1. Perbedaan utama antara sifat mean dan median dari suatu dataset adalah hubungannya dengan outlier pada dataset tersebut. Nilai mean sangat dipengaruhi oleh outlier sedangkan nilai median hampir tidak dipengaruhi atau bahkan tidak dipengaruhi sama sekali. Perhatikan gambar berikut:


Dataset bagian atas memiliki nilai 1, 2.5, 4, 8, dan 28. Nilai mean dari dataset tersebut adalah 8.7 dan nilai mediannya adalah 4. Dataset bagian bawah menunjukkan bagaimana perubahan nilai mean ketika nilai paling kanan pada dataset atas yang memiliki nilai 28 di pindahkan.

Berikut adalah salah satu cara mencari nilai median menggunakan python:

>>> n = len(x)
>>> if n % 2:
...     median_ = sorted(x)[round(0.5*(n-1))]
... else:
...     x_ord, index = sorted(x), round(0.5 * n)
...     median_ = 0.5 * (x_ord[index-1] + x_ord[index])
...
>>> median_
4
Langkah penting pada proses di atas adalah:

Mengurutkan elemen-elemen pada dataset
Mencari elemen tengah pada dataset yang telah diurutkan
Kita juga bisa mendapatkan nilai median dengan statistics.median():

>>> median_ = statistics.median(x)
>>> median_
4
Cara yang lain untuk mendapatkan nilai median adalah menggunakan np.median():

>>> median_ = np.median(y)
>>> median_
4.0
Mode atau modus dari suatu sampel dataset adalah nilai yang paling banyak muncul dalam dataset tersebut. Dengan python kita dapat menghasilkan nilai modus suatu dataset sebagai berikut:

>>> u = [2, 3, 2, 8, 12]
>>> mode_ = max((u.count(item), item) for item in set(u))[1]
>>> mode_
2
Kita dapat mencari modus dari suatu daset menggunakan statistics.mode(), dan juga menggunakan statistics.multimode() (mulai dikenalkan pada python 3.8) jika nilai modusnya tidak hanya satu:

>>> mode_ = statistics.mode(u)
>>> mode_
2
>>> mode_ = statistics.multimode(u)
>>> mode_
[2]
Dapat dilihat bahwa mode() menghasilkan nilai tunggal, sedangkan multimode() menghasilkan list yang berisi nilai modus. Bahkan mode() akan menghasilkan error jika dalam dataset tersebut terdapat dua modus:

>>> v = [12, 15, 12, 15, 21, 15, 12]
>>> statistics.mode(v)  # StatisticsError
>>> statistics.multimode(v)
[12, 15]
Bagaimana jika dalam dataset terdapat nilai nan? Bisa dicoba sendiri hehe..

Untuk menghasilkan nilai modus jika menggunakan scipy.stats.mode():

>>> u, v = np.array(u), np.array(v)
>>> mode_ = scipy.stats.mode(u)
>>> mode_
ModeResult(mode=array([2]), count=array([2]))
>>> mode_ = scipy.stats.mode(v)
>>> mode_
ModeResult(mode=array([12]), count=array([3]))
Jika terdapat lebih dari satu nilai modus, scipy.stats.mode() akan menjadikan nilai terkecil sebagai modus.

Menghitung Ukuran Sebaran Data
Ukuran pemusatan saja tidak cukup untuk menjelaskan suatu data, kita juga perlu menghitung ukuran sebaran data. Beberapa ukuran sebaran data yang perlu diketahui yaitu:

Variance atau variansi. Menghitung variansi menggunakan python dapat dilakukan dengan cara berikut:

>>> n = len(x)
>>> mean_ = sum(x) / n
>>> var_ = sum((item - mean_)**2 for item in x) / (n - 1)
>>> var_
123.19999999999999
Cara yang lebih singkat dan elegan adalah menggunakan statistics.variance():

>>> var_ = statistics.variance(x)
>>> var_
123.2
Bagaimana jika terdapat nilai nan dalam dataset? Silahkan dicoba sendiri hehe..

Cara yang lain yaitu menggunakan fungsi np.var() atau metode .var():

>>> var_ = np.var(y, ddof=1)
>>> var_
123.19999999999999
>>> var_ = y.var(ddof=1)
>>> var_
123.19999999999999
Penting untuk mendefinisikan nilai ddof=1. Parameter ini digunakan agar perhitungan nilai s2 sesuai yaitu menggunakan n-1 sebagai pembagi bukan n saja. Untuk dataset yang memiliki nilai nan, kita dapat mengabaikan nilai nan tersebut dengan np.nanvar():

>>> np.nanvar(y_dgn_nan, ddof=1)
123.19999999999999
Standar Deviasi atau simpangan baku. Menghitung standar deviasi menggunakan python dapat dilakukan dengan cara:

>>> std_ = var_ ** 0.5
>>> std_
11.099549540409285
Kita juga bisa menggunakan statistics.dev():

>>> std_ = statistics.stdev(x)
>>> std_
11.099549540409287
Jika kita menggunakan Numpy, perhatikan untuk menggunakan fungsi yang sesuai jika terdapat nilai nan:

>>> np.std(y, ddof=1)
11.099549540409285
>>> y.std(ddof=1)
11.099549540409285
>>> np.std(y_dgn_nan, ddof=1)
nan
>>> y_dgn_nan.std(ddof=1)
nan
>>> np.nanstd(y_dgn_nan, ddof=1)
11.099549540409285
Skewness, nilai dari skewness dapat dihasilkan menggunakan python dengan cara:

>>> x = [8.0, 1, 2.5, 4, 28.0]
>>> n = len(x)
>>> mean_ = sum(x) / n
>>> var_ = sum((item - mean_)**2 for item in x) / (n - 1)
>>> std_ = var_ ** 0.5
>>> skew_ = (sum((item - mean_)**3 for item in x)
...          * n / ((n - 1) * (n - 2) * std_**3))
>>> skew_
1.9470432273905929
Kita juga bisa menggunakan scipy.stats.skew():

>>> y, y_dgn_nan = np.array(x), np.array(x_dgn_nan)
>>> scipy.stats.skew(y, bias=False)
1.9470432273905927
>>> scipy.stats.skew(y_dgn_nan, bias=False)
nan
suatu dataset dapat dianggap simetris jika memiliki nilai skewness mendekati 0, yaitu antara -0.5 dan 0.5.

Percentiles ke-p dari sekumpulan data adalah nilai dimana p% dari data tersebut berada dibawahnya. Setiap data memiliki tiga nilai kuartil, yang membagi data menjadi 4 bagian sama besar.

Kuartil pertama (Q1) adalah persentil ke-25 dari data
Kuartil kedua (Q2) adalah persentil ke-50 dari data yang juga merupakan median dari data tersebut.
Kuartil ketiga (Q3) adalah persentil ke-75 dari data
Nilai persentil dapat dicari menggunakan np.percentile():

>>> x = [-5.0, -1.1, 0.1, 2.0, 8.0, 12.8, 21.0, 25.8, 41.0]
>>> y = np.array(x)
>>> np.percentile(y, 5)
-3.44
>>> np.percentile(y, 95)
34.919999999999995
Jika kita ingin mengabaikan nilai nan pada data maka digunakan np.nanpercentile():

>>> y_dgn_nan = np.insert(y, 2, np.nan)
>>> y_dgn_nan
array([-5. , -1.1,  nan,  0.1,  2. ,  8. , 12.8, 21. , 25.8, 41. ])
>>> np.nanpercentile(y_dgn_nan, [25, 50, 75])
array([ 0.1,  8. , 21. ])
Ranges dari data adalah selisih antara elemen maksimum dan elemen minimum pada suatu dataset. Kita dapat menghitungnya dengan fungsi np.ptp():

>>> np.ptp(y)
46.0
>>> np.ptp(y_dgn_nan)
nan
Alternatifnya, kita bisa menggunakan fungsi bawaan python dan NumPy:

>>> np.amax(y) - np.amin(y)
46.0
>>> np.nanmax(y_dgn_nan) - np.nanmin(y_dgn_nan)
46.0
>>> y.max() - y.min()
46.0
Menghitung Korelasi Antara Sepasang Data
Korelasi atau hubungan antara sepasang data dapat dilihat dengan menghitung:

Covariance, dengan menggunakan fungsi dari python kovariansi dapat dihitung sebagai berikut:

>>> n = len(x)
>>> mean_x, mean_y = sum(x) / n, sum(y) / n
>>> cov_xy = (sum((x[k] - mean_x) * (y[k] - mean_y) for k in range(n))
...           / (n - 1))
>>> cov_xy
19.95
Dengan menggunakan np.cov() dari NumPy kita akan mendapatkan matriks kovariansi:

>>> cov_matrix = np.cov(x_, y_)
>>> cov_matrix
array([[38.5       , 19.95      ],
       [19.95      , 13.91428571]])
Dimana nilai 38.5 atau posisi atas kiri merupakan nilai variansi dari x, dan nilai 13.91 merupakan nilai variansi dari y, dan dua nilai lainnya merupakan nilai kovariansi antara x dan y, yaitu 19.95.

Correlation coefficient, untuk menghitung koefisien korelasi hanya menggunakan fungsi bawaan python adalah sebagai berikut:

>>> var_x = sum((item - mean_x)**2 for item in x) / (n - 1)
>>> var_y = sum((item - mean_y)**2 for item in y) / (n - 1)
>>> std_x, std_y = var_x ** 0.5, var_y ** 0.5
>>> r = cov_xy / (std_x * std_y)
>>> r
0.861950005631606
Library scipy.stats memiliki fungsi pearsonr() yang menghitung nilai dari koefisien korelasi dan juga nilai p-value nya:

>>> r, p = scipy.stats.pearsonr(x_, y_)
>>> r
0.861950005631606
>>> p
5.122760847201171e-07
Jika ingin menggunakan NumPy, dapat memakai fungsi np.corrcoef() dengan argumen x_ dan y_, maka didapatkan matriks koefisien korelasinya:

>>> corr_matrix = np.corrcoef(x_, y_)
>>> corr_matrix
array([[1.        , 0.86195001],
       [0.86195001, 1.        ]])
Nilai 1 pada matriks tersebut menunjukkan koefisien korelasi antara satu argumen dengan dirinya sendiri, sedangkan dua nilai yang lain menunjukkan koefisien korelasi antara kedua argumen yakni x_ dan y_.

>>> r = corr_matrix[0, 1]
>>> r
0.8619500056316061
>>> r = corr_matrix[1, 0]
>>> r
0.861950005631606
Kita juga bisa menggukanan fungsi scipy.stats.linregress() yang akan menghasilkan beberapa nilai, salah satunya adalah koefisien korelasinya:

>>> scipy.stats.linregress(x_, y_)
LinregressResult(slope=0.5181818181818181, intercept=5.714285714285714, rvalue=0.861950005631606, pvalue=5.122760847201164e-07, stderr=0.06992387660074979)
>>> result = scipy.stats.linregress(x_, y_)
>>> r = result.rvalue
>>> r
0.861950005631606

List Video :
Data Science Statistik : Apa itu Deskriptif Statistik 
  https://youtu.be/d4VW7uT0P74

Central Tendency, Dispersi, Visualisasi Displot dan Boxplot
  https://youtu.be/vnUKA86AxuM

4.Data Science Statistik : Dispersi, Variansi dan Standard Deviasi : https://youtu.be/v7QK6DJaTT4 

5.Data Science Statistik : Mean Standard Deviasi vs Median Interquartile : https://youtu.be/VY4nENvuXyM

Sumber:
https://realpython.com/python-statistics/
https://www.academia.edu/25566517/Variansi_and_Kovariansi

Rekomendasi Bacaan:
https://tau-data.id/tipe-data-dm-ds/
https://tau-data.id/model-statistika-data-mining-data-science/



https://blog.sanbercode.com/docs/kurikulum-python-data-science/week-1/hari-5-statistika-deskriptif/

