Terlindungi: Hari 5 – Merging DataFrame
Menggabungkan data adalah salah satu hal yang penting dalam suatu pekerjaan data analyst atau data science. karena dalam banyak kasus data selalu berada dri berbagai file dan sumber. Maka menguasai penggabungan data beserta logika-logika penggabungan data menjadi hal yang esensi untuk di kuasai.

Pandas menyediakan berbagai tool atau method yang memudahkan kita untuk melakukan penggabungan data dengan berbagai macam logik. method-method tersebut diantaranya seperti join(), merge(), concat(). kali ini kita kan mempelejari beberapa teknik tersebut.

Ada beberapa logika penggabungan data, diantaranya adalah :

Inner Join
Full Outer Join
Left Outer Join
Right Outer Join
dll.
Hive Join | HiveQL Select Joins Query | Types of Join in Hive ...
source : https://d2h0cx97tjks2p.cloudfront.net/blogs/wp-content/uploads/sites/2/2018/03/Types-of-Hive-joins.jpg
Penggabungan Baris dan Column dengan Metod concat()
Concat adalah salah satu metode untuk melakukan penggabungan data berdasarkan sumbu tertentu. langsung saja kita lihat.

misalkan kita mempunyai data seperti ini :

import pandas as pd

df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
                            'B': ['B0', 'B1', 'B2', 'B3'],
                            'C': ['C0', 'C1', 'C2', 'C3'],
                            'D': ['D0', 'D1', 'D2', 'D3']},
                           index=[0, 1, 2, 3])

df2 = pd.DataFrame({'A': ['A4', 'A5', 'A6', 'A7'],
                            'B': ['B4', 'B5', 'B6', 'B7'],
                            'C': ['C4', 'C5', 'C6', 'C7'],
                            'D': ['D4', 'D5', 'D6', 'D7']},
                           index=[4, 5, 6, 7])

df3 = pd.DataFrame({'A': ['A8', 'A9', 'A10', 'A11'],
                            'B': ['B8', 'B9', 'B10', 'B11'],
                            'C': ['C8', 'C9', 'C10', 'C11'],
                            'D': ['D8', 'D9', 'D10', 'D11']},
                           index=[8, 9, 10, 11])

Perhatikan, data yang kita punya sangatlah simple, kita mempunyai 3 data yang mempunyai nama column yang sama. apabila kita ingin menggabungkan baris data ini, kita bisa menggunakan suatu method concat(). pertama kita buat terlebih dahulu list dari data yang akan kita gabung, kemudian masukan list tersebut sebagai argument kedalam method concat(). seperti ini.

# list data yang akan di gabung
list_dataframe = [df1, df2, df3]
# gabungkan data dengan metode concat dari pandas
pd.concat(list_dataframe)
A	B	C	D
0	A0	B0	C0	D0
1	A1	B1	C1	D1
2	A2	B2	C2	D2
3	A3	B3	C3	D3
4	A4	B4	C4	D4
5	A5	B5	C5	D5
6	A6	B6	C6	D6
7	A7	B7	C7	D7
8	A8	B8	C8	D8
9	A9	B9	C9	D9
10	A10	B10	C10	D10
11	A11	B11	C11	D11
Berikut hasilnya, hasil tersebut merupakan gabungan yang seperti ini :


Apabila kita ingin menggabungkan data tersebut berdasarkan column, kita mesti memberikan satu argument lagi kedalam method concat yaitu axis, dengan nilai 1. seperti ini

pd.concat(list_dataframe, axis=1)
A	B	C	D	A	B	C	D	A	B	C	D
0	A0	B0	C0	D0	NaN	NaN	NaN	NaN	NaN	NaN	NaN	NaN
1	A1	B1	C1	D1	NaN	NaN	NaN	NaN	NaN	NaN	NaN	NaN
2	A2	B2	C2	D2	NaN	NaN	NaN	NaN	NaN	NaN	NaN	NaN
3	A3	B3	C3	D3	NaN	NaN	NaN	NaN	NaN	NaN	NaN	NaN
4	NaN	NaN	NaN	NaN	A4	B4	C4	D4	NaN	NaN	NaN	NaN
5	NaN	NaN	NaN	NaN	A5	B5	C5	D5	NaN	NaN	NaN	NaN
6	NaN	NaN	NaN	NaN	A6	B6	C6	D6	NaN	NaN	NaN	NaN
7	NaN	NaN	NaN	NaN	A7	B7	C7	D7	NaN	NaN	NaN	NaN
8	NaN	NaN	NaN	NaN	NaN	NaN	NaN	NaN	A8	B8	C8	D8
9	NaN	NaN	NaN	NaN	NaN	NaN	NaN	NaN	A9	B9	C9	D9
10	NaN	NaN	NaN	NaN	NaN	NaN	NaN	NaN	A10	B10	C10	D10
11	NaN	NaN	NaN	NaN	NaN	NaN	NaN	NaN	A11	B11	C11	D11
Coba kalian perhatikan, penggabungan ini adalah penggabungan sumbu column pada setiap dataframe, dan pada sumbu baris di lakukan penggabungan juga berdasarkan indeks. secara default logika penggabunganya adalah outer join. kita akan melihat beberapa logika penggabungan setelah ini.

Logika-Logika Penggabungan Dengan Metode merge
Full Outer Join

source : https://static.cdn-cdpl.com/source/998b78e349061b4971c0a2b0e8d6be41/sql6.png
Full Outer Join menghasilkan gabungan index bari dari setiap data yang di gabung.
Full Outer Join menggabungan pula column yang berbeda
Memberikan nilai null untuk nilai column yang tidak di miliki oleh suatu index tertentu.
Misalkan kita mempunyai data seperti ini :

left = pd.DataFrame({'key': ['K0', 'K1', 'K2', 'K3'],
                              'A': ['A0', 'A1', 'A2', 'A3'],
                              'B': ['B0', 'B1', 'B2', 'B3']})

right = pd.DataFrame({'key': ['K0', 'K1', 'K4', 'K5'],
                                 'C': ['C0', 'C1', 'C2', 'C3'],
                                 'D': ['D0', 'D1', 'D2', 'D3']})

print('data pertama')
print(=========)
print(left)
print('data kedua')
print(=========)
print(right)
data pertama
=========
  key   A   B
0  K0  A0  B0
1  K1  A1  B1
2  K2  A2  B2
3  K3  A3  B3
data kedua
=========
  key   C   D
0  K0  C0  D0
1  K1  C1  D1
2  K4  C2  D2
3  K5  C3  D3
Kita akan menggabungkan data ini denga menggunakan method merge() dari pandas. dalam penggabungan kita kan gunakan column key dari data kita sebagai variabel identifier dari data kita, atau sebagai column key/referensi.

Untuk melakukan penggabungan dengan menggunakan column key sebagai referensi penggabungan, maka kita akan memberikan argument on dengan nilai ‘key’
untuk melakukan penggabungan outer join kita akan memberikan argument how dengan nilai ‘outer’
# gabungkan data dengan logika outer join
pd.merge(left, right, on='key', how='outer')
key	A	B	C	D
0	K0	A0	B0	C0	D0
1	K1	A1	B1	C1	D1
2	K2	A2	B2	NaN	NaN
3	K3	A3	B3	NaN	NaN
4	K4	NaN	NaN	C2	D2
5	K5	NaN	NaN	C3	D3
Inner Join

source : https://static.cdn-cdpl.com/source/998b78e349061b4971c0a2b0e8d6be41/sql1.png
Inner join ini akan menggabungkan data antara nilai key/referensi yang beririsan.

Kita akan mencoba melakukan inner join dengan data yang sama pada outer join, Untuk melakukan inner join dengan metode merge(), kurang lebih sama seperti yang di lakukan pada outer join, kita hanya perlu mengubah argument argument how menjadi inner.

pd.merge(left, right, on='key', how='inner')
key	A	B	C	D
0	K0	A
0	B0	C0	D0
1	K1	A1	B1	C1	D1
Coba perhatikan, bahwa data yang di gabungkan adalah data yang mempunyai nilai key beririsan.

Left Join

source : https://static.cdn-cdpl.com/source/998b78e349061b4971c0a2b0e8d6be41/sql2.png
Left Outer Join menghasilkan seluruh data dari data yang kiri ditambah data kanan yang memiliki nilai key yang sama dengan data dari kiri.

Kita akan mencoba melakukan left outer join dengan data yang sama pada outer join, untuk melakukan left outer join kita hanya perlu memberikan nilai ‘left’ kepada argument how.

pd.merge(left, right, on='key', how='left')
key	A	B	C	D
0	K0	A0	B0	C0	D0
1	K1	A1	B1	C1	D1
2	K2	A2	B2	NaN	NaN
3	K3	A3	B3	NaN	NaN
Right Join
Right outer join ini hanya kebalikan dari left outer join.

Untuk melakukan operasi penggabungan right outer join dengan metode merge, kita hanya perlu memberikan nilai ‘right’ pada argument how.

pd.merge(left, right, on='key', how='right')
key	A	B	C	D
0	K0	A0	B0	C0	D0
1	K1	A1	B1	C1	D1
2	K4	NaN	NaN	C2	D2
3	K5	NaN	NaN	C3	D3

Video Pembelajaran

Belajar Pandas: Menggabungkan Data : https://youtu.be/BeTEJCThNXk

Belajar Pandas: Menggabungkan Data 2 : https://youtu.be/n2QuPsIcUW0

External Source
List Artikel :

https://www.it-swarm.dev/id/python/penggabungan-panda-101/807882802/




https://blog.sanbercode.com/docs/kurikulum-python-data-science/week-2/day-5-videos/

