
![](./images/header5.png)<!-- -->

-----

Seringkali kebutuhan data kita dikelompokkan berdasarkan kategori:
tekanan darah berdasarkan rentang usia, kecelakaan oleh produsen
kendaraan bermotor dan sebagainya. R memiliki tipe bentukan khusus yang
disebut **factor** untuk mengatasi nilai dengan kategori seperti ini.

## 5.1 Creating Factors

Masih sebagai kapten bajak laut, kita akan menginventaris harta jarahan
yang dimiliki. Kita akan membuat vector untuk item barang di tiap peti.

Untuk mengkategorikan item barang di tiap peti, cukup lewatkan vector ke
fungsi **factor**:

``` r
chests <- c("gold", "silver", "gems", "gold", "gems")

types <- factor(chests)
```

Ada perbedaan antara vector asli dan faktor yang baru dibuat dan perlu
diperhatikan. Silahkan cetak vector chests ke konsol:

``` r
print(chests)
```

    ## [1] "gold"   "silver" "gems"   "gold"   "gems"

Anda melihat item barang yang berulang, sekarang cetak faktor types:

``` r
print(types)
```

    ## [1] gold   silver gems   gold   gems  
    ## Levels: gems gold silver

Dicetak di bagian bawah, Anda akan melihat tingkatan faktor, kelompok
nilai yang “unik”. Perhatikan juga bahwa tidak ada tanda kutip di
sekitar nilai. Itu karena mereka bukan string biasa, mereka sebenarnya
nilai integer sebagai referensi ke salah satu tingkatan faktor.

Kita bisa melihat nilai integer dari faktor types dengan melewatkan
faktor types ke dalam fungsi **as.integer**:

``` r
as.integer(types)
```

    ## [1] 2 3 1 2 1

Kita juga bisa mendapatkan tingkatan faktor dengan fungsi **levels**:

``` r
levels(types)
```

    ## [1] "gems"   "gold"   "silver"
