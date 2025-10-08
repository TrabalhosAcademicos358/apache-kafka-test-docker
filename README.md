# 🧱 Apache Kafka (KRaft Mode) + Kafka UI --- Docker Compose Setup

## 📘 Descrição

Este ambiente sobe o **Apache Kafka (modo KRaft)** junto com o **Kafka
UI** da [Provectus](https://github.com/provectus/kafka-ui).
Com isso, você pode criar tópicos, enviar mensagens e inspecionar
consumidores direto pelo browser ou pelo terminal.

---

## ⚙️ Estrutura do Projeto

    .
    ├── docker-compose.yml
    └── README.md

---

## 🐋 1. Subir os containers

```bash
docker compose up -d
```

Verifique:

```bash
docker ps
```

Saída esperada:

    kafka-ui     0.0.0.0:8080->8080/tcp
    kafka        0.0.0.0:9092->9092/tcp

---

## 💻 2. Acessar o container Kafka por bash

Caso prefira usar os comandos do Kafka diretamente, entre no container:

```bash
docker exec -it kafka bash
```

Os binários do Kafka ficam em:

    /opt/kafka/bin

Exemplos de uso: 

* listar tópicos:

  ```shell
  /opt/kafka/bin/kafka-topics.sh --list --bootstrap-server localhost:9092
  ```
* Criar um tópico

  ```shell
  /opt/kafka/bin/kafka-topics.sh --create --topic meu-topico --bootstrap-server localhost:9092
  ```
* Usar o **Producer** (enviar mensagens)

  ```shell
  /opt/kafka/bin/kafka-console-producer.sh --topic meu-topico --bootstrap-server localhost:9092
  ```
* Usar o ***Consumer** (ler mensagem)*

  ```shell
  /opt/kafka/bin/kafka-console-consumer.sh --topic meu-topico --from-beginning --bootstrap-server localhost:9092
  ```

---

## 🌐 3. Acessar o Kafka UI

Abra no navegador:
👉 [http://localhost:8080](http://localhost:8080)

Você verá a interface **Kafka UI**, com o cluster "local" já conectado.

---

## 🧩 4. Usando a interface

- **Tópicos** → criar, listar e deletar tópicos.\
- **Mensagens** → produzir e consumir direto na UI.\
- **Consumers** → visualizar grupos de consumidores.\
- **Configurações** → editar parâmetros do cluster.

---

## 🧹 5. Parar tudo

```bash
docker compose down
```

Para também remover volumes e dados:

```bash
docker compose down -v
```

---

## 💡 Dica Extra

Se quiser testar vários clusters, basta adicionar novos blocos no
`docker-compose.yml`, por exemplo:

```yaml
KAFKA_CLUSTERS_1_NAME: staging
KAFKA_CLUSTERS_1_BOOTSTRAPSERVERS: kafka-staging:9092
```

---

## 📚 Referências

- [Apache Kafka --- Documentação
  Oficial](https://kafka.apache.org/documentation/)
- [Kafka UI --- GitHub](https://github.com/provectus/kafka-ui)
- [Kafka KRaft Mode ---
  Overview](https://kafka.apache.org/documentation/#kraft)
