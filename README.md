# grpc-tutorial Refleksi
1. Pada RPC:
a. Unary adalah metode pengiriman data yang dilakukan oleh  server dan client melalui request dan response dimana client akan mengirimkan suatu request kepada server dan server akan mengembalikan response yang ditunggu oleh client. Metode ini berguna untuk melakukan pertukaran data berukuran kecil di waktu yang diperlukan saja.

b. Streaming adalah metode pengiriman data dimana client atau server mengirimkan data ke yang lain melalui rantai response yang terjadi secara beruntun. Metode ini berguna ketika client atau server memerlukan data secara real-time dari yang lain dan untuk pengiriman data yang besar. 

c. Bi_directional streaming adalah metode pengiriman data dimana client dan server sama-sama melakukan streaming ke satu sama lain sehingga kedua puhak dapat melakukan pertukaran data secara real-time. Metode ini berguna untuk mendapatkan data terbatu dari masing-masing pihak dan memungkinkan komunikasi antar server dan client secara real-time.

2. Implementasi keamanan dalam penggunaan gRPC di Rust akan membutuhkan perhatian lebih banyak peratian karena server harus memastikan bahwa client yang melakukan streaming tetap terautentikasi selama streaming berjalan. Selain itu, server juga harus dipastikan hanya melakukan streaming bagian yang boleh diakses oleh pengguna. Tentu saja pengiriman data antar server dan client juga harus dipastikan terenkripsi semua karena pengiriman data terjadi secara terus menerus. 

3. Pada Bi-directional streaming, masalah yang mungkin terjadi adalah ketika koneksi antara client dan server terputus. Pada saat itu perubahan apapun yang terjadi pada server tidak akan terkirim ke klien dan juga sebaliknya. Sehingga koneksi antara client dan server harus dijaga agar pengiriman data tetap terjadi secara real time seperti server harus dipastikan tetap bisa jalan terus.

4. Keuntungan dari wrapper tersebut adalah kita mampu mengubah suatu receiver menjadi sebuah receiver yang dapat menerima data dalam bentuk stream. Namun, wrapper tersebut hanya dapat digunakan untuk receiver yang berasal dari tokio::sync::mpsc::Receiver.

5. Kita bisa mencoba mengenkapsulasi beberapa metode yang dibutuhkan oleh gRPC untuk mempersingkat kode. 

6. Pada MyPaymentService, untuk menangani pembayaran yang lebih kompleks, mungkin diperlukan untuk melakukan handling ketika jumlah pembayaran yang dilakukan tidak cukup serta diperlukan juga cara untuk mengkalkulasi jumlah yang harus dibayar.

7. gRPC cenderung lebih canggih jika dibandingkan dengan REST dimana gRPC dapat memanfaatkan HTTP/2 yang memungkinkan multiplexing request dan response. Selain itu gRPC juga memungkinkan penggunaan streaming antara client dan server yang memungkinkan pemindahan data secara real time. Namun, kemampuan gRPC terbatas karena tidak semua browser dapat menggunakan gRPC.

8. Keuntungan dari HTTP/2 adalah kemampuannya untuk melakukan multiplexing terhadap request dan response. Selain itu, HTTP/2 juga dapat melakukan header compression dimana HTTP/2 hanya akan mengirim header yang unik dari header sebelumnya sehingga meningkatkan performanya jika dibandingkan protokol lainnya.

9. Kemampuan request-response dari REST APIs cenderung kurang dalam kemampuan komunikasi real-time serta dalam responsiveness karena REST API harus melakukan suatu request untuk mendapatkan suatu response atau pembaruan dari server, sedangkan streaming tidak harus selalu mengirim request untuk mendapatkan suatu response atau pembaruan dari server.

10. Implikasi yang dimiliki dari penggunaan schema-based approach pada gRPC adalah lebih banyak pekerjaan harus dilakukan untuk megimplementasikan protocol buffer yang akan digunakan. Namun, protobuf dapat melakukan serialisasi dengan lebih efisien dan dengan ukuran yang lebih kecil sehingga meningkatkan performa jaringan yang digunakan untuk pemindahan data.