
![](./images/header6.png)<!-- -->

-----

Seandainya kita memiliki dataset **weights**, **prices** dan **types**
yang terikat satu sama lain, maka ketika ketika menambahkan satu data di
dataset manapun maka kita juga harus menambahkan data baru di dataset
lainnya. Untuk menghindari kerumitan menambahkan data secara manual di
tiap dataset, baiknya dataset-dataset tersebut ada dalam satu struktur
data.

Untungnya, R memiliki struktur data untuk mengakomodasi hal diatas. R
memiliki tipe data bentukan yang disebut **data frame**. Data frame
berbentuk tabular seperti tabel di database atau spreadsheet di Excel,
tentunya strukturnya berupa kolom dan baris.

## 6.1 Data Frames

Data harta karun kita bisa menjadi kandidat yang bagus untuk dijadikan
sebuah data frame. Caranya sangat mudah, teman-teman cukup melewatkan
vector **weights**, **prices** dan **types** ke dalam fungsi
**data.frame** dan simpan didalam variabel **treasure**:

``` r
weights <- c(300, 200, 100, 250, 150)
prices <- c(9000, 5000, 12000, 7500, 18000)
types <- c("gold", "silver", "gems", "gold", "gems")

treasure <- data.frame(weights, prices, types)
```

Sekarang teman-teman bisa melihat isi data.frame treasure dengan
perintah print:

``` r
print(treasure)
```

    ##   weights prices  types
    ## 1     300   9000   gold
    ## 2     200   5000 silver
    ## 3     100  12000   gems
    ## 4     250   7500   gold
    ## 5     150  18000   gems

Inventaris harta jarahan kita sudah tersusun rapih berdasarkan baris dan
kolom.

## 6.2 Data Frames Access

Cara mengakses data di data frame semudah pengaksesan di matriks.

Teman-teman bisa mendapatkan data kolom secara individual dengan
memberikan nomor indeks mereka dengan menggunakan *double brackets*.
Sekarang kita akan coba untuk mengakses kolom ke-2 (prices):

``` r
treasure[[2]]
```

    ## [1]  9000  5000 12000  7500 18000

Kita juga bisa menggunakan nama kolom untuk mengakses data dari suatu
kolom tentunya masih didalam double brackets dan menggunakan kutip
ganda. Coba teman-teman panggil data kolom **“weights”**.

``` r
treasure[["weights"]]
```

    ## [1] 300 200 100 250 150

Mengetik semua tanda kurung dapat sedikit merepotkan, jadi kita bisa
menggunakan fungsi *shorthand*: Nama frame data *diikuti* tanda dolar
*diikuti* nama kolom (tanpa kutip ganda):

``` r
treasure$prices
```

    ## [1]  9000  5000 12000  7500 18000

Coba gunakan untuk mendapatkan kolom “types”;

``` r
treasure$types
```

    ## [1] gold   silver gems   gold   gems  
    ## Levels: gems gold silver

## 6.3 Loading Data Frames

Dalam prakteknya data frame akan di load dari sebuah file berupa teks
file dan R memiliki kemampuan untuk dengan mudah me-*load* data ke dalam
data frame yang berasal dari file eksternal. Gunakan fungsi
**list.files** untuk melihat teks file yang sudah disediakan:

``` r
list.files("../data-raw/")
```

    ## [1] "infantry.txt" "targets.csv"

Kita memiliki file bernama “targets.csv” yang berupa file CSV (Comma
Separated Value). Untuk me-load fie CSV kita akan menggunakan fungsi
**read.csv** dan melewatkan nama file yang akan kita load sebagai
parameter. Run perintah dibawah untuk melihat isi
    targets.csv:

``` r
read.csv("../data-raw/targets.csv")
```

    ## Warning in read.table(file = file, header = header, sep = sep, quote =
    ## quote, : incomplete final line found by readTableHeader on '../data-raw/
    ## targets.csv'

    ##          Port Population Worth
    ## 1   Cartagena      35000 10000
    ## 2 Porto Bello      49000 15000
    ## 3      Havana      14000 50000
    ## 4 Panama City     105000 35000

file “infantry.txt” mempunyai format yang serupa, tapi fieldnya
dipisahkan oleh tab bukan dengan koma. Kita bisa menggunakan fungsi
**read.table** dengan parameter nama file dan karakter yang menjadi
*separator-nya* (diisi di parameter **“sep”**) dan karena kita memiliki
file dengan separator tab maka parameter tab diisi dengan **"**:

``` r
read.table("../data-raw/infantry.txt", sep = "\t")
```

    ##            V1       V2
    ## 1        Port Infantry
    ## 2 Porto Bello      700
    ## 3   Cartagena      500
    ## 4 Panama City     1500
    ## 5      Havana     2000

Perhatikan nama kolom dari data diatas, disana tertulis “V1” dan “V2”,
itu karena baris ke-1 secara otomatis dianggap sebagai data. Untuk
menjadikan kolom ke-1 diperlakukan sebagai header (jika memang header),
tambahkan parameter header dan diisi TRUE:

``` r
read.table("../data-raw/infantry.txt", sep = "\t", header = TRUE)
```

    ##          Port Infantry
    ## 1 Porto Bello      700
    ## 2   Cartagena      500
    ## 3 Panama City     1500
    ## 4      Havana     2000

## 6.4 Merging Data Frames

Kami ingin menjarah kota dengan harta paling banyak dan penjaga paling
sedikit. Saat ini, kita harus melihat kedua file dan mencocokkan baris.
Akan lebih baik jika data untuk kota pelabuhan dan kekuatan militernya
berada dalam satu dataset.

Itu bisa dilakukan dengan fungsi **merge**, dimana kita akan dapat
menggabungkan dua data frame menjadi satu. Pertama-tama hasil pembacaan
dua file diatas akan kita tampung dalam dua variabel, variabel
**targets** dan **infantry**.

Fungsi merge membutuhkan dua parameter, data frame x (targets) dan data
frame y
    (infantry):

``` r
targets <- read.csv("../data-raw/targets.csv")
```

    ## Warning in read.table(file = file, header = header, sep = sep, quote =
    ## quote, : incomplete final line found by readTableHeader on '../data-raw/
    ## targets.csv'

``` r
infantry <- read.table("../data-raw/infantry.txt", sep = "\t", header = TRUE)

merge(x = targets, y = infantry)
```

    ##          Port Population Worth Infantry
    ## 1   Cartagena      35000 10000      500
    ## 2      Havana      14000 50000     2000
    ## 3 Panama City     105000 35000     1500
    ## 4 Porto Bello      49000 15000      700
