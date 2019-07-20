
![](./images/header3.png)<!-- -->

-----

Sejauh ini kita hanya bekerja dengan vector, yang merupakan tipe
bentukan sederhana untuk menampung nilai. Bagaimana jika kita memerlukan
data dalam bentuk baris dan kolom? Maka kita membutuhkan **Matrix**
untuk kebutuhan tersebut.

Matriks hanya istilah keren untuk array 2 dimensi. Dalam bagian ini,
kita akan melihat bagaimana caranya bekerja dengan matrix, dari membuat
sampai pengaksesan.

## 3.1 Matrix

Kita akan memulai dengan membuat matrix 3x4, matrix dengan 3 baris dan 4
kolom, totalnya berisi 12 elemen yang diisi nilai 0.

``` r
matrix(0, 3, 4)
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    0    0    0    0
    ## [2,]    0    0    0    0
    ## [3,]    0    0    0    0

Teman-teman juga dapat menggunakan vector untuk menginisialisasi
matriks. Untuk membuat matrix menggunakan vector kita mulai dengan
vector yang berisi sequence angka dari 1 sampai 12:

``` r
a <- 1:12
```

Jika kita mencetak nilai vector tersebut, maka akan ditampilkan dalam
satu baris:

``` r
print(a)
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10 11 12

Sekarang buat matriks dengan melewatkan vector, diikuti dengan jumlah
baris dan jumlah kolom:

``` r
matrix(a, 3, 4)
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    4    7   10
    ## [2,]    2    5    8   11
    ## [3,]    3    6    9   12

Nilai dari vector akan disalin satu per satu kedalam matrix. Teman-teman
juga bisa membentuk kembali vector itu sendiri menjadi matrix. Coba buat
vector sequence dari angka 1 sampai 8:

``` r
plank <- 1:8
```

Fungsi **dim** bisa kita gunakan untuk membentuk sebuah matrix. Fungsi
dim dapat di*assign* vector yang berisi baris dan kolom.

Assign *dimensi* baru untuk vector plank, dengan dimensi 2x4:

``` r
dim(plank) <- c(2,4)
```

Jika vector plank dicetak ke konsol, maka bentuknya akan berubah menjadi
2 baris dan 4 kolom:

``` r
print(plank)
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    3    5    7
    ## [2,]    2    4    6    8

Vector plank tidak lagi 1 dimensi, tapi sudah berubah menjadi sebuah
matrix.

Sekarang gunakan fungsi matriks untuk membuat matrix dengan dimensi 5x5,
dengan nilai elemen diisi dengan angka 1.

``` r
matrix(1, 5, 5)
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    1    1    1    1    1
    ## [2,]    1    1    1    1    1
    ## [3,]    1    1    1    1    1
    ## [4,]    1    1    1    1    1
    ## [5,]    1    1    1    1    1

## 3.2 Matrix Access

Untuk mendapatkan atau mengakses nilai matrix, tidak berbeda dengan
mengakses nilai vector, bedanya sekarang teman-teman membutuhkan 2 nilai
(baris dan kolom) untuk mendapatkan nilai yang spesifik.

``` r
print(plank)
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    3    5    7
    ## [2,]    2    4    6    8

Coba dapatkan saya nilai dari baris kedua di kolom ketiga dari matrix
plank:

``` r
plank[2, 3]
```

    ## [1] 6

Sekarang, cobalah mendapatkan nilai dari baris pertama kolom keempat:

``` r
plank[1, 4]
```

    ## [1] 7

Seperti halnya vector, untuk meng-assign sebuah nilai, kita hanya perlu
menentukan baris dan kolomnya:

``` r
plank[1, 4] <- 0
plank
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    3    5    0
    ## [2,]    2    4    6    8

Atau teman-teman bisa mendapatkan seluruh baris matriks dengan
menghilangkan indeks kolom (tapi tetap menggunakan koma). Mari kita coba
mengambil baris kedua:

``` r
plank[2, ]
```

    ## [1] 2 4 6 8

``` r
plank[2, , drop = FALSE]
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    2    4    6    8

Untuk mendapatkan seluruh kolom, hilangkan indeks baris:

``` r
plank[ , 4]
```

    ## [1] 0 8

``` r
plank[ , 4, drop = FALSE]
```

    ##      [,1]
    ## [1,]    0
    ## [2,]    8

Kita juga bisa mengakses banyak baris atau kolom dengan menggunakan
vector atau sequence. Coba akses kolom 2 hingga 4.

``` r
plank[ ,2:4]
```

    ##      [,1] [,2] [,3]
    ## [1,]    3    5    0
    ## [2,]    4    6    8
