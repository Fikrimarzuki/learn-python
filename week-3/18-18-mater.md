# Terlindungi: Hari 4 – Perbandingan Kuantitatif
Overview Materi
Pada materi-materi sebelumnya telah di perkenalkan tentang pondasi-pondasi visualisasi. Dari sekarang dan ke depan materi akan lebih advance lagi, pertama akan di perkenalkan beberapa bentuk visualisasi lainnya (sebelumnya telah di pelajari lineplot), kemudian akan di tunjukan kegunaannya untuk perbandingan kuantitatif.

Langsung saja. beberapa bentuk visualisasi yang akan di perkenalkan adalah :

Bar Chart
Scatter Plot
Histogram
Akan di gunakan data tentang penjualan video games dalam satuan juta dollar, yang mana filenya bisa di download disini.

https://blog.sanbercode.com/wp-content/uploads/2020/04/vgsales.csv

Datanya sebagai berikut :

import pandas as pd

df = pd.read_csv('vgsales.csv')
df.head()

Rank	Name	Platform	Year	Genre	Publisher	NA_Sales	EU_Sales	JP_Sales	Other_Sales	Global_Sales
0	1	Wii Sports	Wii	2006.0	Sports	Nintendo	41.49	29.02	3.77	8.46	82.74
1	2	Super Mario Bros.	NES	1985.0	Platform	Nintendo	29.08	3.58	6.81	0.77	40.24
2	3	Mario Kart Wii	Wii	2008.0	Racing	Nintendo	15.85	12.88	3.79	3.31	35.82
3	4	Wii Sports Resort	Wii	2009.0	Sports	Nintendo	15.75	11.01	3.28	2.96	33.00
4	5	Pokemon Red/Pokemon Blue	GB	1996.0	Role-Playing	Nintendo	11.27	8.89	10.22	1.00	31.37

Pengenalan Beberapa Bentuk Visualisasi
Bar Chart
Bar chart bisa di buat dengan method bar. Bar chart berguna untuk memvisualisasikan frekuensi kejadian suatu data berdasarkan suatu kategori. Jadi, bar chart ini di visualisasikan untuk membandingkan data yang bertipe kategori. Bar chart berguna bila jumlah kategori tidak lebih dari 30 pada umumnya. Apabila lebih dari itu, biasanya bar chart akan menjadi kacau sehingga data sulit untuk di interpretasi.

Berikut contoh sederhana dari visualisasi bar chart:

# import library
import pandas as pd
import matplotlib.pyplot as plt

# read data vgsales
df = pd.read_csv('vgsales.csv')

# extract data tentang banyaknya setiap jenis genre dalam data
data = df['Genre'].value_counts()
category = data.index
frequency = data.values

# plot data
fig, ax = plt.subplots()
ax.bar(category, frequency)
ax.set_xticklabels(category, rotation=90)
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-52.png

Dari gambar di atas dapat di lihat bahwa data ini memiliki paling banyak data video games dengan genre Action, kemudian Sport, dan seterusnya.

Method set_xticklabels() adalah untuk mengontrol komponen label data di sumbu x. di berikan label nya dengan data category, dan di putar sebesar 90 derajat agar label tidak bertumpuk.

Pada bahasan selanjutnya akan di tunjukan improvisasi terhadap visualisasi ini.

Scatter Plot
Scatter plot berguna untuk melakukan perbandingan data antara data bertipe numerik. untuk melakukan visualisasi scatter plot bisa dilakukan menggunakan method scatter().

Contoh akan di visualisasikan dengan scatter plot data tentang penjualan semua video games di jepang dan Europa.

fig, ax = plt.subplots()

# pembuatan plot
ax.scatter(df['JP_Sales'], df['EU_Sales'], c='g')

# axis labeling
ax.set_xlabel('Penjualan di Jepang')
ax.set_ylabel('Penjualan di Europa')
ax.set_title('Penjualan Semua Video Games')

plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-53.png

Histogram
Histogram mempunyai kemiripan dengan bar chart, beberapa keliru memahami bahwa bar chart sama dengan histogram. Kunci dari perbedaannya adalah Histogram untuk memvisualisasikan distribusi data dari suatu data bertipe numerik dan continues. sedangan bar chart untuk memvisualisasikan data bertipe kategori.

Misalkan ingin mengetahui perbedaan distribusi penjualan video games di seluruh dunia untuk game bergenre Action dan Sport. Berikut adalah contoh visualisasi dari Histogram nya :

action = df[df['Genre']=='Action']['Global_Sales']
sport = df[df['Genre']=='Sports']['Global_Sales']

fig, ax = plt.subplots(ncols=2, figsize=(16, 8))
ax[0].hist(action, bins=50)
ax[0].set_xlabel('Penjualan Global Game Action')
ax[0].set_ylabel('Frekuensi')
ax[0].set_title('Distribusi Game Action Global')

ax[1].hist(sport, bins=50, color='g')
ax[1].set_xlabel('Penjualan Global Game Sports')
ax[1].set_ylabel('Frekuensi')
ax[1].set_title('Distribusi Penjualan Game Sports Global')
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-54.png

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-54.png

Video Pembelajaran
Perbandingan Kuantitatif Scatter Plot 1

Belajar Data Science Maplotlib Visualisasi Scatter Plot Perbandingan Kuantitatif 1 : https://youtu.be/zduwtYbQnkE

Perbandingan Kuantitatif Scatter Plot 2

Belajar Data Science Matplotlib Visualisasi Scatter Plot Perbandingan Kuantitatif 2 : https://youtu.be/FTqGQXf-XOg

Perbandingan Kuantitatif Bar Plot 1

Belajar Data Science Matplotlib Visualisasi Bar Plot Perbandingan Kuantitatif 1 : https://youtu.be/gLEaW3MjiiU

Perbandingan Kuantitatif Bar Plot 2

Belajar Data Science Matplotlib Visualisasi Bar Plot Perbandingan Kuantitatif 2 : https://youtu.be/TxG_7vA6lCg

Perbandingan Kuantitatif Bar Plot 3

Belajar Data Science Matplotlib Visualisasi Bar Plot Perbandingan Kuantitatif 3 : https://youtu.be/vtbMImYNIzo
