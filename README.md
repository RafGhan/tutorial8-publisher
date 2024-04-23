# TUTORIAL 8 ADPRO
#### Rafi Ghani Harditama (2206081364)
#### ADPRO A / VRO

---

## REFLECTION 

1. How many data your publlsher program will send to the message broker in one run?

Program publisher mempunyai lima pesan yang dikirim ke message broker dalam sekali dijalankan. Ini ditandai oleh pemanggilan `publish_event` yang mengirim pesan berupa `UserCreatedEventMessage` di dalam fungsi `main`. Isi dari pesan-pesan tersebut berupa `user_id` dan `user_name` yang berbeda tiap pemanggilan, diantaranya adalah:

* user_id: "1", user_name: "2206081364-Amir"
* user_id: "2", user_name: "2206081364-Budi"
* user_id: "3", user_name: "2206081364-Cica"
* user_id: "4", user_name: "2206081364-Dira"
* user_id: "5", user_name: "2206081364-Emir"

2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

URL `amqp://guest:guest@localhost:5672` digunakan dalam kedua program subscriber dan publisher untuk memastikan bahwa keduanya terhubung dan berkomunikasi melalui RabbitMQ, yang bertindak sebagai message broker yang sama. URL tersebut adalah cara untuk menentukan kredensial(username dan password) untuk menghubungkan ke server AMQP yang berjalan di local pada port 5672.

* `guest:guest`: bagian ini merepresentasikan kredensial(`guest` pertama merujuk ke username dan `guest`merujuk ke password) yang digunakan untuk autentikasi.
* `@localhost:5672`: merujuk pada alamat hostname dan port number dari server dimana merupakan tempat broker AMQP berjalan. `localhost` mengacu pada mesin lokal dan `5672` adalah nomor port default untuk komunikasi AMQP. 


# Running RabbitMQ as message broker.
![alt text](./img/image.png)

# Sending and processing event.
Screenshot terminal ketika berhasil menerima 5 event message broker dari publisher.
![alt text](./img/image1.png)

Setelah menjalankan perintah cargo run pada subscriber dan publisher, data yang telah disiapkan oleh publisher akan diposting ke dalam antrian pesan yang ada. Setelah itu, subscriber akan mengambil data dari antrian pesan tersebut dan menampilkan informasinya di console atau terminal sesuai dengan pesan yang telah dikirimkan oleh publisher.

# Monitoring chart based on publisher.
Screenshot grafik RabbitMQ yang menunjukkan adanya spike pada message rates
![alt text](./img/image2.png)

Spike dalam message rates yang terlihat pada grafik disebabkan oleh eksekusi berulang dari perintah cargo run pada publisher, mengakibatkan pengiriman pesan setiap kali perintah tersebut dijalankan.