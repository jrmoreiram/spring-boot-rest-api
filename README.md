# Spring Boot REST API

Uma aplicação de API REST desenvolvida com Spring Boot, focada em demonstrar as melhores práticas de desenvolvimento de APIs modernas com Java.

**Baseado no Curso:** Curso de Spring Boot API REST: construa uma API da DevMedia

---

## 📋 Sumário Executivo

Este projeto implementa uma **API REST para Fórum** utilizando o framework Spring Boot, demonstrando princípios sólidos de arquitetura de software, padrões de design e boas práticas de desenvolvimento. O projeto foi desenvolvido como material educacional e serve como referência para construção de APIs RESTful robustas e escaláveis.

---

## 1️⃣ Visão Geral do Projeto

### 1.1 Descrição

Este é um projeto educacional que implementa um fórum API REST construído com Spring Boot. Ele demonstra conceitos fundamentais de desenvolvimento de APIs RESTful, incluindo:

- Operações CRUD (Create, Read, Update, Delete)
- Validação de dados
- Tratamento robusto de erros e exceções
- Integração com banco de dados via ORM
- Segurança de dados
- Versionamento de API

### 1.2 Objetivos

- ✅ Demonstrar a criação de aplicações Java modernas com Spring Boot
- ✅ Aplicar padrões REST em operações HTTP (GET, POST, PUT, DELETE)
- ✅ Implementar validação de dados com Bean Validation
- ✅ Gerenciar persistência de dados com Spring Data JPA
- ✅ Implementar tratamento global de exceções
- ✅ Desenvolver endpoints bem estruturados e documentados

---

## 2️⃣ Arquitetura e Design

### 2.1 Padrão Arquitetural

O projeto segue o padrão **Modelo-Visão-Controlador (MVC)** com separação de responsabilidades:

```
┌─────────────────────────────────────────────────────────┐
│                    Client/Requisição                     │
└────────────────────────┬────────────────────────────────┘
                         │
                  ┌──────▼──────┐
                  │ Controller  │ (Recebe requisições HTTP)
                  └──────┬──────┘
                         │
                  ┌──────▼──────┐
                  │   Service   │ (Lógica de negócio)
                  └──────┬──────┘
                         │
          ┌──────────────┼──────────────┐
          │              │              │
    ┌─────▼────┐  ┌─────▼────┐  ┌───────▼──┐
    │Repository│  │Validator │  │Mapper    │
    └─────┬────┘  └──────────┘  └──────────┘
          │
    ┌─────▼────────────────────────┐
    │  Banco de Dados (H2)         │
    └──────────────────────────────┘
```

### 2.2 Componentes Principais

| Componente | Responsabilidade | Localização |
|---|---|---|
| **Controller** | Mapear requisições HTTP, validar entrada | `controller/` |
| **Service** | Implementar lógica de negócio | `service/` |
| **Repository** | Comunicar com banco de dados | `repository/` |
| **Model/Entity** | Representar entidades do domínio | `model/` |
| **DTO** | Transfer Objects para API | `dto/` |

---

## 3️⃣ Tecnologias Utilizadas

| Tecnologia | Versão | Propósito |
|---|---|---|
| **Java** | 1.8+ | Linguagem de programação |
| **Spring Boot** | 2.1.4.RELEASE | Framework web e IoC |
| **Spring Data JPA** | 2.1.4 | ORM e acesso a dados |
| **Maven** | 3.6+ | Gerenciador de dependências |
| **H2 Database** | 1.4.197 | Banco de dados em memória |
| **Bean Validation** | 2.0.1 | Validação de dados |
| **Hibernat** | 5.3.9 | Implementação JPA |

### 3.1 Dependências do Projeto

```xml
<!-- Spring Boot Starters -->
spring-boot-starter-web          # API REST
spring-boot-starter-data-jpa     # Persistência ORM
spring-boot-starter-validation   # Bean Validation
spring-boot-devtools             # Desenvolvimento

<!-- Banco de Dados -->
h2                               # H2 Database

<!-- Testes -->
spring-boot-starter-test         # Testes unitários
```

---

## 4️⃣ Pré-requisitos

Antes de começar, certifique-se de ter os seguintes requisitos atendidos:

- **Java Development Kit (JDK) 8+** - [Download](https://www.oracle.com/java/technologies/javase-downloads.html)
- **Maven 3.6+** ou Maven Wrapper (incluído no projeto)
- **Git** (opcional, para clonar o repositório)
- **Editor de Código/IDE** - Recomendado: IntelliJ IDEA ou Visual Studio Code

### 4.1 Verificar Instalação

```bash
# Verificar Java
java -version

# Verificar Maven
mvn -version
```

---

## 5️⃣ Instalação e Configuração

### 5.1 Clonar o Repositório

```bash
git clone https://github.com/jrmoreiram/spring-boot-rest-api.git
cd spring-boot-rest-api
```

### 5.2 Estrutura de Diretórios

```
spring-boot-rest-api/
├── .mvn/                              # Maven Wrapper
├── src/
│   ├── main/
│   │   ├── java/br/com/alura/forum/
│   │   │   ├── Application.java       # Classe de inicialização
│   │   │   ├── controller/            # Controladores REST
│   │   │   │   └── TopicsController.java
│   │   │   ├── service/               # Serviços e lógica de negócio
│   │   │   │   └── TopicsService.java
│   │   │   ├── model/                 # Entidades JPA
│   │   │   │   ├── Topic.java
│   │   │   │   └── Answer.java
│   │   │   ├── repository/            # Repositórios JPA
│   │   │   │   ├── TopicsRepository.java
│   │   │   │   └── AnswersRepository.java
│   │   │   └── dto/                   # Data Transfer Objects
│   │   │       ├── TopicDTO.java
│   │   │       └── AnswerDTO.java
│   │   └── resources/
│   │       ├── application.properties # Configurações da aplicação
│   │       └── data.sql               # Script SQL inicial
│   └── test/java/                     # Testes unitários e integração
├── pom.xml                            # Arquivo de dependências Maven
├── mvnw / mvnw.cmd                    # Maven Wrapper (Windows/Unix)
└── README.md                          # Este arquivo
```

---

## 6️⃣ Como Executar

### 6.1 Usando Maven Wrapper (Recomendado)

```bash
# Linux/macOS
./mvnw spring-boot:run

# Windows
mvnw.cmd spring-boot:run
```

### 6.2 Usando Maven Instalado

```bash
mvn spring-boot:run
```

### 6.3 Compilar e Gerar JAR

```bash
# Compilar e empacotar
./mvnw clean package

# Executar JAR
java -jar target/forum-0.0.1-SNAPSHOT.jar
```

### 6.4 Acessar a Aplicação

```
http://localhost:8080
```

---

## 7️⃣ Configuração da Aplicação

### 7.1 Arquivo de Propriedades

As configurações da aplicação estão em `src/main/resources/application.properties`:

```properties
# ============================================
# CONFIGURAÇÕES DO SERVIDOR
# ============================================
server.port=8080
server.servlet.context-path=/api

# ============================================
# CONFIGURAÇÕES DO BANCO DE DADOS H2
# ============================================
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

# Console H2 (apenas desenvolvimento)
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# ============================================
# CONFIGURAÇÕES JPA/HIBERNATE
# ============================================
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=create-drop
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

# ============================================
# CONFIGURAÇÕES DE LOG
# ============================================
logging.level.root=INFO
logging.level.br.com.alura.forum=DEBUG
```

### 7.2 Configurações por Ambiente

Para diferentes ambientes, crie arquivos específicos:

```
application-dev.properties       # Desenvolvimento
application-test.properties      # Testes
application-prod.properties      # Produção
```

Ative com: `spring.profiles.active=prod`

---

## 8️⃣ API Endpoints

### 8.1 Documentação de Endpoints

#### **Tópicos**

| Método | Endpoint | Descrição | Status |
|--------|----------|-----------|--------|
| `GET` | `/api/topics` | Listar todos os tópicos | 200 OK |
| `GET` | `/api/topics/{id}` | Obter tópico específico | 200 OK / 404 Not Found |
| `POST` | `/api/topics` | Criar novo tópico | 201 Created |
| `PUT` | `/api/topics/{id}` | Atualizar tópico | 200 OK / 404 Not Found |
| `DELETE` | `/api/topics/{id}` | Deletar tópico | 204 No Content |

#### **Respostas**

```json
# GET /api/topics
{
  "id": 1,
  "title": "Como começar com Spring Boot?",
  "message": "Gostaria de saber os primeiros passos...",
  "createdAt": "2026-03-28T10:30:00",
  "author": "joao_silva",
  "status": "OPEN"
}

# POST /api/topics
{
  "title": "Novo tópico",
  "message": "Descrição do tópico",
  "author": "usuario"
}
```

### 8.2 Códigos de Status HTTP

- `200 OK` - Requisição bem-sucedida
- `201 Created` - Recurso criado com sucesso
- `204 No Content` - Sucesso, sem conteúdo
- `400 Bad Request` - Requisição inválida
- `404 Not Found` - Recurso não encontrado
- `500 Internal Server Error` - Erro no servidor

---

## 9️⃣ Validação de Dados

### 9.1 Bean Validation

A aplicação utiliza anotações do Bean Validation para validar dados:

```java
@Entity
public class Topic {
    
    @NotBlank(message = "Título não pode estar em branco")
    @Size(min = 5, max = 100)
    private String title;
    
    @NotBlank(message = "Mensagem não pode estar em branco")
    @Size(min = 10, max = 500)
    private String message;
    
    @Email(message = "Email deve ser válido")
    private String authorEmail;
}
```

### 9.2 Anotações Comuns

| Anotação | Descrição |
|----------|-----------|
| `@NotNull` | Campo não pode ser nulo |
| `@NotBlank` | String não pode estar vazia |
| `@Size(min, max)` | Validar tamanho |
| `@Email` | Validar formato de email |
| `@Min/@Max` | Validar valores numéricos |
| `@Pattern` | Validar com expressão regular |

---

## 🔟 Tratamento de Erros

### 10.1 Exception Handler Global

A aplicação implementa um tratamento centralizado de exceções:

```java
@RestControllerAdvice
public class GlobalExceptionHandler {
    
    @ExceptionHandler(EntityNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleNotFound(EntityNotFoundException e) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND)
            .body(new ErrorResponse(e.getMessage()));
    }
}
```

### 10.2 Formato de Erro

```json
{
  "timestamp": "2026-03-28T10:30:00",
  "status": 404,
  "error": "Not Found",
  "message": "Tópico não encontrado",
  "path": "/api/topics/999"
}
```

---

## 1️⃣1️⃣ Testes

### 11.1 Executar Testes

```bash
# Executar todos os testes
./mvnw test

# Executar testes de classe específica
./mvnw test -Dtest=TopicsControllerTest

# Executar com cobertura
./mvnw test jacoco:report
```

### 11.2 Estrutura de Testes

```
src/test/java/br/com/alura/forum/
├── controller/
│   └── TopicsControllerTest.java
├── service/
│   └── TopicsServiceTest.java
└── repository/
    └── TopicsRepositoryTest.java
```

---

## 1️⃣2️⃣ Troubleshooting

### Problema: Porta 8080 já está em uso

**Solução:**
```bash
# Opção 1: Mudar porta via command line
./mvnw spring-boot:run -Dspring-boot.run.arguments="--server.port=8081"

# Opção 2: Editar application.properties
server.port=8081

# Opção 3: Encontrar e matar processo
# Linux/macOS
lsof -i :8080
kill -9 <PID>

# Windows
netstat -ano | findstr :8080
taskkill /PID <PID> /F
```

### Problema: Erro ao executar com Java 11+

**Solução:**
```bash
./mvnw spring-boot:run -Dspring-boot.run.jvmArguments="-Xmx1024m"
```

### Problema: Dependências não baixando

**Solução:**
```bash
# Limpar cache Maven
./mvnw clean

# Forçar download de dependências
./mvnw dependency:resolve
```

### Problema: Erro de conexão com banco de dados

**Solução:**
```properties
# Verificar arquivo application.properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
```

---

## 1️⃣3️⃣ Deployment

### 13.1 Preparar para Produção

```bash
# Gerar build otimizado
./mvnw clean package -DskipTests -Dspring.profiles.active=prod
```

### 13.2 Executar em Servidor

```bash
# Executar JAR em background
nohup java -jar forum-0.0.1-SNAPSHOT.jar &

# Com parametros JVM otimizados
java -Xms512m -Xmx1024m -jar forum-0.0.1-SNAPSHOT.jar
```

### 13.3 Docker (Opcional)

```dockerfile
FROM openjdk:8-jre-alpine
COPY target/forum-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

---

## 1️⃣4️⃣ Contribuindo

### 14.1 Processo de Contribuição

1. **Fork** o repositório
2. Crie uma **branch de feature** (`git checkout -b feature/AmazingFeature`)
3. **Commit** suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. **Push** para a branch (`git push origin feature/AmazingFeature`)
5. Abra um **Pull Request**

### 14.2 Padrões de Código

- Seguir convenções Java
- Adicionar testes para novas funcionalidades
- Documentar mudanças no README
- Usar mensagens de commit descritivas

---

## 1️⃣5️⃣ Referências e Recursos

### Documentação Oficial

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- [Spring Web MVC](https://docs.spring.io/spring-framework/docs/current/reference/html/web.html)
- [Bean Validation Specification](https://beanvalidation.org/)
- [Hibernate ORM](https://hibernate.org/orm/)

### REST API Best Practices

- [RESTful API Design Guidelines](https://restfulapi.net/)
- [JSON API Specification](https://jsonapi.org/)
- [OpenAPI Specification](https://swagger.io/specification/)

### Recursos Adicionais

- [Alura - Plataforma de Educação](https://www.alura.com.br/)
- [Spring Boot Guide](https://spring.io/guides)
- [Baeldung - Spring Boot Tutorials](https://www.baeldung.com/spring-boot)

---

## 📝 Licença

Este projeto é fornecido como material educacional baseado no **Curso de Spring Boot API REST: construa uma API**. Todos os direitos reservados conforme legislação aplicável.

---

## 👥 Autor

**Junior Moreira Martins**

- 🔗 GitHub: [@jrmoreiram](https://github.com/jrmoreiram)
- 📧 Entre em contato através de Issues no repositório

---

## 📞 Suporte e Feedback

Para dúvidas, sugestões ou relato de problemas:

1. Abra uma [Issue](https://github.com/jrmoreiram/spring-boot-rest-api/issues) descrevendo o problema
2. Inclua informações relevantes (versão Java, mensagens de erro, etc.)
3. Seja específico e forneça passos para reproduzir

---

## 📋 Changelog

### v1.0.0 (2026-03-28)
- ✅ Implementação inicial da API REST
- ✅ Endpoints CRUD para tópicos
- ✅ Validação de dados com Bean Validation
- ✅ Tratamento global de exceções
- ✅ Documentação técnica completa

---

**Última atualização:** 2026-03-28

**Status:** ✅ Ativo e Mantido
