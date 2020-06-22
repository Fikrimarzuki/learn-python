# Hari 4 – Python List dan Dictionary

List
List adalah salah satu tipe data untuk mengoleksikan data di python. Contohnya, kita punya koleksi data suhu semua anggota keluarga kita, untuk menyimpan data ini, tentunya lebih mudah kalau kita menyimpannya dalam satu tempat, dan tempat itu salah satunya bisa bernama list. Mengapa salah satunya? Karena tempat menyimpan koleksi data di python tidak hanya list, ada tipe data lain seperti dictionary, tuple, set dan lain-lain. Namun dalam pembahasan ini kita akan fokus membahas tentang list.

Sampai di sini setidaknya kita sudah dapat sedikit gambaran tentang apa itu list. Selanjutnya kita akan coba pelajari bagaimana cara membuat list di python.. Berikut caranya..

# inisialisasi suhu anggota keluarga
suhu1 = 21
suhu2 = 20
suhu3 = 22

# simpan dalam list
suhu_keluarga = [suhu1, suhu2, suhu3]
Akses Data List
Setelah kita bisa membuat data sederhana dengan list. Sekarang kita akan belajar bagaimana caranya mengakses data dalam list. Untuk mengakses data dalam list, python menggunakan sesuatu yang bernama index. Index menunjukan posisi suatu data di dalam list, dan python memulai index dari 0. Perlu diketahui sebelumnya bahwa ada 2 teknik untuk mengakses data di dalam list. Pertama dengan subsetting list, kedua dengan slicing list. Mari kita lihat contohnya :

# Membuat data list
>>> tinggi_badan = [
                162, # index 0 
                177, # index 1
                182, # index 2
                150, # index 3
                166 # index 4
                ]

# Subsetting list
>>> print(tinggi_badan[0]) # posisi pertama
162
>>> print(tinggi_badan[-2]) # posis kedua dari belakang
150

# Slicinglist
# Mengambil data dengan index 0, 1, 2, 3
>>> print(tinggi_badan[:4]) 
[162, 177, 182, 150, 166]
# Mengambil data dengan index 2, 3, 4
>>> print(tinggi_badan[2:5])
[182, 150, 166]
Sifat List
Sebelumnya, kita sudah mengenal sedikit tentang list, mari kita kenal lebih dalam lagi tentang list.

List berisi koleksi nilai/data.
List bisa berisi tipe data apapun dan tidak harus semua data berisi tipe data yang sama.
List bisa berubah
Untuk sifat no 1. sudah dijelaskan dan tunjukan di atas. Sekarang kita langsung bahas sifat no.2. Sebelumnya, kita sudah mengenal tentang beberapa tipe data dalam list, ada numerik, string, boolean, dan sebagainya. Nah, nilai-nilai yang bertipe data apapun dapat dimasukan sebagai koleksi di dalam list, bahkan list itu sendiri bisa ada di dalam list. Untuk lebih jelasnya mari kita lihat contoh berikut..

# membuat list
suhu_keluarga_ucup = [
                'ayah ucup', 19, 'ucup', 19, 'ibu ucup', 20
                ]
suhu_keluarga_boy = [
                'istri boy', 20, 'anak boy', 18, 'istri kedua boy', 21
                ]

# membuat list dalam list dan di campur dengan data boolean
suhu_keluarga = [
                suhu_keluarga_ucup, suhu_keluarga_boy 
                ]
Manipulasi List 
List adalah “mutable”, artinya dapat diubah.

Salah satu cara untuk mengubah daftar adalah dengan menetapkan indeks atau ekspresi irisan.
#
Misalnya, katakanlah kita ingin mengubah suhu ucup:

# mengubah suhu ucup
suhu_keluarga_ucup[3] = 22

print(suhu_keluarga_ucup)
>>> ['ayah ucup', 19, 'ucup', 22, 'ibu ucup', 20]
katakanlah kita ingin mengganti ‘ibu ucup’ dengan ‘mamah ucup’, beserta suhunya :

suhu_keluarga_ucup[-2:] = ['mamah ucup', 22]
print(suhu_keluarga_ucup)
>>> ['ayah ucup', 19, 'ucup', 22, 'mamah ucup', 22]
kita juga bisa menambahkan elemen di list, yaitu dengan menggunakan ‘+’ operator, katakanlah kita ingin menambahkan adik ucup beserta suhunya, berikut contohnya :

suhu_keluarga_ucup = suhu_keluarga_ucup + ['adik ucup', 20]

print(suhu_keluarga_ucup)
>> ['ayah ucup', 19, 'ucup', 22, 'mamah ucup', 22, 'adik ucup', 20]
terakhir, kita juga bisa menhilangkan element di dalam list, yaitu seperti ini :

del(suhu_keluarga_ucup[0])
Perhatian, setelah suatu elemen di dalam list dihapus, maka index dari seluruh elemennya pun akan berubah, contohnya di atas kita mendelete elemen dengan index 0 di list, artinya kita mendelete elemen ‘ayah ucup’, maka elemen yang lain akan berubah menyesuaikan dengan perubahan tersebut, maka ketika kita mengambil index 0 di list tersebut maka hasilnya akan seperti ini :

print(suhu_keluarga_ucup[0])
>>>19
Some Function in List
Python memiliki beberapa fungsi bawaan yang berguna untuk bekerja dengan list. diantaranya adalah :

‘len’ memberikan panjang daftar:

keluarga_ucup = ['mamah', 'papah', 'ucup', 'adek ucup', 'kaka ucup']

# berapa banyak anggota keluarga ucup
print(len(keluarga_ucup))
>>>5
‘sorted’ mengurutkan elemen list:

>>>print(sorted(keluarga_ucup))
>>>['adek ucup', 'kaka ucup', 'mamah', 'papah', 'ucup']
‘sum’, tentu fungsi ini untuk menjumlahkan:

primes = [2, 3, 5, 7]
print(sum(primes))
>>>17
Dictionary
Dictionary adalah suatu topik yang sangat penting dalam python dan data science. Karena dictionary seperti penyusun untuk suatu objek yang lebih kompleks seperti pandas dataframe yang akan kita pelajari nanti.

Jadi, dictionary ini adalah salah satu jenis tipe data di python yang memetakan antara key dan value dari suatu data. Berikut contohnya:

numbers = {'one':1, 'two':2, 'three':3}
Kita dapat mengakses suatu nilai dalam dictionary dengan cara seperti ini:

>>>print(numbers['one'])
1
Kita juga dapat mengubah suatu nilai dalam dictionary dengan cara berikut:

>>>numbers['one'] = 'satu'
>>>print(numbers)
 {'one':satu, 'two':2, 'three':3}
Perhatikan value dari key ‘one’ berubah dari awalnya 1 menjadi ‘satu’

Jika kita melakukan loop pada suatu dictionary, maka kita akan me-loop terhadap key pada dictionary tersebut:

or k in numbers:
    print("{} = {}".format(k, numbers[k]))

result :
one = satu
two = 2
three = 3
Object dictionary mempunyai suatu method yang bernama items(), dimana dengan fungsi ini kita dapat melakukan loop terhadap suatu dictionary beserta dengan key dan value nya:

for k, v in numbers.items():
    print("{} = {}".format(k, v))

result:
one = satu
two = 2
three = 3
Untuk memahami lebih jauh lagi tentang dictionary, kita bisa menggunakan fungsi help sebagai penolong.


## External Resources
Python Datetime :

[Python Data Science ToolBox] : Python Datetime: https://youtu.be/3uCjs4LU0Jg

Python List: https://youtu.be/kuLBqkpnKDk

[Python Data Science ToolBox] : Penyusunan Element atau Sorting: https://youtu.be/jtO_aX1zn30

List vs Tuple :

[Python Data Science ToolBox] : Apa itu Tuple? Tuple vs List: https://youtu.be/tOJb2HvorZI

Python Dictionary:

Belajar Python #19-tipe data Dictionary: https://youtu.be/ARfcEqYpzkk


List Artikel/ Tutorial:
  * https://www.petanikode.com/python-list/
  * https://belajarpython.com/tutorial/dictionary-python
  * https://www.petanikode.com/python-dictionary/






=========
# Tambahan Tugas Hari 4
=========

1. Remove Duplicate List
Buatlah sebuah fungsi, yang menerima suatu argument objek list, dan return sebuah objek list baru, dimana objek list baru ini berisi list sebelumnya dikurangi dengan data yang duplikat, sehingga setiap element di dalam list adalah unik.

Berikan 2 solusi, solusi pertama menggunakan loop dan list, solusi yang kedua menggunakan objek set!

Video tentang set:

Belajar Python #18 - tipe data Set: https://youtu.be/Fn6073uEifE

Hint:

# solusi tanpa menggunakan set
def remove_duplicate(obj_list):
    ''''
    code Here
    ''''
    return new_list

# solusi dengan menggunakan set
def remove_duplicate_with_set(obj_list):
    ''''
    code Here
    ''''
    return new_list

obj_list = [1, 2, 4, 6, 2, 1, 4, 5, 7, 8, 6]
print(remove_duplicate(obj_list))
print(remove_duplicate_with_set(obj_list))

output :
[1, 2, 4, 6, 5, 7, 8]
[1, 2, 4, 5, 6, 7, 8]

2. Membuat ChatBot Sederhana
Buatlah sebuah fungsi chatbot yang memberikan suatu respon dimana chatbot ini menerima satu argument string.

Buah sebuah fungsi chatbot yang memberikan suatu respon dimana chatbot ini menerima satu argument string.

Jika argument adalah pertanyaan kemudian chatbot mengecek lagi apakah pertanyaan tersebut adalah pertanyaan yang bisa di jawab atau tidak. Jika pertanyaannya bisa di jawab maka fungsi akan memberikan jawaban yang bersifat random berdasarkan opsi list jawaban yang disediakan berdasarkan jenis pertanyaan tersebut. Jika tidak maka chatbot akan memberikan jawaban default bahwa chatbot tidak mengerti pertanyaannya.

Jika argument adalah bukan pertanyaan maka chatbot akan memberikan sebuah statement random yang disediakan.


Hint:

# import library
from datetime import datetime
import random

# ganti dengan sebuah nama
nama  = "Nama Anda"
# variabel tanggal
tanggal = datetime.now().day
# default variabel untuk pertanyaan tidak diketahui
default = "maaf, aku tidak tahu jawaban dari pertanyaanmu"

# Membuat objek dictionary berisi berbagai opsi jawaban

# list jawaban untuk pertanyaan tentang nama
jawaban_nama = [
      "nama saya  {0}".format(nama),
      "orang-orang memanggil saya {0}".format(nama),
      "panggil saja saya {0}".format(nama)
   ]

# list jawaban untuk pertanyaan tentang tanggal
jawaban_tanggal = [
      "hari ini tanggal {0}".format(tanggal),
      "ya ampun masa tidak tahu, hari ini tanggal".format(tanggal)
    ]

# opsi pertanyaan yang bisa dijawab
pertanyaan = {
  "nama kamu siapa?": jawaban_nama,
  "kamu siapa?" : jawaban_nama,
  "tanggal berapa hari ini?": jawaban_tanggal,
  "hari ini tanggal berapa?" : jawaban_tanggal,
  "default": default
}

# list jawaban untuk sebuah argument selain pertanyaan
statement =  [
                'ceritakan lebih banyak!',
                'kenapa kamu berpikir begitu?',
                'sudah berapa lama kamu merasa seperti ini?',
                'Itu sangat menarik!',
                'oh wow!',
                ':)'
              ]

# respon keseluruhan
responses = {
    'pertanyaan' : pertanyaan,
    'statement' : statement
}
#------
             
# ayo buat chatbotmu
def chatbot(message):
    ## code disini

print(chatbot('Selamat Pagi'))
print(chatbot('Mau bermain bersamaku?'))
print(chatbot('nama kamu siapa?'))
print(chatbot('hari ini tanggal berapa?'))

output :
:)
maaf, aku tidak tahu jawaban dari pertanyaanmu
orang-orang memanggil saya Nama Anda
ya ampun masa tidak tahu, hari ini tanggal

Penjelasan
Pada code yang ini print(chatbot(‘Selamat Pagi’)), chatbot melihat list opsi jawaban yang ada pada variabel statement, kemudian memilih secara random jawaban yang akan diberikan.
Pada code yang ini print(chatbot(‘Mau bermain bersamaku?’)), chatbot melihat bahwa pesan ini adalah sebuah pertanyaan karena di akhiri dengan tanda tanya, kemudian value dari key ‘default’ karena pertanyaan tersebut tidak bisa dijawab oleh chatbot.
Pada code yang ini print(chatbot(‘nama kamu siapa?’)), chatbot melihat bahwa pesan ini adalah sebuah pertanyaan karena di akhiri dengan tanda tanya, kemudian melihat pada variabel ‘jawaban_nama’ dan memilih secara random jawaban yang akan di berikan.
Pada code yang ini print(chatbot(‘hari ini tanggal berapa?’)), chatbot melihat bahwa pesan ini adalah sebuah pertanyaan karena di akhiri dengan tanda tanya, melihat pada variabel ‘jawaban_tanggal’ dan memilih secara random jawaban yang akan diberikan.

Lingkup Materi :
String
Dictionary
If-elif-else
Fungsi
List
Library/Module Random
