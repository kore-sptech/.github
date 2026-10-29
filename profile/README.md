
# 📋 Sobre o Projeto, Arquitetura e Equipe

## 💡 Sobre o Projeto

O **Kore** é uma plataforma completa de gestão para salões e estúdios, desenvolvida como projeto acadêmico de monorepo na São Paulo Tech School. O sistema centraliza a operação de negócios de beleza e estética, reunindo autenticação, gestão de usuários, agendamentos, catálogo de produtos, controle de estoque, transações financeiras, relatórios gerenciais e notificações instantâneas.

---

## 🏛️ Visão Geral da Arquitetura

A aplicação adota uma estrutura modular e desacoplada, dividida em três frentes de software mais a camada de infraestrutura:

* **API Principal (`backend/kore`):** Desenvolvida em Java 21 e Spring Boot em arquitetura em camadas (`controller -> service -> repository -> model`). Responde pela autenticação JWT, regras de negócio e streaming de eventos via **SSE** (*Server-Sent Events*).
* **Microsserviço de Notificações (`backend/notification`):** Estrutura orientada a casos de uso acoplada via mensageria **RabbitMQ**. Processa notificações de forma assídua e idempotente utilizando padrões resilientes como *Transactional Outbox* e *Dead Letter Queue (DLQ)*.
* **Frontend (`front-end`):** SPA em React 19 estruturada sob o conceito de **Atomic Design** e separação por domínio. Consome a API via Axios, rotas protegidas e contexto global para atualizações em tempo real.
* **Infraestrutura AWS (`infra/`):** Automação completa via Terraform simulando um ambiente de produção em nuvem. Conta com uma **camada pública** (Nginx e Frontend) e uma **camada privada** isolada (Backend e RabbitMQ), onde a comunicação externa ocorre exclusivamente por **NAT Gateway**.

---

## 👥 Equipe e Colaboração

Projeto desenvolvido de forma integrada por uma equipe de estudantes do curso de **Análise e Desenvolvimento de Sistemas** da **São Paulo Tech School** *(incluindo a colaboração de Henry Franz Ramos Arcaya, Ana Mioki, Caroline Soares, Diogo Procopio, Guilherme Faria de Mira e Vitor Restini)*. A atuação conjunta uniu competências em:

* **Engenharia Full-Stack:** Construção de backends robustos em Java/Spring Boot e interfaces dinâmicas e responsivas em React.
* **Arquitetura de Sistemas:** Implementação de microsserviços, mensageria assíncrona, monorepo e padrões de projeto limpos.
* **DevOps & Cloud Computing:** Provisionamento automatizado de infraestrutura em nuvem com Terraform, redes privadas VPC, Docker e balanceamento com Nginx.
