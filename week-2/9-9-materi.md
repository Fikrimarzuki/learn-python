Hari 2 – Akses/Indexing dan Transformasi Data
Indexing DataFrame
Akses DataFrame sering juga di kenal indexing atau Subset Selection. secara sederhana maknanya adalah kita memilih suatu data dari baris tertentu dan column tertentu. kita bisa saja memilih beberapa baris dan semua kolom dari data, semua baris dan beberapa column dari data, atau beberapa baris dan bebearpa column dari data.

Ada banyak cara-cara kita indexing suatu dataframe. diantranya adalah dengan menggunakan :

dataframe[] : cara seperti ini dikenal sebagai index operator.
dataframe.loc[]: operator yang menggunakan label untuk mengakses data, jika misalkan kamu melakukan dataframe.loc[‘jumlah’], berarti kamu hendak mengakses data yang mempunyai index jumlah
dataframe.iloc[: operator yang menggunakan posisi index untuk mengakses data. jikalau kamu melakukan dataframe.iloc[2] berarti kamu hendak mengakses dataframe dengan index posisi 2
Untuk lebih jelasnya kamu bisa melihat video pembelajaran tentang ‘Mengakses DataFrame dengan index’.

Filtering DataFrame with Boolean
Dapat dibilang kalau filtering dataframe dengan boolean is more human. karena kita mengakses suatu data berdasarkan logika dan dapat kita masukan ke dalam suatu statement, sebagai contoh, ‘Ambilkan data yang memiliki nilai luas lebih dari 50’. ketika mengubahnya kedalam suatu kode python ckup dengan menuliskan df>50. maka akan menghasillkan sua tu data Boolean Series berisi Ya (True) dan Tidak (False).

Filtering DataFrame dimulai dari pertanyaan
Pada tulisan ini saya akan memberikan beberapa contoh mengakses DataFrame dengan Filtering by Boolean. kita akan menggunakan suatu data tentang kejadian titanic. pertama kita import data kita.


Importing and Inspecting Data
Dari gambar dapat kita lihat bahwa data kita memiliki beberapa column seperti tentang status survived, tentang umur, tentang jenis kelamain, dan lain-lain. misalkan boss kita menyuruh kita untuk melakukan beberapa hal sebagai berikut :

1. Tunjukan kepada saya semua data orang-orang yang selamat!!
2. Tunjukan kepada saya semua data laki-laki yang selamat.
3. Tunjukan kepada saya semua data tentang perempuan yang tidak selamat di umur lebih dari 40 tahun atau kurang dari 20 tahun.

Hal pertama yang mesti kita lakukan untuk melakukan operasi yang bisa menjawab permintaan di atas adalah… kita membuat terlebih dahulu suatu Boolean Series. kemudian boolean series tersebut kita masukan kedalam dataframe kita. langsung saja akan saya perlihatkan dengan contoh. dimulai dari pertanyaan pertama.

1. Data orang-orang yang selamat
# boolean series orang orang yang selamat
survived = df.survived == 1
print(survived)
=================
0        True
1        True
2       False
3       False
4       False
        ...  
1304    False
1305    False
1306    False
1307    False
1308    False
Name: survived, Length: 1309, dtype: bool
Sekarang kita masukan boolean series kita ke dalam dataframe kita.


Hasil filtering data orang yang selamat
2. Data laki-laki yang selamat
Seperti biasa kita buat terlebih dahulu boolean series nya, kali ini kita membuat 2 boolean series. yaitu boolean series orang yang selamat dan bolean series orang yang berjenis kelamin laki-laki. berikut caranya

# bolean series orang yang selamat
survived = df.survived == 1
# boolean series laki-laki
laki2 = df.sex = 'male'

# tampilkan data boolean series laki2
print(laki2)
=============
0       False
1        True
2       False
3        True
4       False
        ...  
1304    False
1305    False
1306     True
1307     True
1308     True
Name: sex, Length: 1309, dtype: bool
Sekarang kita masukan 2 boolean series ini ke dalam dataframe kita, ada sedikit hal yang perlu kamu lakukan ketika ingin memfilter dataframe dengan lebih dari satu kondisi boolean series, pertama kamu harus memberikan kurung kepada setiap boolean series mu, kedua hubungkan kedua boolean series itu dengan logical operator seperti & (and), | (or), dan lain sebagainya. berikut caranya.

print(df[(survived) & (laki2)])

3. Data Perempuan yang tidak selamat dengan umur lebih dari 40 tahun atau kurang dari 20 tahun.
Coba perhatikan ada berapa boolean series yang perlu kita buat. disini ada 4 boolean series yang perlu kita buat, yaitu orang yang tidak selamat, orang yang berjnis kelamin perempuan, orang yang berumur lebih dari 40 tahun, dan orang yang kurang dari 20 tahun. jadi mari kita buat boolean series nya.

# orang yang tidak selamat
not_survived = df.survived == 0

# orang berjnis kelamin perempuan
perempuan = df.sex == 'female'

# orang yang berumur lebih dari 40 tahun
lebih_40 = df.age > 40

# orang yang berumur kurang dari 20 tahun
kurang_20 = df.age < 20
kemudian kita gabungkan boolean series ini dengan seperti ini :

df[(not_survived) & (perempuan) & (lebih_40 | kurang_20)]

Data Transformation
Data transformasi adalah mengubah format data kepada suatu format yang kita inginkan. didalam matematika dikenal dengan istilah mapping. dalam melakukan transformasi kita memerlukan terlebih dahulu suatu fungsi yang dapat memetkan bentuk data awal kita menjadi bentuk data akhir yang kita inginkan.

Identifying Functions from Mapping Diagrams
source : https://www.onlinemath4all.com/identifying-functions-from-mapping-diagrams.html
Identifying Functions from Mapping Diagrams
source : https://www.onlinemath4all.com/identifying-functions-from-mapping-diagrams.html
Pandas menyediakan berbagai method bawaan untuk melakukan transformasi terhadap data kita, beberapa diantaranya telah diperkenalkan pada hari pertama di minggu ke dua ini. misalnya describe(), method describe ini tidak lain memetakan data mentah kita menjadi suatu data hasil tentang deskriptif statistik.

Selain itu masih banyak lagi method2 bawaan yang di sediakan pandas untuk melakukan dat transformasi seperti method mean(), dan lain sebagaiinya.

Kita juga bisa melakukan transformasi sesuai keinginan kita sendiri atau custom transformation. untuk melakukan custom transformation terlebih dahulu perlu membuat fungsi untuk melakukan mapping antara data awal hingga menjadi data yang di harapkan. berikut akan di periihatkan satu contoh transformasi data

kita kembali akan menggunakan data tentang titanic. misalkan kita ingin mengubah data kita, dimana kita ingin mengubah column age, semua nilainya di kurangi dengan nilai minimum dari kolumn tersebut. maka pertama kita definiskan fungsi tersebut.

def minus_minimum(x):
    return x - x.min()
setelah kita mendefinisikan fungsinya. sekarang kita akan menggunakan method apply() dari pandas. method apply ini akan menerima suatu fungsi kemudian ‘meng-apply’ fungsi tersebut ke dalam setiap sumbu dari dataframe, secara default sumbu yang ‘apply’ adalah sumbu column. langsung saja kita perlihatkan. sebelum nykita lihat dulu data awal kita seperti apa.

print(df.age)
================
0       29.00
1        0.92
2        2.00
3       30.00
4       25.00
        ...  
1304    14.50
1305      NaN
1306    26.50
1307    27.00
1308    29.00
Name: age, Length: 1309, dtype: float64
Dan nilai minumum dari column age adalah :

(df.age.min())
==============-
0.17
maka seharusnya apabila kita melakukan transformasi terhadap column age dengan fungsi ‘minus_minimum’, maka seharusnya semua nilai dari column age akan di kurangi dengan nilai minimumnya. kita buktikan

print(df[['age']].apply(minus_minimum))

Kalian lihat, hasilnya seperti yang kita harapkan, yaitu semua data dari column age dikurangi nilai minmumnya.

Video Pembelajaran

4.[Pandas] : Pemilihan Data di Objek Pandas Series : https://youtu.be/_zIO4XXOtIU

5.[Pandas] :Pemilihan Data di Objek Pandas DataFrame : https://youtu.be/Ayib8wGENz8

Belajar Data Science Pandas Data Transformasi : https://youtu.be/rzyyDE65w48

6.[Pandas] : Memfilter Pandas DataFrame : https://youtu.be/445yw9Mq-gs

7.[Pandas] : Data Transformasi : https://youtu.be/ZUSH7ljpLvc


List artikel :

https://www.it-swarm.dev/id/python/memilih-beberapa-kolom-dalam-bingkai-data-panda/1068562049/
https://www.it-swarm.dev/id/python/pilih-baris-dari-dataframe-berdasarkan-nilai-nilai-dalam-kolom-di-panda/1073294319/
https://www.it-swarm.dev/id/python/jatuhkan-kolom-yang-namanya-berisi-string-spesifik-dari-panda-dataframe/1041678799/ (Pandas Filtering)



https://blog.sanbercode.com/docs/kurikulum-python-data-science/week-2/day-2-videos-1-mengakses-dataframe-dengan-index/

