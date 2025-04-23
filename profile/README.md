

# 🚀 Modelify-T

**Modelify-T** é uma plataforma SaaS baseada em LLM (Large Language Models) para criação e venda de templates web. Utilizamos uma arquitetura de **microserviços desacoplados** com base na **Arquitetura Hexagonal**, priorizando escalabilidade, segurança e organização.

---
```markdown
## 🧠 Visão Geral

- Criação de templates via LLM
- Pré-visualização dos templates
- Catálogo de templates personalizáveis
- Integração com sistemas de pagamento
- Orquestração de lógica entre os microserviços
- Frontend moderno e desacoplado
- APIs independentes por domínio

---

## 🧱 Arquitetura de Microserviços

Utilizamos **Arquitetura Hexagonal (Ports and Adapters)** em cada microserviço. Isso significa que:

- A lógica de negócio está no centro (domínio)
- Interfaces externas (REST, DB, eventos) ficam nas "bordas"
- Separação clara entre camadas: Domínio, Aplicação, Infraestrutura e Interfaces

**Recomendado para estudo:**  
[Hexagonal Architecture by Alistair Cockburn (oficial)](https://alistair.cockburn.us/hexagonal-architecture/)

---

## 📦 Estrutura de Pastas


```
```bash

app/
 ├── autenticacao/
 │ ├── servico-de-autenticacao # Domínio + regras + adapters
 │ └── api-de-autenticacao # Interface REST
 ├── catalogo/
 │ ├── servico-de-catalogo
 │ └── api-de-catalogo
 ├── pagamentos/
 │ ├── servico-de-pagamentos
 │ └── api-de-pagamentos
 ├── preview/
 │ ├── servico-de-preview
 │ └── api-de-preview
 ├── template/
 │ ├── servico-de-template
 │ └── api-de-template
 ├── orquestrador/
 │ ├── servico-de-orquestracao
 │ └── api-de-orquestracao
 ├── front/
 │ ├── inicio
 │ ├── pagina-de-preview
 │ ├── pagina-de-pagamento
 │ └── sobrenos

```

---

## 🔌 Serviços e APIs

| Serviço         | Responsabilidade                                         |
|----------------|----------------------------------------------------------|
| Autenticação    | Login, tokens, autorização                               |
| Catálogo        | Templates listados e filtros                            |
| Preview         | Geração visual de previews                              |
| Pagamentos      | Integração com gateways de pagamento                    |
| Template        | Criação e entrega do produto final                      |
| Orquestrador    | Coordenação dos microserviços e fluxo de geração       |

---

## 🔁 Comunicação entre Serviços

- Cada serviço tem sua **API REST** própria
- A comunicação entre serviços é feita via **mensageria assíncrona** (ex: RabbitMQ, Kafka)
- O `orquestrador` centraliza os fluxos de negócio entre serviços

---

## 🧪 Testes

Cada serviço possui sua suíte de testes automatizados:

```bash
# Exemplo de execução
cd app/template/servico-de-template
pytest

```

----------

## ⚙️ Ambiente Local

### Requisitos

-   Docker + Docker Compose
    
-   Python 3.10+
    
-   Node.js (Frontend)
    

### Subindo o ambiente

```bash
git clone https://github.com/modelify-t/infra.git
cd infra
cp .env.example .env
docker-compose up --build

```

----------

## 🌱 GitFlow (Workflow de Branches)

> Baseado no [modelo de GitFlow por Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/)

### Branches principais

-   `main`: código em produção (estável)
    
-   `develop`: branch de desenvolvimento (últimas features integradas)
    

### Branches secundárias

-   `feature/*`: novas funcionalidades
    
-   `bugfix/*`: correções de bugs
    
-   `hotfix/*`: correções urgentes em produção
    
-   `release/*`: preparação de novas versões
    

### Regras:

-   Nunca faça commits direto na `main`
    
-   Faça PR da `feature/` para `develop`
    
-   Merge de `develop` para `main` só quando tudo estiver testado
    
-   Use `rebase` para manter histórico limpo (quando possível)
    

----------

## 🧠 Boas Práticas de Código

-   Seguir padrões da arquitetura hexagonal
    
-   Escreva testes automatizados (unitários, integração, e2e se aplicável)
    
-   Documente endpoints da API com Swagger/OpenAPI
    
-   Nunca vaze secrets em commits (`.env` está no `.gitignore`)
    
-   Use nomes explícitos para arquivos, métodos e variáveis
    

----------

## 📦 CI/CD

-   **GitHub Actions** para testes automatizados e builds Docker
    
-   Deploy com Docker Swarm/Kubernetes (planejado)
    
-   Segurança com GitHub Secrets e controle de acesso aos repositórios
    

----------

## 💬 Contribuindo

1.  Faça fork do repositório
    
2.  Crie uma nova branch: `git checkout -b feature/nome-da-feature`
    
3.  Faça commits organizados
    
4.  Envie um Pull Request com descrição clara da mudança
    
5.  Aguarde revisão e integração 🎉
    

----------

## 🔐 Segurança

-   JWT assinado por microserviço
    
-   API Gateway para controle centralizado (Traefik/Nginx)
    
-   Encriptação de dados sensíveis
    
-   Controle de escopo e permissões por domínio
    

----------

## 📄 Licença

Distribuído sob a licença MIT. Consulte `LICENSE` para mais informações.

----------

## 🤝 Feito com visão por

**Modelify-T Team** — moldando o futuro da criação visual com inteligência artificial.

