# Nexus Support - Configurations

![Java](https://img.shields.io/badge/Java-24-blue?logo=java&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.3-green?logo=springboot&logoColor=white)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-2025.0.0-blueviolet?logo=spring&logoColor=white)
![Config Server](https://img.shields.io/badge/Spring_Config_Server-Config_Files-orange?logo=spring&logoColor=white)
![Microservices](https://img.shields.io/badge/Architecture-Microservices-lightgrey)

---

## 📚 Visão Geral

Este repositório armazena os arquivos de configuração **centralizados** utilizados pelo [Spring Cloud Config Server](https://github.com/franklinclf/nexus-spring-cloud-config) do ecossistema **Nexus Support**. Ele permite que todos os microsserviços acessem suas configurações externas de forma versionada, segura e unificada, via Git.

## ⚙️ Funcionamento

O **Spring Cloud Config Server** busca as configurações deste repositório e as expõe via endpoints HTTP para os demais serviços. Isso facilita a **manutenção**, **alterações em tempo de execução** (com Actuator + Bus, se habilitado) e o **versionamento via Git**.

Cada microsserviço do Nexus Support busca suas configurações com base no seu `application.name` e no perfil ativo (ex: `dev`, `prod`), utilizando o padrão de nome:

```
{application}-{profile}.yml
```

Por exemplo, ao iniciar com:

```yaml
spring:
  application:
    name: AI
  profiles:
    active: dev
```

O Config Server buscará automaticamente o arquivo:

```
AI/dev/ai-dev.yml
```


## 📁 Estrutura de Pastas

```bash
.
├── AI/
│   └── dev/
│       └── ai-dev.yml
├── Eureka/
│   └── dev/
│       └── eureka-dev.yml
├── Gateway/
│   └── dev/
│       └── gateway-dev.yml
├── Nexus/
│   └── dev/
│       └── nexus-dev.yml
```

> 🗂️ Cada subdiretório corresponde a um serviço, e os perfis (`dev`, `prod`, etc.) são organizados dentro deles.


## ✅ Benefícios da Configuração Centralizada

- 🔄 **Hot reload** com Spring Actuator + Spring Cloud Bus (opcional).
- 🛠️ **Gerenciamento unificado** de propriedades sensíveis e variáveis de ambiente.
- 📦 **Versionamento via Git**: histórico de alterações rastreável.
- 🧩 **Integração com múltiplos perfis** (ex: `dev`, `prod`, `test`).



## 🔗 Repositórios Relacionados

Os serviços abaixo consomem as configurações contidas aqui:

* 🧠 **[AI Service (Spring AI + RAG)](https://github.com/franklinclf/nexus-spring-cloud-ai)**
* 🧭 **[Gateway (Spring Cloud Gateway)](https://github.com/franklinclf/nexus-spring-cloud-gateway)**
* 🔍 **[Eureka Discovery Service](https://github.com/franklinclf/nexus-spring-cloud-discovery)**
* 🧾 **[Ticket Service + MCP](https://github.com/franklinclf/nexus-spring-cloud-mcp)**
* ☁️ **[Serverless Function](https://github.com/franklinclf/nexus-spring-cloud-serverless)**
* 
---
