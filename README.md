# 🔐 API de Autenticação e Autorização com JWT (Spring Boot 3)

## 🚀 Visão Geral

Este projeto é uma API RESTful construída com Spring Boot 3, que implementa autenticação e autorização com JWT (JSON Web Token). Ele oferece mecanismos seguros de login, geração de tokens, proteção de rotas com base em permissões e documentação integrada via Swagger.

✅ Ideal para sistemas distribuídos e microsserviços que necessitam de autenticação centralizada e segura.

---

## 📋 Funcionalidades

* Login com usuário e senha
* Emissão de token JWT assinado no backend
* Validação local de tokens JWT
* Controle de acesso por roles (`USER`, `ADMIN`)
* Uso de `@PreAuthorize` para proteger endpoints
* Testes automatizados com JUnit e MockMvc
* Testes de estresse com Apache JMeter
* Documentação interativa com Swagger
* Banco de dados em memória (H2)
* Monitoramento via Spring Boot Actuator
* Pronto para deploy com Docker e hospedagem em nuvem (Render, Railway)

---

## 🚀 Tecnologias Utilizadas

* Java 17+
* Spring Boot 3.x
* Spring Security
* Spring OAuth2 Resource Server
* Spring Data JPA
* H2 Database (memória)
* Lombok
* Swagger UI (via Springdoc OpenAPI)
* JUnit 5 + Mockito
* Apache JMeter
* Spring Boot Actuator
* Docker

---

## ⚙️ Executando Localmente

1. Clone o repositório:

```bash
git clone https://github.com/seu-usuario/auth-jwt-api.git
cd auth-jwt-api
```

2. Execute a aplicação:

```bash
./mvnw spring-boot:run
```

---

## 🔐 Usuários Padrão

| Usuário | Senha    | Permissão |
| ------- | -------- | --------- |
| admin   | 123456   | ADMIN     |
| user    | password | USER      |

> ⚠️ As senhas são criptografadas com BCrypt.

---

## 🔑 Principais Endpoints

| Método | Caminho        | Proteção  | Descrição                              |
| ------ | -------------- | --------- | -------------------------------------- |
| POST   | /auth/login    | ❌ Público | Realiza autenticação e retorna JWT     |
| POST   | /auth/validate | ❌ Público | Verifica se o token informado é válido |
| GET    | /api/hello     | ✅ JWT     | Acesso permitido com JWT válido        |
| GET    | /api/admin     | ✅ ADMIN   | Acesso restrito para ADMIN             |

Use o cabeçalho:

```
Authorization: Bearer <seu_token_jwt>
```

---

## 📚 Documentação da API

Documentação interativa disponível via Swagger:

* URL: [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

Inclui suporte ao envio de JWT diretamente pela interface.

---

## 🧪 Testes Automatizados

Execute os testes com:

```bash
./mvnw test
```

Cobertura dos testes:

* Autenticação com credenciais válidas e inválidas
* Acesso a endpoints públicos e protegidos
* Verificação de autorização com role ADMIN

---

## 📈 Testes de Desempenho com JMeter

* Arquivo de teste: `jmeter-tests/login_stress_test.jmx`

### Passos:

1. Instale o Apache JMeter
2. Abra e carregue o arquivo JMX no JMeter
3. Configure o número de usuários (ex: 200 usuários, ramp-up de 20s)
4. Clique em ▶ Start
5. Analise os resultados nos relatórios:

   * Summary Report
   * View Results Tree

---

## 📊 Monitoramento com Spring Boot Actuator

Acesse os principais endpoints de monitoramento:

* `http://localhost:8080/actuator/health`
* `http://localhost:8080/actuator/info`
* `http://localhost:8080/actuator/metrics`

Integração recomendada com Prometheus e Grafana para dashboards em tempo real.

---

## 🐳 Docker (Opcional)

### Dockerfile

```dockerfile
FROM eclipse-temurin:17-jdk-alpine
COPY target/auth-jwt-api.jar app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

### Build e Execução

```bash
./mvnw clean package
docker build -t auth-jwt-api .
docker run -p 8080:8080 auth-jwt-api
```

---

## ☁️ Sugestões de Deploy Gratuito

Você pode publicar a aplicação em serviços como:

* [Render](https://render.com)
* [Railway](https://railway.app)

Inclua a variável `JWT_SECRET` como um segredo no ambiente da plataforma.

---

## 📦 Estrutura do Projeto

```bash
├── src
│   ├── main
│   │   ├── java/com/example/authserver
│   │   │   ├── controller
│   │   │   ├── service
│   │   │   ├── repository
│   │   │   ├── model
│   │   │   └── config
│   │   └── resources
│   │       └── application.yml
│   └── test/java/com/example/authserver
├── jmeter-tests
│   └── login_stress_test.jmx
├── pom.xml
└── README.md
```

---
