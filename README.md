# kafka-mongodb-node.js-case


event-driven-app/
│
├── producer/                  # Producer uygulaması
│   ├── Dockerfile             # Producer uygulamasını containerize etmek için gerekli yapılandırma
│   ├── index.js               # Kafka'ya belirli bir formatta event gönderen ana Node.js dosyası
│   └── .env                   # Kafka bağlantı bilgilerini içeren ortam değişkenleri
│
├── consumer/                  # Consumer uygulaması
│   ├── Dockerfile             # Consumer uygulamasını containerize etmek için gerekli yapılandırma
│   ├── index.js               # Kafka'dan veri tüketip MongoDB'ye kaydeden ana Node.js dosyası
│   └── .env                   # Kafka ve MongoDB bağlantı bilgilerini içeren ortam değişkenleri
│
├── api/                       # REST API uygulaması
│   ├── Dockerfile             # API uygulamasını containerize etmek için gerekli yapılandırma
│   ├── index.js               # MongoDB'den veri alıp filtreleme ve listeleme yapan ana Node.js dosyası
│   └── .env                   # MongoDB bağlantı bilgilerini içeren ortam değişkenleri
│
├── docker-compose.yml         # Yerel geliştirme ortamı için tüm uygulamaların Docker'da çalıştırılmasını sağlayan yapılandırma dosyası
│
├── k8s-manifests/             # Kubernetes YAML manifest dosyaları
│   ├── producer-deployment.yaml  # Producer uygulamasının Kubernetes deployment ve service tanımı
│   ├── consumer-deployment.yaml  # Consumer uygulamasının Kubernetes deployment ve service tanımı
│   ├── api-deployment.yaml       # API uygulamasının Kubernetes deployment ve service tanımı
│   ├── kafka.yaml                # Kafka cluster için Bitnami manifest dosyası
│   └── mongodb.yaml              # MongoDB için Bitnami manifest dosyası
│
└── helm/                       # Helm Chart dosyaları
    ├── Chart.yaml             # Helm Chart meta bilgileri
    ├── values.yaml            # Helm değer dosyası
    └── templates/             # Helm template dosyaları
        ├── producer-deployment.yaml  # Producer deployment tanımı
        ├── consumer-deployment.yaml  # Consumer deployment tanımı
        ├── api-deployment.yaml       # API deployment tanımı
        ├── kafka.yaml                # Kafka tanımı
        └── mongodb.yaml              # MongoDB tanımı



# Event-Driven Application

This repository contains an **Event-Driven Application** built to demonstrate the integration of **Kubernetes**, **Kafka**, **MongoDB**, and **Node.js**. The application includes a **Producer**, a **Consumer**, and a **REST API** service. It also contains Kubernetes manifests and Helm charts for deployment in a Kubernetes cluster.

---

## **Project Overview**

The project is designed to process and expose event data using an event-driven architecture. The key components of the system are:

1. **Producer**: Publishes random event payloads to a Kafka topic every 3 seconds.
2. **Consumer**: Consumes messages from the Kafka topic and stores them in MongoDB.
3. **REST API**: Exposes an endpoint to query stored events with filtering and pagination support.

---

## **Technologies Used**

- **Node.js**: For implementing the producer, consumer, and REST API services.
- **Kafka**: For messaging and event streaming.
- **MongoDB**: For persistent storage of consumed events.
- **Docker**: To containerize the applications.
- **Kubernetes**: For deployment and orchestration.
- **Helm**: To manage Kubernetes deployments using custom Helm charts.
- **Terraform**: To provision the Kubernetes cluster.

---

## **Project Structure**

