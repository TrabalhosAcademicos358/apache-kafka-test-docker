# Kafka KRaft com Kafka UI

Este guia explica como rodar um **cluster Kafka sem Zookeeper (KRaft)** com múltiplos brokers e acessar através do **Kafka UI** usando Docker Compose.

---

## 📁 Estrutura

* `docker-compose.yml` contendo 3 brokers Kafka e Kafka UI

---

## 🐳 Rodando o cluster

1. Clone ou crie o arquivo `docker-compose.yml` com o conteúdo do exemplo.
2. Suba os containers:

```bash
docker-compose up -d
```

---

## 🔹 Endereços dos Brokers

| Broker | Porta |
| ------ | ----- |
| kafka1 | 9092  |
| kafka2 | 9094  |
| kafka3 | 9096  |

---

## 🌐 Kafka UI

* Acesse no navegador:

```
http://localhost:8080
```

* Visualize tópicos, mensagens e consumidores do cluster.

---

## 🧪 Testando os Brokers

Entre no container do Kafka:

```bash
docker exec -it kafka1 bash
```

Criar um tópico:

```bash
kafka-topics.sh --create --topic teste --partitions 3 --replication-factor 3 --bootstrap-server localhost:9092
```

Listar tópicos:

```bash
kafka-topics.sh --list --bootstrap-server localhost:9092
```

---

## 📦 Volumes

Os dados de cada broker são persistidos nos volumes:

```yaml
volumes:
  kafka1_data:
  kafka2_data:
  kafka3_data:
```

Isso garante que os dados não serão perdidos ao reiniciar os containers.
