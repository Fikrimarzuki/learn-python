Pandas Introduction
Instalasi Pandas
Kali ini, kamu akan mempelajari semua tentang pandas, pandas adalah suatu liblary di Python yang paling populer untuk analisis data.

Pandas adalah suatu liblary yang open source, menyediakan performance yang sangat baik, struktur data yang mudah digunakan dan alat analisis data untuk Python. Pandas akan menjadi langkah besar kamu dalam perjalanan mempelajari data science.

Untuk menggunakan pandas, kamu terlebih dahulu mesti menginstall nya di command prompt dengan mengetikan pip install pandas.


Installasi Pandas
Tunggu sampai installasi selesai, ketika kamu hendak menginstall pandas, tidak hanya pandas yang akan di install, tapi juga beserta dependency nya, di gambar, ketika menginstall pandas kamu juga menginstall pytz dan numpy.

Pada artikel ini, akan dijelaskan beberapa materi fondasi untuk memahami pandas. diantaranya adalah :

Objek Pandas : DataFrame vs Series
Membaca data dari File
Pemeriksaan sederhana tentang Karakteristik Data
Objek Panas : DataFrame vs Series
Dataframe dan series ini adalah suatu objek tempat kita menyimpan data secara terstruktur. perbedaan dari DataFrame dan Series ini terletak pada struktur nya dan juga attribute dan method-method yang mereka miliki, untuk perbedaan strukturnya adalah sebagai berikut :

DataFrame adalah suatu objek 2 dimensi, mirip seperti tabel
Series adalah objek 1 dimensi
Series
Series adalah suatu objek satu dimensi yang dapat menyimpan berbagai jenis tipe data seperti integer, string, dan lain sebagainya. tipe data dari objek series ini harus seragam. berikut contoh membuat list :

import pandas as pd

x = pd.Series([6,3,4,6])
print(x)
=============
0    6
1    3
2    4
3    6
dtype: int64
Series memiliki satu sumbu saja, dari contoh di atas sumbu tersebut berada baris baris, yaitu 0, 1, 2, 3. kita bisa mengubah sumbu tersebut dengan sebagai berikut :

# cara pertama
x.index = ['a', 'b', 'c', 'd']
print(x)
===========
a    6
b    3
c    4
d    6
dtype: int64


# cara kedua
x = pd.Series([6,3,4,6], index=['a', 'b', 'c', 'd'])
print(x)
===========
a    6
b    3
c    4
d    6
dtype: int64

# check tipe data
print(type(x))
================
pandas.core.series.Series
Perhatikan : jumlah index harus sama dengan jumlah data.

DataFrame
DataFrame adalah suatu objek 2 dimensi tempat menyimpan data dengan lebih terstruktur. dataframe memiliki 2 index, yaitu index baris dan index columns. Dalam satu column dataframe harus memiliki tipe data yang sama. tapi antar columnnya dataframe bisa memiliki jenis data yang berbeda. untuk lebih jelasnya perhatikan contoh berikut :

import pandas as pd

df = pd.DataFrame({'tipe_int': [50, 21], 'tipe_string': ['a', 'b']})
print(df)
==========
tipe_int    tipe_string
0 	50 	a
1 	21 	b

# check tipe data
print(type(df))
==========
<class 'pandas.core.frame.DataFrame'>
Membaca data dari File 
Membaca data dari file adalah hal pertama yang dilakukan dalam suatu pekerjaan data science. maka hal ini sangat penting.

Ada beberapa tipe file yang biasa di gunakan untuk menyimpan data, seperti database, excel, csv. disini akan di jelaskan beberapa saja tentang cara membaca file dari berbagai sumber tersebut. akan di jelaskan 2 yaitu csv dan excel karena csv dan excel adalah sumber yang biasa di gunakan untuk menyimpan data karena kemudahannya. ok kita langsung saja.

Pandas menyediakan metode yang berbeda untuk membaca file dengan tipe berbeda. untuk membaca file bertipe csv pandas menggunakan suatu metode read_csv(), untuk membaca file bertipe excel pandas menggunkan suatu metode bernama read_excel. perhatikan contoh berikut :

# membaca dari dari csv
df_from_csv = pd.read_csv('jabar-corona-virus-case.csv')

# membaca data dari excel
df_from_excel = pd.read_excel('jabar-corona-virus-case.xlsx')
Untuk menggunakan method tersebut kita hanya perlu memasukan argument wajib, yaitu path dari file yang akan kita baca. lebih lanjutnya lagi pandas memiliki beberapa argumen optional, kalian bisa mecarinya dengan menggunakan metode help yang telah kalian pelajari sebelumnya

Pemeriksaan sederhana tentang Karakteristik Data 
Pandas memiliki beberapa method untuk memahami gambaran besar karakteristik dari data kita. diantaranya adalah :

head()
tail()
info()
describe()
Metode head() adalah secara default adalah untuk melihat 5 pertama data kita, sedangkan metode tail() secara default untuk melihat 5 data kita dari terakhir. kita bisa mengganti jumlah data yang akan di tampilkan dengan memberikan data integer sebagai argument terhadap metode tersebut. contohnya sebagai beriktu :


menampilkan tujuh data pertama

Menampilkan 5 data dari terakhir
info() adalah suatu method untuk melakukan summary terhadap data yang memberikan informasi tentang tipe dari index data, tipe dari column data, non-null values pada setiap column dan jumlah memory yang digunakan. berikut adalah contohnya :


descirbe() adalah sutau metode yang menghasilkan kesimpulan deskriptif statistik dari data. kesimpulan deskriptif statistik yang dihasilkan adalah seperti central tendency, dispersi dan bentuk distributsi dari data. untuk mengetahui lebih dalam tentang deskriptik statistik silahkan baca artikel ini. berikut contoh penggunaan metode ini.


Hasil Deskripsi Statistik

Video Pembelajaran

Belajar NUmpy: Numpy vs List : https://youtu.be/rZh9bFAG2Co

0. [Pandas] : Pengenalan Singkat Pandas : https://youtu.be/EBHkqzDUxCw

1. [Pandas] : Pandas Series dan List : https://youtu.be/mkqdYtUqLos

2. [Pandas] : Series dan Dictionary : https://youtu.be/Tsjfq1QG6bQ

3. [Pandas] : Pandas DataFrame : Struktur dan Membuat DataFrame : https://youtu.be/Af10_l79vLg

Pandas Apa itu Series Membuat Series dari List : https://youtu.be/3sU4Fn9w_ag

Pandas Apa Itu Series Perbedaan List dan Series : https://youtu.be/j-o7vsiWafg

Pandas Apa Itu Series Perbedaan Dictionary dan Series : https://youtu.be/fg4HNG17qgI

Belajar Pandas : Membaca dan Membuat Data : https://youtu.be/vKnx8sr9xHo


External Resources
List Video:

Menggunakan Numpy Array - [Tutorial Python Data Science bahasa Indonesia untuk pemula] #INDOSOAI : https://youtu.be/06cjWxfk-Zc

Manipulasi Data Pandas [Tutorial Python Data Science bahasa Indonesia untuk pemula] #INDOSOAI : https://youtu.be/3krwFrozpek

LOADING DATA di COLAB [Tutorial Python Data Science bahasa Indonesia untuk pemula] #INDOSOAI : https://youtu.be/qghFcRSdCSk


List Artikel :

https://www.yuksinau.id/statistika-deskriptif/ (deskriptif statistik)
https://petruknisme.com/2019/04/15/pengenalan-pandas-dan-series/
https://code.tutsplus.com/id/tutorials/introducing-pandas–cms-26514



https://blog.sanbercode.com/docs/kurikulum-python-data-science/week-2/pandas-foundation/

