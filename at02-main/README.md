# 🔐 API de Autenticação e Autorização com JWT (Spring Boot 3)

Este projeto é uma API RESTful desenvolvida com **Spring Boot 3** que fornece autenticação e autorização baseadas em **JWT (JSON Web Tokens)**. A API permite o login de usuários, geração de tokens, proteção de recursos com base em roles e documentação interativa com Swagger.

> ✅ Ideal para cenários de autenticação centralizada em arquiteturas com microsserviços ou APIs seguras.

---

## 📋 Funcionalidades

- Autenticação via login (usuário/senha)
- Geração de token JWT assinado internamente
- Validação interna de tokens
- Autorização baseada em roles (`USER`, `ADMIN`)
- Endpoints protegidos com `@PreAuthorize`
- Testes automatizados com JUnit + MockMvc
- Testes de carga com JMeter
- Documentação interativa com Swagger
- Banco de dados em memória (H2)
- Monitoramento com Spring Boot Actuator
- Preparado para deploy via Docker + Render/Railway

---

## 🚀 Tecnologias e Dependências

- Java 17+
- Spring Boot 3.x
- Spring Security
- OAuth2 Resource Server
- Spring Data JPA
- H2 Database
- Lombok
- Springdoc OpenAPI (Swagger UI)
- JUnit 5 + Mockito
- Apache JMeter
- Spring Boot Actuator
- Docker

---

## ⚙️ Como Executar Localmente

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/auth-jwt-api.git
cd auth-jwt-api


🔐 Usuários Criados Automaticamente
Username	Senha	Role
admin	123456	ADMIN
user	password	USER

⚠️ Senhas são armazenadas com BCrypt.

🔑 Endpoints Principais
Método	Caminho	Protegido?	Descrição
POST	/auth/login	❌	Login e geração de token JWT
POST	/auth/validate	❌	Validação manual de token
GET	/api/hello	✅	Acesso com qualquer JWT válido
GET	/api/admin	✅ ADMIN	Apenas para role ADMIN

Para endpoints protegidos, use:
Authorization: Bearer <token_jwt>

📚 Swagger / OpenAPI
Acesse a documentação interativa em:

📄 http://localhost:8080/swagger-ui.html

🧪 Testes Automatizados
Execute os testes com:

bash
Copiar
Editar
./mvnw test
Testes incluídos:

Login com credenciais válidas e inválidas

Acesso a endpoints com e sem token

Validação de role ADMIN em endpoints protegidos

📈 Testes de Carga com JMeter
Arquivo de teste: jmeter-tests/login_stress_test.jmx

Como rodar:
Instale o Apache JMeter

Abra o JMeter e carregue o arquivo .jmx

Configure a thread (ex: 200 usuários, 20s ramp-up)

Clique em ▶ Start

Analise os relatórios em Summary Report e View Results Tree

📊 Monitoramento com Actuator
Acesse os endpoints de monitoramento:

http://localhost:8080/actuator/health

http://localhost:8080/actuator/info

http://localhost:8080/actuator/metrics

Se quiser, integre com Prometheus e Grafana.

🐳 Docker (Opcional)
Dockerfile
dockerfile
Copiar
Editar
FROM eclipse-temurin:17-jdk-alpine
COPY target/auth-jwt-api.jar app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
Build e Run
bash
Copiar
Editar
./mvnw clean package
docker build -t auth-jwt-api .
docker run -p 8080:8080 auth-jwt-api
☁️ Deploy Gratuito (Sugestões)
Você pode publicar a API em plataformas como:

Render

Railway

Inclua a variável JWT_SECRET como segredo no painel da plataforma.

📦 Estrutura do Projeto
bash
Copiar
Editar
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

