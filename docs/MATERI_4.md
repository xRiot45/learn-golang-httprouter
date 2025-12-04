# Video 4 | Router Pattern

## Router Pattern

- Sekarang kita sudah tahu bahwa dengan menggunakan Router, kita bisa menambah params di URL
- Sekarang pertanyaannya, bagaimana pattern (pola) pembuatan parameter nya?

## Named Parameter

- Named parameter adalah pola pembuatan parameter dengan menggunakan nama
- Setiap nama parameter harus diawali dengan : (titik dua), lalu diikuti dengan nama parameter
- Contoh, jika kita memiliki pattern seperti ini :

| Pattern                     | /user/:user        |
| --------------------------- | ------------------ |
| **/user/eko**         | **match**    |
| **/user/you**         | **match**    |
| **/user/eko/profile** | **no match** |
| **/user/**            | **no match** |

## Catch All Parameter

- Selain named parameter, ada juga yang bernama catch all parameter, yaitu menangkap semua parameter
- Catch all parameter harus diawali dengan * (bintang), lalu diikuti dengan nama parameter
- Catch all parameter harus berada di posisi akhir URL

| **Pattern**              | **/src/*filepath** |
| ------------------------------ | ---------------------- |
| **/src/**                | **no match**     |
| **/src/somefile**        | **match**        |
| **/src/subdir/somefile** | **match**        |
