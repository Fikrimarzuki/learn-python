# Terlindungi: Hari 1 – Pengenalan Matplotlib
Pengenalan
Manusia adalah makhluk visual. kita dapat lebih mudah memahami sesuatu lebih baik dengan visualisasi. kita dapat lebih mudah menemukan pola-pola yang mungkin tersembunyi apa bila kita bisa melihatnya secara visual.

Pada artikel ini kita akan membahasa suatu topik tentang Visualisasi menggunakan liblary matplotlib. kita akan belajar bagaimana caranya membuat objek visual yang informatif dan menarik.

Matplotlib adalah suatu liblary yang low-level untuk membangun objek visual. maksudnya low-level bukan jelek ya. tapi low-level ini memberikan kita control sampai ke komponen-komponen kecilnya. kalau misalkan kita buat mobil, kita mengontrol sampai pembuatan ke baut bautnya. Oleh karena itu matplotlib penting di fahami sebagai dasar apabila ingin mendalami bidang visualisasi data.

Install Liblary Matplotlib
Untuk dapat menggunakan liblary matplotlib, install terlebih dahulu liblary tersebut dengan :

pip install matplotlib

atau

conda install matplotlib

Komponen Besar : Figure dan Axes
Kita akan membahasa top-level component, yaitu komponen terbesar dalam suatu objek visualisasi, Figure dan Axes.

Sebelum dijelaskan lebih jauh lagi, mari lihat terlebih dahulu seperti apa contoh sederhana visualisasi data.

import random
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 10, 100)
y = [random.random()*100 for i in range(100)]

plt.figure(figsize=(12, 8))
plt.plot(x, y)
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-35.png

Ok, sampai sini setidaknya kalian mempunyai gambaran besar tentang objek visual data. Kita akan lanjut bahas tentang komponen terbesar dalam objek visual ini.

Figure, adalah window atau page atau halaman dalam objek visual. kalau kita ngegambar di kertas, maka kertas tersebutlah yang di namakan figure.

Axis, kedalam Figure kita menambahkan Axis, Axis adalah suatu area di dalam figure dimana data akan di plot. di dalam Axis juga terdapat berbagai macam komponen lagi seperti x-axis, y-axis, dan lain sebagainya. hal ini akan kalian lihat di artikel ke dua.

Setelah memahami komponen terbesar dari matplotlib, berikut akan di tunjukan beberapa macam perintah kode untuk membuat component-component tersebut dan memberiakan data kepada komponent Axis.

Beikut adalah method untuk membuat figure :

import matplotlib.pyplot as plt

fig = plt.figure()
print(fig)
===========
<Figure size 432x288 with 0 Axes>
Perhatikan kita mempunyai objek Figure dengan 0 Axis. sekarang kita akan menambahkan axis kedalam objek figure kita dengan method add_subplot(). kemudian kita tunjukan objek figure kita dengan method show().

# membuat objek figure
fig = plt.figure()
# membuat objek axes
ax = fig.add_subplot()
# menampilkan objek visual
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-36.png

Sekarang kita akan tambahkan data kedalam objek tersebut dengan memanggil method plot() dan memberikan data sebagai argument method tersebut :

# membuat objek figure
fig = plt.figure()

# membuat objek axes
ax = fig.add_subplot()

# membuat data
data_x = [1, 2, 3, 4, 5]
data_y = [10, 20, 25, 30, 15]

# menambahkan dalam ke objek axes
ax.plot(data_x, data_y)

# menampilkan data
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-37.png

Begitulah cara sederhana untuk membuat objek visualisasi, sekarang akan di tunjukan cara lain yang lebih clean.

# membuat objek visual
plt.plot(data_x, data_y)
# menampilkan objek visual
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-37.png

Perhatikan, kedua cara tadi menghasilkan hasil yang sama. tapi cara kedua lebih clean karena tidak memerlukan banyak kode. sebenarnya ke dua cara tersebut sama-sama menghasilkan komponen Figure dan Axis. tetapi cara pertama Explicit sedangkan cara kedua Implicit.

Cara yang Explicit di rekomendasikan ketika kita ingin membuat visualisasi data yang lebih kompleks. karena kita dapat mengonrol berbagai macam komponen yang terdapat di dalam objek figure dan axes, saat ini kalian belum banyak melihat komponen tersebut, materi ini akan diberikan di materi ke 2.

Namun, kita juga dapat membuat cara visualisasi data lebih simple dengan menggabungkan pembuatan objek Figure dan Axis dengan sekali jalan, melalui pemanggilan method subplots(), seperti ini :

# membuat objek figure dan axes
fig, ax = plt.subplots()

# membuat data
data_x = [1, 2, 3, 4, 5]
data_y = [10, 20, 25, 30, 15]

# menambahkan dalam ke objek axes
ax.plot(data_x, data_y)

# menampilkan data
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-37.png

Memungkinkan untuk memplot lebih dari satu data kedalam suatu axis dengan cara seperti ini :

fig, ax = plt.subplots()
data_x1 = [1, 2, 3, 4]
data_y1 = [10, 20, 25, 30]
data_x2 = [1, 2, 3, 4, 5]
data_y2 = [5, 15, 20, 25, 30]
ax.plot(data_x1, data_y1)
ax.plot(data_x2, data_y2)
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-38.png

Video Belajar

Data Science Pengenalan Matplotlib

Data Science Pengenalan Matplotlib: https://youtu.be/5DUjDr_iCQ4

Klarifikasi Bahan Poin Terakhir Pengenalan Matplotlib: https://youtu.be/lxpf566gsDY

