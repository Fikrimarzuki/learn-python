# Hari 3 – Logic Control Flow and Loop
Python memiliki sebuah tipe data bernama boolean, yang hanya memiliki 2 nilai, yaitu True atau False.

>>>x = True
>>>print(x)
>>>print(type(x))
True
<class 'bool'>
Daripada memasukan nilai boolean (True or False) langsung kepada variable, lebih baik mendapatkan nilai dengan melakukan suatu operasi. Operasi itu dinamakan comparison operator. Comparison operator ini yang nantinya akan memberikan jawaban nilai berdasarkan logic yang kita bangun. Ada beberapa dasar comparison operator, yaitu sebagai berikut :


def can_run_for_president(age):
    """Can someone of the given age run for president in the US?"""
    # The US Constitution says you must "have attained to the Age of thirty-five Years"
    return age >= 35

print("Can a 19-year-old run for president?", can_run_for_president(19))
print("Can a 45-year-old run for president?", can_run_for_president(45))

result :
Can a 19-year-old run for president? False
Can a 45-year-old run for president? True
Comparison cukup pintar juga, perhatikan :

print(3.0 == 3)
True
Tapi tidak terlalu pintar

print('3'==3)
False
Python menyediakan operator untuk menggabungkan nilai boolean menggunakan konsep bahasa standar yang biasa kita pahami seperti “and”, “or”, dan “not”.

Dengan ini, kita dapat membuat fungsi seperti ini :

def can_run_for_president(age, is_natural_born_citizen):
    """Can someone of the given age and citizenship status run for president in the US?"""
    # The US Constitution says you must be a natural born citizen *and* at least 35 years old
    return is_natural_born_citizen and (age >= 35)

print(can_run_for_president(19, True))
print(can_run_for_president(55, False))
print(can_run_for_president(55, True))

result : 
False
False
True
Boolean dan conditional operator sangat berguna dalam mengatur alur atau logic di dalam kode kita. Namun Boolean dan conditional akan lebih powerful ketika kita menggunakannya bersama conditional statement, dengan menggunakan keyword if, else, dan elif. Conditional statement biasa disebut dengan if-then.

Conditional Statement, memungkinkan programmer untuk mengeksekusi suatu kode tertentu tergantung pada beberapa kondisi Boolean. Contoh dasar dari pernyataan conditional Python adalah ini:

def inspect(x):
    if x == 0:
        print(x, "is zero")
    elif x > 0:
        print(x, "is positive")
    elif x < 0:
        print(x, "is negative")
    else:
        print(x, "is unlike anything I've ever seen...")

inspect(0)
inspect(-15)

result :
 0 is zero 
-15 is negative 
Loop
Loop adalah cara untuk berulang kali mengeksekusi beberapa kode. Ini sebuah contoh:

planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
for planet in planets:
    print(planet, end=' ') # print all on same line

result :
Mercury Venus Earth Mars Jupiter Saturn Uranus Neptune 
Ketika kita menggunakan loop, ada beberapa hal yang perlu diperhatikan :

Kita perlu memberikan nama variable yang akan digunakan (dalam contoh di atas adalah planet)
Serentetan nilai yang ingin kita looping untuk melakukan operasi kepada setiap elemennya ( dalam contoh di atas adalah planets ).
range(), range() adalah suatu fungsi yang menghasilkan suatu baris nilai. Lebih jauhnya lagi ,kita bisa menggunakan fungsi help yang telah kita pelajari sebelumnya untuk lebih faham berbagai macam cara untuk menggunakannya. Berikut merupakan satu contoh sederhana :

for i in range(5):
    print("Doing important work. i =", i)

result :
Doing important work. i = 0
Doing important work. i = 1
Doing important work. i = 2
Doing important work. i = 3
Doing important work. i = 4
Di python ada sebuah fungsi bawaan yang bernama enumerate(). Enumerate() memungkinkan kita untuk melakukan loop terhadap suatu object semacam list disertai dengan pengambilan index dari setiap elemennya. Contohnya seperti berikut :

areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Change for loop to use enumerate() and update print()
for index,area in enumerate(areas) :
    print("room"+str(index)+": "+str(area))

result :
room0: 11.25
room1: 18.0
room2: 20.0
room3: 10.75
room4: 9.5
Jenis loop lain dalam python adalah while loop, yang terus menerus melakukan looping sampai memenuhi suatu kondisi yang membuat dia harus berhenti, berikut contohnya :

i = 0
while i < 10:
    print(i, end=' ')
    i += 1

result :
0 1 2 3 4 5 6 7 8 9 
Argumen dari while loop dievaluasi setiap looping, dan loop dijalankan sampai hasil evaluasi dari conditional operator bernilai False.

## External Resource
Percabangan:

Belajar Python #5a - If Elif Else: https://youtu.be/Hqndpzj0ZFg

Belajar Python #5b - If Elif Else(Lanjutan): https://youtu.be/f28RoIcHZhY

Loop:

Belajar Python #6 - For Loop: https://youtu.be/KMmZo_dvmyk

Belajar Python #7 - For Else, Range, Break: https://youtu.be/L5GGd1JHqnE

Belajar Python #8 - Continue dan Pass: https://youtu.be/sLxR7vvPemY

Belajar Python #9 - While Loop: https://youtu.be/S8PxQTcme9k

Tambahan:

Belajar Python # 20 - Teknik Looping: https://youtu.be/ZnBZWAUusj8


List Artikel:
  * https://www.petanikode.com/python-percabangan/
  * https://www.petanikode.com/python-perulangan/

Docs Python:
  * https://docs.python.org/3/tutorial/introduction.html
  * https://docs.python.org/3/tutorial/controlflow.html
  * https://docs.python.org/3/library/operator.html?highlight=operator
  
  

https://blog.sanbercode.com/docs/kurikulum-python-data-science/week-1/logic-control-flow-and-loop/

