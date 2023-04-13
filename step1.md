#### Apa Itu Docker Volume

Secara sederhana, Docker Volume adalah cara untuk menyimpan data pada container yang dapat diakses dari luar container. Dengan Volume, kita dapat mempertahankan data yang disimpan dalam container meskipun container dihapus atau diubah.

Volume dapat dianalogikan seperti sebuah kotak penyimpanan pribadi yang dapat diakses oleh sebuah rumah (container). Di dalam rumah, kita melakukan berbagai kegiatan dan menghasilkan banyak barang seperti pakaian, buku, dan mainan. Namun, jika semua barang tersebut disimpan di dalam rumah, rumah akan menjadi penuh dan tidak teratur.

Oleh karena itu, kita dapat menyimpan barang-barang tersebut di dalam kotak penyimpanan yang terpisah dari rumah. Kotak penyimpanan ini dapat diakses dengan mudah oleh rumah, dan kita dapat menyimpan dan mengambil barang-barang yang kita butuhkan kapan saja. Dengan begitu, rumah tetap rapi dan teratur, dan barang-barang kita tetap aman dan terjaga.

Dalam hal ini, Volume berfungsi sebagai kotak penyimpanan yang terpisah dari container. Data yang dihasilkan oleh aplikasi kita disimpan di dalam kotak penyimpanan ini, sehingga tetap aman dan terjaga meskipun container dihapus atau dibuat ulang. Container dapat mengakses kotak penyimpanan dengan mudah, sehingga kita dapat menggunakan data yang kita butuhkan kapan saja.

#### Membuat Volume

Sekarang, kita akan membuat Volume. Ketik perintah berikut di terminal:

```{.bash .copy}
docker volume create myvolume
```

Ini akan membuat sebuah Volume baru bernama "myvolume".

Selanjutnya, kita akan membuat container dan mengaitkannya dengan Volume yang telah kita buat sebelumnya. Ketik perintah berikut di terminal:

```{.bash .copy}
docker run --name mycontainer -v myvolume:/app -d ubuntu sleep 1h
```

Perintah ini akan membuat container baru dengan nama "mycontainer", mengaitkannya dengan Volume "myvolume", dan menjalankan sistem operasi Ubuntu di dalam container.

Sekarang, kita akan masuk ke dalam container dan membuat file di dalamnya. Ketik perintah berikut di terminal:

```{.bash .copy}
docker exec -it mycontainer /bin/bash
```

```{.bash .copy}
echo "Hello from Docker Volume" > /app/hello.txt
```

Perintah ini akan masuk ke dalam container "mycontainer", membuka shell di dalamnya, dan membuat file "hello.txt" di dalam direktori "/app" dengan pesan "Hello from Docker Volume".

Sekarang, kita akan keluar dari container dan menghapusnya. Ketik perintah berikut di terminal:

```{.bash .copy}
exit
```

```{.bash .copy}
docker rm -f mycontainer
```

Perintah ini akan keluar dari container "mycontainer" dan menghapusnya dari sistem.

Selanjutnya, kita akan membuat container baru dan mengaitkannya kembali dengan Volume "myvolume". Ketik perintah berikut di terminal:

```{.bash .copy}
docker run --name mycontainer2 -v myvolume:/app -d ubuntu sleep 1h
```

Perintah ini akan membuat container baru dengan nama "mycontainer2", mengaitkannya dengan Volume "myvolume", dan menjalankan sistem operasi Ubuntu di dalam container.

Terakhir, kita akan memeriksa apakah file "hello.txt" masih ada di dalam container. Ketik perintah berikut di terminal:

```{.bash .copy}
docker exec -it mycontainer2 /bin/bash
```

```{.bash .copy}
cat /app/hello.txt
```

Perintah ini akan masuk ke dalam container "mycontainer2", membuka shell di dalamnya, dan menampilkan isi file "hello.txt". Jika semuanya berjalan dengan baik, kita akan melihat pesan `Hello from Docker Volume` yang telah kita buat sebelumnya.

Selanjutnya keluar dari container menggunakan perintah berikut

```{.bash .copy}
exit
```

Sekarang, kita telah berhasil membuat dan menggunakan Docker Volume!. Pada halaman selanjutnya kita akan mencoba versi lain dari volume yaitu mounting directori host ke dalam container
