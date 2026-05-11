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