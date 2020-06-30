# Terlindungi: Hari 2 – Custom Visualisasi
Pada materi sebelumnya telah di jelaskan cara membuat objek figure, axes, dan memplot data ke dalam axis tersebut.

Pada artikel ini akan di bahas tentang meng-custom visualisasi kita agar lebih informatif dan menarik.

Berikut adalah raw objek visualisasi data yang akan kita custom:

import matplotlib.pyplot as plt

# membuat component figure dan axis
fig, ax = plt.subplots()

data_x = [1, 2, 3, 4, 5, 6, 7]
data_y = [10, 20, 25, 30, 15, 18, 10]

# memberikan data kedalam axis
ax.plot(data_x, data_y)
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-39.png

Marker Data Point
Coba perhatikan bahwa bentuk plot dari data adalah berupa line plot, tidak dapat di ketahu dimana tepatnya data poin terletak. Terdapat sebuah argument dalam methode plot untuk memberikan marker/tanda terhadap data poin, argument tersebut adalah marker, perhatikan kode berikut:

import matplotlib.pyplot as plt

# membuat component figure dan axis
fig, ax = plt.subplots()

data_x = [1, 2, 3, 4, 5, 6, 7]
data_y = [10, 20, 25, 30, 15, 18, 10]

# memberikan data kedalam axis
ax.plot(data_x, data_y, marker='o')
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-40.png

Di atas telah di berikan nilai ‘o’ terhadap argument marker, ‘o’ artinya bulat, jadi di berikan marker bulat terhadap setiap data poin, sehingga dapat lebih jelas membedakan antara garis penghubung dengan data poin.

Nilai marker tidak hanya ‘o’ berikut opsi nilai untuk memberikan berbagai jenis bentuk marker terhadap data poin.

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-41.png

https://matplotlib.org/1.4.1/api/markers_api.html

Custom LineStyle
Garis penghubung antara data poin dapat di ubah dengan memberikan argument linestyle terhadap method plot, perhatikan contoh code berikut:

import matplotlib.pyplot as plt

# membuat component figure dan axis
fig, ax = plt.subplots()

data_x = [1, 2, 3, 4, 5, 6, 7]
data_y = [10, 20, 25, 30, 15, 18, 10]

# memberikan data kedalam axis
ax.plot(data_x, data_y, marker='x', linestyle='--')
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-44.png

Di atas di berikan nilai ‘–‘ terhadap argument linestyle, terdapat berbagai opsi untuk memberikan berbagai jenis bentuk terhdap linestyle, yaitu sebagai berikut :

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-43.png

Memilih Warna
Dapat di pilih warna plot dengan memberikan argument color terhadap method plot.

Memilih value untuk argument color bisa dengan berbagai bentuk format warna, seperti format RGB, hex code, atau label warna biasa seperti ‘r’ untuk red, ‘b’ untuk blue dan lain sebagainya. Dapat dilihat pada code berikut:

import matplotlib.pyplot as plt

# membuat component figure dan axis
fig, ax = plt.subplots()

data_x = [1, 2, 3, 4, 5, 6, 7]
data_y = [10, 20, 25, 30, 15, 18, 10]

# memberikan data kedalam axis
ax.plot(data_x, data_y, marker='D', linestyle='dotted', color='#9934FF')
plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-45.png

Custom Axis Label and Title
Komponen lain yang penting untuk di custom adalah axis label karena axis label menunjukan variabel apa yang sedang di plot.

Axis terdapat 2, yaitu x-axis dan y-axis. untuk mengubah x-axis dapat menggungkan method set_xlabel(), untuk mengubah y-axis dapat menggungkan set_ylabel().

Title juga adalah komponen yang sangat penting untuk menunjukan data apa yang sedang di visualisasikan. Untuk mengubah title dapat menggunakan method set_title().

Perhatikan contoh code berikut:

import matplotlib.pyplot as plt

# membuat component figure dan axis
fig, ax = plt.subplots()

data_x = [1, 2, 3, 4, 5, 6, 7]
data_y = [10, 20, 25, 30, 15, 18, 10]

# memberikan data kedalam axis
ax.plot(data_x, data_y, marker='D', linestyle='dotted', color='#9934FF')

# mengubah axis label dan title
ax.set_xlabel('X Label Axis')
ax.set_ylabel('Y Label Axis')
ax.set_title('Title of Graph')

plt.show()

https://blog.sanbercode.com/wp-content/uploads/2020/04/image-46.png

Belajar Data Science Customisasi Matplotlib Custom Legends : https://youtu.be/yj-Vdi0t4rk

