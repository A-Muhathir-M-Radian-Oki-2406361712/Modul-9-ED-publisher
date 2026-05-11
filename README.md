# Conceptual Review

## Berapa banyak publisher mengirim data ke broker tiap run?
5

## Apa arti “amqp://guest:guest@localhost:5672” yang sama seperti subscriber?
Artinya publisher dan subscriber adalah user yang sama karena username-password yang sama, lalu mereka juga terhubung ke address-port yang sama juga (rabbitmq)

# Screenshot Attachment
![RabbitMQ first run](img/rabbitmq_firstrun.png)
Gambar: RabbitMQ di lokal

![Publishing user creation](img/cli_publish.png)
Gambar: Subscriber-Docker-Publisher

![Another publishing](img/rabbitmq_republish.png)
Gambar: Laporan publish dua kali

![Another publishing](img/rabbitmq_slowsubscriber.png)
Gambar: Setelah implementasi threads-sleep

![Another publishing](img/cli_run3subscriber.png)
Gambar: Simulasi running tiga subscriber

![Another publishing](img/rabbitmq_monitor3subscriber.png)
Gambar: Laporan simulasi tiga subscriber

## Refleksi - 1 
Merujuk ke gambar ke-2, melalui RabbitMQ, subscriber menerima event user_creation dari publisher.

## Refleksi - 2
Merujuk ke gambar ke-3, spike ada dua karena publish dilakukan sebanyak dua kali, grafik memperlihatkan event publishing selama 10 menit terakhir.

## Refleksi - 3
Merujuk ke gambar ke-4, sudah diterapkan thread-sleep. Queued message menunjukkan ke angka 1.0 berarti hanya ada satu message yang mengantre (tertunda) di RabbitMQ.

## Refleksi - 4
Merujuk ke gambar ke-5 dan 6, ketika thread sleep ditambahkan dan simulasi tiga subscriber dijalankan bersamaan pada queue yang sama, event dari publisher akan terbagi secara bergantian kepada ketiga subscriber tersebut. Hal ini terjadi karena RabbitMQ secara default menerapkan metode Round-Robin Dispatching (pola Work Queues / Competing Consumers) untuk mendistribusikan beban kerja secara merata. Thread sleep berfungsi untuk mensimulasikan processing time yang memakan waktu, sehingga kita bisa melihat secara langsung bagaimana sistem melakukan load balancing antar subscriber.