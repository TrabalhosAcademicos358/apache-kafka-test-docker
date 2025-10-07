
## 🧱 Apache Kafka (KRaft Mode) — Docker Compose Setup

### 📘 Descrição

Este ambiente configura o **Apache Kafka** em modo **KRaft** (sem Zookeeper) utilizando  **Docker Compose** .

Ideal para desenvolvimento local, testes e aprendizado sobre o Kafka moderno.

---

### ⚙️ Estrutura do Projeto

<preclass="overflow-visible!"data-start="480"data-end="526"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre!">`<span><span>`.

├── docker-compose.yml

└── README.md

`</code></div>``</div></pre>`

---

### 🐋 1. Subir o Kafka

Execute no terminal:

<preclass="overflow-visible!"data-start="580"data-end="612"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`docker compose up -d

`</code></div>``</div></pre>`

Isso irá iniciar um único container Kafka acessível em `localhost:9092`.

Verifique se o serviço está rodando:

<preclass="overflow-visible!"data-start="726"data-end="747"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`docker ps

`</code></div>``</div></pre>`

Saída esperada:

<preclass="overflow-visible!"data-start="765"data-end="906"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre!">`<span><span>`CONTAINER ID   IMAGE                PORTS                    NAMES

abc123456789   apache/kafka:latest  0.0.0.0:9092->9092/tcp   kafka

`</code></div>``</div></pre>`

---

### 📦 2. Acessar o container Kafka

<preclass="overflow-visible!"data-start="950"data-end="988"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`docker `<span>`exec`<span>` -it kafka bash

`</code></div>``</div></pre>`

Os scripts do Kafka estão em:

<preclass="overflow-visible!"data-start="1020"data-end="1042"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre!">`<span><span>`/opt/kafka/bin

`</code></div>``</div></pre>`

---

### 🧩 3. Criar um tópico

<preclass="overflow-visible!"data-start="1076"data-end="1188"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`/opt/kafka/bin/kafka-topics.sh --create \

  --topic meu-topico \

  --bootstrap-server localhost:9092

`</code></div>``</div></pre>`

Listar tópicos existentes:

<preclass="overflow-visible!"data-start="1218"data-end="1301"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`/opt/kafka/bin/kafka-topics.sh --list --bootstrap-server localhost:9092

`</code></div>``</div></pre>`

---

### 📨 4. Enviar mensagens (Producer)

<preclass="overflow-visible!"data-start="1347"data-end="1460"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`/opt/kafka/bin/kafka-console-producer.sh \

  --topic meu-topico \

  --bootstrap-server localhost:9092

`</code></div>``</div></pre>`

Digite mensagens e pressione **Enter** para enviar:

<preclass="overflow-visible!"data-start="1514"data-end="1547"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre!">`<span><span>`> mensagem 1`<span>`

`<span>`> mensagem 2`<span>`

`</code></div>``</div></pre>`

---

### 👂 5. Ler mensagens (Consumer)

Em outro terminal:

<preclass="overflow-visible!"data-start="1610"data-end="1648"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`docker `<span>`exec`<span>` -it kafka bash

`</code></div>``</div></pre>`

Depois:

<preclass="overflow-visible!"data-start="1658"data-end="1792"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`/opt/kafka/bin/kafka-console-consumer.sh \

  --topic meu-topico \

  --from-beginning \

  --bootstrap-server localhost:9092

`</code></div>``</div></pre>`

As mensagens enviadas aparecerão em tempo real.

---

### 🧹 6. Parar o ambiente

<preclass="overflow-visible!"data-start="1876"data-end="1907"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`docker compose down

`</code></div>``</div></pre>`

Para também remover volumes e dados persistidos:

<preclass="overflow-visible!"data-start="1959"data-end="1993"><divclass="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><divclass="sticky top-9"><divclass="absolute end-0 bottom-0 flex h-9 items-center pe-2"><divclass="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">`</div></div>``</div>`<divclass="overflow-y-auto p-4"dir="ltr"><codeclass="whitespace-pre! language-bash">`<span><span>`docker compose down -v

`</code></div>``</div></pre>`

---

### 📚 Referências

* [Apache Kafka Official Docs]()
* [Kafka KRaft Mode Overview]()
* [Apache Kafka Docker Image]()
