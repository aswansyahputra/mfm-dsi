
![](../images/header.png)<!-- -->

-----

Dalam bab pertama ini, kita akan membahas ekspresi R dasar. Kita akan
mulai dengan yang sederhana, dengan angka, string, dan TRUE / FALSE
Kemudian kita akan menunjukkan cara menyimpan nilai dalam variabel dan
cara melewatkannya ke dalam sebuah fungsi. Kemudian akan ditunjukan
kepada teman-teman bagaimana mendapatkan bantuan pada fungsi ketika
teman-teman kesulitan dalam menggunakan sebuah fungsi.

## 1.1 Expression

Ketik apa pun pada prompt dan R akan mengevaluasinya dan mencetak
jawabannya. Mari kita coba matematika sederhana. Jalankan perintah di
bawah ini.

``` r
1 + 1
```

    ## [1] 2

Dan akan menampilkan nilai 2 di konsol. Ini dicetak di konsol tepat
setelah entri yang teman-teman tulis. Ketik string “I am Data
RockStar\!”. (Jangan lupa menggunakan kutip\!)

``` r
"I am Data RockStar!"
```

    ## [1] "I am Data RockStar!"

Sekarang coba perkalian 6 kali 7 (\* adalah operator perkalian)

``` r
2 * 3
```

    ## [1] 6

-----

> \#\#\#Jump \#1\#\#\#

  - Type 2^5 in the editor to calculate 2 to the power 5.

<!-- end list -->

``` r
2^5
```

    ## [1] 32

  - Type 28 %% 6 to calculate 28 modulo 6.

<!-- end list -->

``` r
28 %% 6 
```

    ## [1] 4

-----

## 1.2 Logical Value

Beberapa ekspresi mengembalikan nilai logika berupa TRUE atau FALSE.
(banyak bahasa pemrograman menyebut ini sebagai nilai “boolean”.) Mari
kita coba mengetik ekspresi yang memberi kita nilai logika:

``` r
3 < 4
```

    ## [1] TRUE

Dan nilai logis lainnya (perhatikan bahwa teman-teman memerlukan dua
sama dengan untuk memeriksa apakah dua nilai sama):

``` r
2 + 2 == 5
```

    ## [1] FALSE

T dan F adalah singkatan untuk TRUE dan FALSE. Silahkan coba ini :

``` r
T == TRUE
```

    ## [1] TRUE

## 1.3 Variable

Seperti dalam bahasa pemrograman lainnya, teman-teman dapat menyimpan
nilai ke dalam variabel untuk mengaksesnya nanti. Ketik x \<- 42 untuk
menyimpan nilai dalam x.

``` r
x <- 42
```

Variabel x sekarang dapat digunakan dalam ekspresi sebagai pengganti
nilai asli. Cobalah membagi x dengan 2 (/ adalah operator pembagian)

``` r
x / 2
```

    ## [1] 21

Teman-teman dapat menetapkan kembali nilai apa pun ke variabel kapan
saja. Coba tetapkan “Trust me, I am a Data RockStar” ke x.

``` r
x <- "Trust me, I am a Data RockStar"
```

Teman-teman dapat mencetak nilai variabel setiap saat hanya dengan
mengetikkan nama variabel di konsol. Silahkan cetak nilai saat ini x.

``` r
x
```

    ## [1] "Trust me, I am a Data RockStar"

Sekarang coba tetapkan nilai logika TRUE ke x.

``` r
x <- TRUE
```

-----

> \#\#\#Jump \#2\#\#\#

  - Assign the value 5 to my\_apples.
  - Assign to my\_oranges the value 6.
  - Assign the result of adding my\_apples and my\_oranges to a new
    variable my\_fruit and have R simply print the result

<!-- end list -->

``` r
my_apples <- 5
my_oranges <- 6
my_fruit <- my_apples + my_oranges
my_fruit
```

    ## [1] 11

-----

## 1.4 Function

Kita dapat memanggil fungsi dengan mengetikkan namanya, diikuti oleh
satu atau lebih argumen ke fungsi itu dalam kurung. Mari kita coba
menggunakan fungsi penjumlahan, untuk menambahkan beberapa angka.
Masukkan:

``` r
sum(1,3,5)
```

    ## [1] 9

Beberapa argumen memiliki nama. Misalnya, untuk mengulang nilai 3 kali,
teman-teman akan memanggil fungsi rep dan memberikan argumen berapa kali
akan diulang:

``` r
rep("Data RockStar!", times = 3)
```

    ## [1] "Data RockStar!" "Data RockStar!" "Data RockStar!"

Coba panggil fungsi sqrt untuk mendapatkan akar kuadrat dari 16.

``` r
sqrt(16)
```

    ## [1] 4

## 1.5 Help

**help(function\_name)** memunculkan bantuan untuk fungsi yang
diberikan. Coba tampilkan help untuk fungsi penjumlahan:

``` r
help(sum)
```

(Jangan khawatir tentang argumen na.rm opsional, kita akan membahas itu
nanti.)

Sekarang cobalah membawa bantuan untuk fungsi rep:

``` r
?rep
```

**example(function\_name)** menampilkan contoh penggunaan untuk fungsi
yang diberikan. Coba Menampilkan contoh untuk fungsi mean:

``` r
example(mean)
```

    ## 
    ## mean> x <- c(0:10, 50)
    ## 
    ## mean> xm <- mean(x)
    ## 
    ## mean> c(xm, mean(x, trim = 0.10))
    ## [1] 8.75 5.50
