# Terlindungi: Hari 5 – Seaborn dan Altair Seaborn

Matplotlib telah terbukti sangat berguna dan merupakan tool visualisasi yang cukup terkenal, tapi beberapa pengguna mengeluhkan karena untuk menghasilkan fitur yang kecil saja membutuhkan codingan yang banyak, Matplotlib juga hadir satu dekade lebih awal daripada Pandas sehingga tidak cocok untuk disandingkan dengan DataFrames Pandas, untuk mem-visualisasikan data dari DataFrame Pandas, kita harus mengambil masing-masing Series-nya kemudian menggabungkannya ke dalam format yang sesuai. Alangkah baiknya jika ada library untuk plotting yang dapat menggunakan label dari DataFrame ketika menggambarkan plotnya.

Jawaban untuk permasalahan di atas adalah Seaborn. Seaborn merupakan API yang berdasar dari Matplotlib, memiliki high-level function untuk tipe plot yang umum digunakan untuk statistik, Seaborn juga dapat diintegrasikan dengan DataFrames dari Pandas.

Meskipun Matplotlib sudah menambahkan plt.style sehingga memudahkan untuk menangani Pandas, Seaborn tetap sangat direkomendasikan untuk digunakan.

Seaborn vs. Matplotlib
Perhatikan contoh plot sederhana pada Matplotlib berikut:

import matplotlib.pyplot as plt
plt.style.use('classic')
%matplotlib inline
import numpy as np
import pandas as pd

# Buat beberapa data
sat = np.random.RandomState(0)
x = np.linspace(0, 10, 500)
y = np.cumsum(sat.randn(500, 6), 0)

# Plot data menggunakan setting default Matplotlib
plt.plot(x, y)
plt.legend('HIJKLM', ncol=3, loc='lower left');

https://blog.sanbercode.com/wp-content/uploads/2020/06/1-2.png

Meskipun hasilnya memiliki semua informasi yang kita inginkan, tampilannya kurang memiliki nilai estetika, dan bahkan terlihat jadul untuk visualisasi di abad 21 ini.

Sekarang perhatikan contoh penggunaan Seabon untuk data yang sama:

import seaborn as sns
sns.set()

# Menggunakan data yang sama dengan di atas
plt.plot(x, y)
plt.legend('HIJKLM', ncol=3, loc='lower left');

https://blog.sanbercode.com/wp-content/uploads/2020/06/2-1.png

Lebih keren dikit ya kan..

Exploring Seaborn Plots
Tujuan utama Seaborn yaitu menyediakan perintah high-level untuk membuat berbagai jenis plot yang berguna pada eksplorasi data statistika, atau bahkan fitting model statistika.

Mari kita lihat beberapa jenis plot yang tersedia di Seaborn. Catatan: contoh berikut dapat dihasilkan menggunakan perintah Matplotlib, tapi menggukan API Seaborn akan lebih menyenangkan.

Histogram, KDE, dan density
Seringkali pada visualisasi data statistika, yang kita perlukan hanyalah histogram dan joint distribution dari beberapa variabel. Contoh histogram sebagai berikut:

data = np.random.multivariate_normal([0, 0], [[5, 2], [2, 2]], size=2000)
data = pd.DataFrame(data, columns=['x', 'y'])

for col in 'xy':
    plt.hist(data[col], bins=10, density=True, alpha=0.5)

https://blog.sanbercode.com/wp-content/uploads/2020/06/3-1.png

Kita juga dapat menghasilkan estimasi yang tidak kasar dari distribusi tersebut menggunakan kernel density estimation (KDE) yang dapat dihasilkan menggunakan Seaborn dengan sns.kdeplot:

for col in 'xy':
    sns.kdeplot(data[col], shade=True)

https://blog.sanbercode.com/wp-content/uploads/2020/06/4.png

Histogram dan KDE dapat digabungkan menggunakan distplot:

sns.distplot(data['x'])
sns.distplot(data['y']);

https://blog.sanbercode.com/wp-content/uploads/2020/06/5.png

Jika kita menggunakan kedua data dari dataset ke dalam kdeplot, maka akan menghasilkan visualisasi dua-dimensi dari data tersebut:

sns.kdeplot(data['x'], data['y']);

https://blog.sanbercode.com/wp-content/uploads/2020/06/6-1.png

Kita dapat melihat joint distribution dan marginal distribution secara bersamaan menggunakan sns.jointplot. Untuk plot ini, kita gunakan style white background:

with sns.axes_style('white'):
    sns.jointplot(data['x'], data['y'], kind='kde')

https://blog.sanbercode.com/wp-content/uploads/2020/06/7-1.png

Ada beberapa parameter lain yang dapat kita ganti pada jointplot, contohnya adalah kita dapat menggunkaan histogram dengan base hexagonal:

with sns.axes_style('white'):
    sns.jointplot(data['x'], data['y'], kind='hex');

https://blog.sanbercode.com/wp-content/uploads/2020/06/8.png

Pair plots
Ketika kita membuat joint plot menggunakan dataset dengan dimensi yang lebih besar, maka akan menghasilkan pair plots, yang sangat berguna untuk mengeksplorasi hubungan antar data multidimensi, juga melihat pair plots secara berpasangan.

Kita akan menggunakan dataset Iris yang cukup terkenal, berisi ukuran petal dan sepal iris dari tiga spesies:

iris = sns.load_dataset("iris")
iris.head()

https://blog.sanbercode.com/wp-content/uploads/2020/06/Screen-Shot-2020-06-30-at-17.06.37.png

Mem-visualisasikan dengan mudah hubungan multidimensi dari beberapa sampel menggunakan sns.pairplot:

sns.pairplot(iris, hue='species');

https://blog.sanbercode.com/wp-content/uploads/2020/06/9.png

Faceted histograms
Terkadang, langkah terbaik ntuk menganalisa data adalah menggunakan histogram dari bagian-bagiannya. FacetGrid milik Seaborn menjadikan langkah ini sangat mudah. Kita akan menggunakan data ‘tips’ dari dataset Seaborn:

tips = sns.load_dataset('tips')
tips.head()

https://blog.sanbercode.com/wp-content/uploads/2020/06/Screen-Shot-2020-06-30-at-17.05.56.png

tips['tip_prsn'] = 100 * tips['tip'] / tips['total_bill']

grid = sns.FacetGrid(tips, row="sex", col="time", margin_titles=True)
grid.map(plt.hist, "tip_prsn", bins=np.linspace(0, 40, 15));

https://blog.sanbercode.com/wp-content/uploads/2020/06/10.png

Categorical plots
Categorical plots dapat juga digunakan untuk menampilkan visualisasi semacam ini. Kita dapat melihat distribusi sebuah parameter dalam bins yang memiliki nilai dari parameter lain:

with sns.axes_style(style='ticks'):
    g = sns.catplot("day", "total_bill", "sex", data=tips, kind="box")
    g.set_axis_labels("Day", "Total Bill");

https://blog.sanbercode.com/wp-content/uploads/2020/06/11.png

Joint distributions
Seperti pair plot yang sudah kita bahas, kita dapat menggunakan sns.jointplot untuk menampilkan joint distribution antara dataset yang berbeda, seiring dengan marginal distributions-nya:

with sns.axes_style('white'):
    sns.jointplot("total_bill", "tip", data=tips, kind='hex')

https://blog.sanbercode.com/wp-content/uploads/2020/06/12.png

Joint plot juga dapat melakukan kernel density estimation dan regression secara otomatis:

sns.jointplot("total_bill", "tip", data=tips, kind='reg', stat_func=stats.pearsonr, xlim=(0,55), ylim=(0,12));

# stat_func --> deprecated
# xlim dan ylim --> ukuran grid

https://blog.sanbercode.com/wp-content/uploads/2020/06/13.png

Bar plots
Time series data dapat ditampilkan menggunakan bar plot pada sns.catplot. Kali ini kita menggunakan dataset ‘planets’ yang ada pada Seaborn:

planets = sns.load_dataset('planets')
planets.head()

https://blog.sanbercode.com/wp-content/uploads/2020/06/Screen-Shot-2020-06-30-at-20.35.43.png

with sns.axes_style('white'):
    g = sns.catplot("year", data=planets, aspect=2,
                    kind="count", color='steelblue')
    g.set_xticklabels(step=5)

https://blog.sanbercode.com/wp-content/uploads/2020/06/14.png

Altair
Altair merupakan library visualisasi statistik untuk python, berdasar dari Vega dan Vega-Lite. Altair merupakan alat visualisasi yang sangat mantap dan cukup ringkas untuk menampilkan berbagai macam grafik statistika. Kita hanya perlu menentukan hubungan antara masing-masing data, warna, ukuran, dan lainnya, sedangkan detail plotnya akan ditangani secara otomatis. Dengan Altair, kita bisa menghabiskan waktu lebih banyak untuk memahami isi data dibandingkan berpusing-pusing memikirkan coding-nya.

Dasar-dasar Altair
Charts
Altair digunakan pada DataFrames Pandas. Objek utama pada Altair adalah objek Chart yang menggunakan DataFrame sebagai input tunggal pada argumennya.

Marks
Setelah kita menentukan objek chart, selanjutnya kita harus menentukan ‘mark’-nya. Marks merupakan bagian fundamental pada Altair yang menentukan bagaimana data kita ingin di visualisasikan. Attribut mark pada objek Chart dapat menggunakan method Chart.mark_*. Beberapa jenis mark yang umum digunakan sebagai berikut:

mark_bar() : bar plot seperti histogram
mark_line() : line plot
mark_point() : scatter plot dengan titiknya dapat didesain sesuka hati
mark_boxplot() : boxplot
Encodings
Setelah kita menentukan mark-nya, kita juga perlu menentukan ‘encoding’ yang menghubungkan data visualisasinya, atau biasa kita sebut axis x dan y (terkadang juga bersamaan dengan parameter color untuk plot dengan 3 variabel).

Salah satu fitur unik dari Altair adalah, kita dapat menentukan bagaimana sebuah kolom pada DataFrame diperlakukan. Altair menentukan bahwa standar sebuah numeric data adalah ‘quantitative’, untuk data waktu adalah ‘temporal’, dan ‘nominal’ merupakan standar untuk data string. Akan tetapi, kita dapat memaksa Altair untuk memperlakukan kolom numerical sebagai ‘nominal’. Kita juga bisa menentukan di awal bahwa suatu kolom merupakan jenis ‘ordinal’ misalnya. Kita dapat memaksa Altair untuk menggunakan encoding berikut:

Quantitative (Q): nilai bilangan real
Ordinal (O): categorical ordinal
Nominal (N): categorical nominal
Temporal (T): waktu atau tanggal
Data Aggregation
Untuk kenyamanan dan fleksibilitas, Altair memiliki fungsi bawaan untuk melakukan agregasi seperti average, count, dll.

Bar Chart
Mari kita mulai dengan menginstall library Altair pada cmd atau teminal teman-teman:

pip install altair
Altair juga dapat di install bersamaan dengan dataset dari vega_dataset:

pip install altair vega_datasets
Import library yang diperlukan:

import altair as alt
import numpy as np
import pandas as pd
Kali ini kita akan menggunakan dataset diamonds.csv yang sebelumnya pernah teman-teman olah datanya menggunakan Pandas.

df_full = pd.read_csv('diamonds.csv')
Data diamonds.csv memiliki 53940 baris data, kita hanya akan mengambil sampel sebanyak 500 baris data secara acak:

# gunakan random_state yang sama agar data yang dipilih secara acak di blog ini dan yang teman-teman gunakan sama
df = df_full.sample(n=500, random_state=8) 
df.sample(n=5, random_state=8)

https://blog.sanbercode.com/wp-content/uploads/2020/07/Screen-Shot-2020-07-01-at-12.48.30.png

Kita lihat ringkasan data nya hingga 3 desimal:

df.describe().round(3)

https://blog.sanbercode.com/wp-content/uploads/2020/07/Screen-Shot-2020-07-01-at-12.57.58.png

Selanjutnya mari kita lakukan langkah berikut:

Memasukkan dataset diamond ke dalam objek Chart,
Pilih ‘bar’ untuk mark-nya, dan
Encode nilai x dan y dengan nilai ‘cut’ dan ‘count()’ ke dalam chart bar nya untuk menampilkan kolom ‘cut’.
alt.Chart(df).mark_bar().encode(x='cut', y='count()')

https://blog.sanbercode.com/wp-content/uploads/2020/07/15.png

Kita coba masukkan kolom clarity ke dalam plot di atas dengan setting color=’clarity’ agar terlihat lebih keren:

alt.Chart(df).mark_bar().encode(
    x='cut', 
    y='count()', 
    color='clarity')

https://blog.sanbercode.com/wp-content/uploads/2020/07/16.png

Lebih berwarna lah ya, sekarang kita lihat bagaimana perubahan plotnya jika kita mengubah tipe kolom ‘clarity’ menjadi ordinal. Secara default levelnya diurutkan berdasarkan alfabet, yang tentu saja urutannya belum tentu benar, sehingga pada kasus nyata, kita perlu menambahkan urutan yang benarnya.

alt.Chart(df).mark_bar().encode(
    x='cut', 
    y='count()', 
    color='clarity:O')

https://blog.sanbercode.com/wp-content/uploads/2020/07/17.png

Plot yang dihasilkan terlihat cukup kaku, mari kita coba tambahkan sedikit pada codingannya:

alt.Chart(df, 
          width=500, 
          title='Distribusi Cut'
         ).mark_bar(opacity=0.9,
                    color='blue'
          ).encode(x=alt.X('cut', 
                         title='Jenis Cut', 
                         sort=['Fair', 'Good', 'Very Good', 'Premium', 'Ideal'],
                         axis=alt.AxisConfig(labelAngle=45)),
                   y=alt.Y('count()', title='Jumlah Berdasarkan Observasi'),
                   color=alt.Color('clarity')
          )

https://blog.sanbercode.com/wp-content/uploads/2020/07/18.png

Histogram
Kita dapat menghasilkan histogram menggunakan jenis ‘bar’ pada mark-nya dengan menambahkan jumlah maksimum bin yang kita inginkan.

alt.Chart(df).mark_bar(color='green').encode(
    alt.X('carat', bin=alt.Bin(maxbins=20)), 
    y='count()')

https://blog.sanbercode.com/wp-content/uploads/2020/07/19.png

Jika kita menambahkan parameter ‘color’ nya, maka histogram yang dihasilkan seperti berikut:

alt.Chart(df).mark_bar().encode(
    alt.X('carat', bin=alt.Bin(maxbins=20)), 
    y='count()',
    color='cut')

https://blog.sanbercode.com/wp-content/uploads/2020/07/20.png

Boxplot
Boxplot dapat dibuat menggunakan mark ‘bloxplot’. Kita coba tampilkan boxplot untuk kolom ‘carat’ dengan rentang nilai full:

alt.Chart(df).mark_boxplot(extent='min-max').encode(x='carat')

https://blog.sanbercode.com/wp-content/uploads/2020/07/21.png

Sekarang kita coba gunakan nilai default 1.5 IQR(Interquartile Range) pada parameter ‘extent’-nya. Nilai outlier dapat terlihat sebagai lingkaran-lingkaran:

alt.Chart(df).mark_boxplot().encode(x='carat')

https://blog.sanbercode.com/wp-content/uploads/2020/07/22.png

Kita dapat menampilkan beberapa boxplot secara bersamaan untuk kolom categorical. Di bawah ini, kita ubah axesnya menjadi vertikal:

alt.Chart(df, width=300).mark_boxplot().encode(y='carat', x='cut')

https://blog.sanbercode.com/wp-content/uploads/2020/07/23.png

Scatter Plot
Scatter plot dapat dibuat menggunakan ‘point’ pada mark-nya. Kita coba lihat scatter plot untuk kolom carat vs. price, keduanya merupakan numerical:

alt.Chart(df).mark_point().encode(x='carat', y='price')

https://blog.sanbercode.com/wp-content/uploads/2020/07/24.png

Kita dapat menambahkan satu salah satu dimensi yang ada yaitu parameter ‘color’ kita set menggunakan nilai ‘cut’:

alt.Chart(df).mark_point().encode(x='carat', y='price', color='cut')

https://blog.sanbercode.com/wp-content/uploads/2020/07/25.png

Kita dapat menampilkan plot carat vs. price secara terpisah untuk masing-masing jenis ‘cut’ nya dengan method ‘facet’:

alt.Chart(df, width=100).mark_point().encode(
    x='carat', 
    y='price'
).facet(column=alt.Column('cut', 
        sort=['Fair', 'Good', 'Very Good', 'Premium', 'Ideal']))

https://blog.sanbercode.com/wp-content/uploads/2020/07/26.png

Untuk line plot nya silahkan coba teman-teman keasikan sendiri yaa.. ^^

Berikutnya kita akan menjadikan plot yang kita buat lebih interaktif sehingga dapat menampilkan suatu nilai tertentu ketika kita menunjuk suatu titiknya, dan meng-klik titit tersebut:

selection = alt.selection_single();
alt.Chart(df).mark_point(filled=True).encode(
    alt.X('carat:Q', scale=alt.Scale(zero=False)),
    alt.Y('price:Q', scale=alt.Scale(zero=False)),
    alt.Size('depth:Q'),
    alt.Order('depth:Q', sort='descending'),
    tooltip = [alt.Tooltip('clarity:N'),
               alt.Tooltip('depth:Q'),
               alt.Tooltip('table:Q')
              ],
    color=alt.condition(selection, 'cut:N', alt.value('grey'))
).add_selection(selection)

https://blog.sanbercode.com/wp-content/uploads/2020/07/4.gif

Kita juga dapat menyeleksi sekumpulan data tertentu kemudian menampilkan barplotnya seperti berikut:

brush = alt.selection_interval()

points = alt.Chart(df).mark_point().encode(
    x='carat:Q',
    y='price:Q',
    color=alt.condition(brush, 'cut:N', alt.value('lightgray'))
).add_selection(
    brush
)

bars = alt.Chart(df).mark_bar().encode(
    y='cut:N',
    color='cut:N',
    x='count(cut):Q'
).transform_filter(
    brush
)

points & bars

https://blog.sanbercode.com/wp-content/uploads/2020/07/3.gif

Tool Visualisasi Lainnya
Bokeh merupakan library visualisasi JavaScript dengan frontend Python yang dapat membuat visualisasi interaktif, juga dapat menangani streaming dataset atau dataset yang sangat besar. Python frontend menghasilkan output berupa struktur data JSON yang dapat di interpretasi menggunakan Bokeh JS engine.
Plotly, merupakan produk open source dari perusahaan Plotly. Karena produk dari startup, Plotly diurus dan dikembangkan dengan serius. Penggunaannya gratis pooll (Sangat direkomendasikan untuk dicoba).
VisPy, merupakan projek yang sedang dikembangkan secara aktif, berfokus pada visualisasi dinamis dari dataset yang sangat besar. Karena ditargetkan untuk OpenGL dan penggunaan prosessor grafik secara efisien, VisPy dapat me-render visualisasi yang cukup besar dan menakjubkan. WoW.



Referensi dan Sumber
Sumber 1 : https://www.oreilly.com/library/view/python-data-science/9781491912126/ch04.html
Sumber 2 : https://www.featureranking.com/tutorials/python-tutorials/altair/
Sumber 3 : https://towardsdatascience.com/how-to-create-interactive-and-elegant-plot-with-altair-8dd87a890f2a
Sumber 4 : https://towardsdatascience.com/python-interactive-data-visualization-with-altair-b4c4664308f8





