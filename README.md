# Sistema de Envio de E-mails com Arquitetura Distribuída usando RabbitMQ e Docker

Este projeto demonstra, de forma prática e didática, a integração de sistemas distribuídos utilizando mensageria com RabbitMQ e containers Docker. A arquitetura proposta simula um fluxo de envio de e-mails assíncrono e desacoplado, facilitando o entendimento de conceitos de sistemas distribuídos e filas de mensagens.

---

## 📦 Arquitetura do Projeto

O sistema é composto por **três containers Docker**:

- **`broker_mensagens`**  
  Container responsável por rodar o **RabbitMQ** na porta **5672**, atuando como intermediador entre os serviços, recebendo e distribuindo mensagens por meio de filas.

- **`sistema`**  
  Serviço escrito em **PHP**, contendo um **formulário web para envio de e-mails**. Ao enviar o formulário, os dados são encapsulados e enviados como uma **mensagem para o RabbitMQ**, sendo inseridos na fila.

- **`mail_server`**  
  Serviço consumidor, também em **PHP**, que **escuta a fila no RabbitMQ**. Ao receber uma nova mensagem, o serviço processa e realiza o envio do e-mail com base nas informações recebidas.

---

## 🔁 Fluxo de Funcionamento

1. O usuário acessa o formulário disponível no container `sistema` e envia os dados do e-mail.
2. O serviço `sistema` envia uma mensagem com os dados do e-mail para o `broker_mensagens` (RabbitMQ).
3. O container `mail_server` consome essa mensagem da fila e realiza o envio do e-mail.

Este modelo simula uma **comunicação assíncrona e desacoplada**, ideal para projetos escaláveis, com alta disponibilidade e baixa dependência entre serviços.

---

## 🚀 Tecnologias Utilizadas

- Docker
- RabbitMQ
- PHP
- Composer

---

## 🧪 Objetivos Educacionais

- Demonstrar o uso de **filas de mensagens** com RabbitMQ.
- Aplicar o conceito de **sistemas distribuídos** com serviços independentes.
- Exibir a separação clara entre **produção e consumo de mensagens**.
- Mostrar como o **Docker** pode ser utilizado para orquestrar serviços isolados de forma simples e eficaz.

---

## 📷 Diagrama da Arquitetura

![Diagrama da Arquitetura](https://github.com/mateus-nunes/sd-integracao-rabbitmq/blob/main/arquitetura.png)

*Texto gerado por IA