# Spring Boot REST API

Uma aplicação de API REST desenvolvida com Spring Boot, focada em demonstrar as melhores práticas de desenvolvimento de APIs modernas com Java.

## 📋 Descrição do Projeto

Este é um projeto educacional que implementa um fórum API REST construído com Spring Boot. Ele demonstra conceitos fundamentais de desenvolvimento de APIs RESTful, incluindo operações CRUD, validação de dados, tratamento de erros e integração com banco de dados.

## 🎯 Objetivos de Aprendizado

Este projeto aborda os seguintes temas:

- ✅ Criação de aplicações Java com Spring Boot
- ✅ Configuração do Spring Boot sem uso de arquivos XML
- ✅ Desenvolvimento acelerado com Spring DevTools
- ✅ Padrões arquiteturais REST (GET, POST, PUT, DELETE)
- ✅ Integração com banco de dados usando Spring Data JPA
- ✅ Validação de dados com Bean Validation
- ✅ Tratamento robusto de erros e exceções

## 📚 Conteúdo do Curso

### Módulos

1. **Introdução ao Spring Boot**
   - Configuração inicial do projeto
   - Entendimento da estrutura Spring Boot

2. **Publicando Endpoints**
   - Criação de endpoints REST
   - Mapeamento de requisições HTTP

3. **Usando Spring Data**
   - Configuração do JPA
   - Operações com banco de dados

4. **Trabalhando com POST**
   - Recebimento e processamento de dados
   - Criação de novos recursos

5. **Validação com Bean Validation**
   - Validação de entrada
   - Mensagens de erro customizadas

6. **Métodos PUT, DELETE e Tratamento de Erro**
   - Atualização de recursos
   - Exclusão de recursos
   - Tratamento global de exceções

## 🛠️ Tecnologias Utilizadas

- **Linguagem**: Java 1.8
- **Framework**: Spring Boot 2.1.4.RELEASE
- **Build Tool**: Maven
- **Banco de Dados**: H2 Database
- **Dependências Principais**:
  - `spring-boot-starter-web`: Para criação de APIs REST
  - `spring-boot-starter-data-jpa`: Para persistência de dados
  - `h2`: Banco de dados em memória para desenvolvimento
  - `spring-boot-devtools`: Ferramentas de desenvolvimento
  - `spring-boot-starter-test`: Testes unitários

## 📦 Pré-requisitos

Antes de começar, você precisará ter instalado:

- **Java 8** ou superior
- **Maven 3.6+** ou use o Maven wrapper incluído no projeto
- **Git** (opcional, para clonar o repositório)

## 🚀 Começando

### 1. Clonar o Repositório

```bash
git clone https://github.com/jrmoreiram/spring-boot-rest-api.git
cd spring-boot-rest-api
```

### 2. Executar a Aplicação

Usando Maven wrapper (recomendado):

```bash
./mvnw spring-boot:run
```

Ou usando Maven instalado:

```bash
mvn spring-boot:run
```

A aplicação estará disponível em: `http://localhost:8080`

### 3. Construir o Projeto

Para gerar o JAR executável:

```bash
./mvnw clean package
```

Para executar o JAR gerado:

```bash
java -jar target/forum-0.0.1-SNAPSHOT.jar
```

## 📖 Estrutura do Projeto

```
spring-boot-rest-api/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── br/com/alura/forum/
│   │   │       ├── controller/      # Controladores REST
│   │   │       ├── model/           # Entidades do domínio
│   │   │       ├── repository/      # Repositórios JPA
│   │   │       ├── service/         # Lógica de negócio
│   │   │       └── Application.java # Classe principal
│   │   └── resources/
│   │       └── application.properties # Configuração da app
│   └── test/
│       └── java/                    # Testes unitários
├── .mvn/                            # Maven wrapper
├── pom.xml                          # Dependências do projeto
├── mvnw / mvnw.cmd                  # Scripts Maven wrapper
└── README.md                        # Este arquivo
```

## 🔌 API Endpoints

### Exemplos de Endpoints Disponíveis

```
GET    /api/topics          - Listar todos os tópicos
POST   /api/topics          - Criar novo tópico
GET    /api/topics/{id}     - Obter detalhes de um tópico
PUT    /api/topics/{id}     - Atualizar um tópico
DELETE /api/topics/{id}     - Deletar um tópico
```

## ⚙️ Configuração

As configurações da aplicação estão em `src/main/resources/application.properties`:

```
# Servidor
server.port=8080

# Banco de dados H2
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.h2.console.enabled=true
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect

# JPA/Hibernate
spring.jpa.hibernate.ddl-auto=create-drop
spring.jpa.show-sql=true
```

## 🧪 Testando a Aplicação

```bash
# Executar todos os testes
./mvnw test

# Executar testes com cobertura
./mvnw test jacoco:report
```

## 🐛 Troubleshooting

### Porta 8080 já está em uso

```bash
# Mude a porta no arquivo application.properties
server.port=8081
```

### Erro ao executar com Java 11+

```bash
# Java 11+ requer argumentos adicionais
./mvnw spring-boot:run -Dspring-boot.run.jvmArguments="-Xmx1024m"
```

## 📝 Licença

Este projeto é fornecido como material educacional do curso Alura.

## 👥 Autor

**Junior Moreira Martins**
- GitHub: [@jrmoreiram](https://github.com/jrmoreiram)

## 📞 Suporte

Para dúvidas ou sugestões sobre este projeto, abra uma [issue](https://github.com/jrmoreiram/spring-boot-rest-api/issues) no repositório.

## 🔗 Recursos Adicionais

- [Documentação Spring Boot](https://spring.io/projects/spring-boot)
- [Spring Data JPA Documentation](https://spring.io/projects/spring-data-jpa)
- [REST API Best Practices](https://restfulapi.net/)
- [Bean Validation Documentation](https://beanvalidation.org/)

---

**Última atualização**: 2026-03-28 12:06:32
