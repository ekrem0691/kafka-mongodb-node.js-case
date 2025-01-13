# 📦 Kafka-MongoDB-Node.js Case Study

Bu proje, event-driven bir mimariyi uygulamak için tasarlanmıştır. Projede **Node.js**, **Apache Kafka**, **MongoDB**, **Docker**, ve **Kubernetes** teknolojileri bir arada kullanılmıştır. Her bir bileşen, uygulamanın belirli bir işlevini yerine getirmek üzere geliştirilmiş ve dağıtılmıştır.

---

## 🔍 Neler Yapıldı?

### 1. **Producer Uygulaması**
- **Görev:** Her 3 saniyede bir rastgele bir event oluşturur ve Kafka'ya gönderir.
- **Dosyalar:**
  - `producer/index.js`: Rastgele UUID, event türü ve timestamp ile event oluşturur.
  - `producer/Dockerfile`: Producer uygulamasını containerize etmek için gerekli yapılandırma.
  - `producer/package.json`: Gerekli bağımlılıkların listesi.
- **Özellikler:**
  - Kafka bağlantı bilgileri `.env` veya environment variables üzerinden alınır.
  - Mesajlar `kafkajs` kütüphanesi ile Kafka'ya gönderilir.

---

### 2. **Consumer Uygulaması**
- **Görev:** Kafka'dan event tüketir ve MongoDB'ye kaydeder.
- **Dosyalar:**
  - `consumer/index.js`: Kafka'dan mesajları dinler ve MongoDB'ye yazar.
  - `consumer/Dockerfile`: Consumer uygulamasını containerize etmek için gerekli yapılandırma.
  - `consumer/package.json`: Gerekli bağımlılıkların listesi.
- **Özellikler:**
  - Kafka ve MongoDB bağlantı bilgileri `.env` veya environment variables üzerinden alınır.
  - MongoDB için `mongoose` kütüphanesi kullanılır.

---

### 3. **API Uygulaması**
- **Görev:** MongoDB'deki event'leri sorgulamak için REST API sağlar.
- **Dosyalar:**
  - `api/index.js`: API endpoint'lerini tanımlar.
  - `api/Dockerfile`: API uygulamasını containerize etmek için gerekli yapılandırma.
  - `api/package.json`: Gerekli bağımlılıkların listesi.
- **Özellikler:**
  - `/events` endpoint'i ile:
    - `eventType` filtresi.
    - Belirli bir timestamp aralığında sorgulama.
    - Sayfalama (Pagination) desteği.
  - İsteklerin header bilgileri loglanır.

---

### 4. **Docker Compose ile Geliştirme Ortamı**
- **Görev:** Yerel geliştirme için tüm servisleri bir arada çalıştırmak.
- **Dosya:** `docker-compose.yml`
- **Özellikler:**
  - Kafka, MongoDB, Producer, Consumer ve API uygulamalarını bir arada çalıştırır.
  - Yerel ortamda hızlı kurulum sağlar.

---

### 5. **Kubernetes ve Helm ile Dağıtım**
- **Görev:** Tüm uygulamaları Kubernetes ortamında çalıştırmak için Helm kullanımı.
- **Dosyalar:**
  - `kafka/templates/`: Kubernetes manifest dosyalarını içerir.
  - `kafka/Chart.yaml`: Helm Chart meta bilgileri.
  - `kafka/values.yaml`: Varsayılan değerler.
- **Özellikler:**
  - Bitnami'nin Kafka ve MongoDB Helm Chart'ları kullanılarak hızlı kurulum sağlanmıştır.
  - API, Consumer ve Producer için custom Helm Chart oluşturulmuştur.

---

### 6. **Event-Driven Mimari**
- Kafka **Producer-Consumer modeli** ile veri işleme akışı:
  1. **Producer:** Rastgele event'ler üretir ve Kafka'ya gönderir.
  2. **Consumer:** Kafka'dan event'leri alır ve MongoDB'ye kaydeder.
  3. **API:** MongoDB'deki verileri sorgular ve dışarıya REST API olarak sunar.

---

## 📂 Proje Dosya Yapısı

