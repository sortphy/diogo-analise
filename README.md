### Equipe: Gustavo Henrique, Icaro Botelho, Maruan Biasi, Ricardo Falcao e Thiago Saraiva

# ANALISE DIOGO
![Screenshot_1098](https://github.com/user-attachments/assets/392d2c5f-7a3f-4b57-879f-50b03984bba0)


----------------------

## 🧠 Projeto: [coderkan/spring-boot-redis-cache](https://github.com/coderkan/spring-boot-redis-cache)  
### ✅ Característica: Uso de cache (Redis)

**Trecho de código:**
```java
@EnableCaching
public class RedisConfig {
  @Bean
  public RedisCacheManager cacheManager(...) { ... }
}
````

**Por que usar:**
Esse projeto usa Redis pra salvar dados temporários de forma rápida. Isso ajuda a diminuir acesso repetido ao banco, melhora o tempo de resposta e economiza recurso quando muitos usuários acessam ao mesmo tempo.

---

## 📨 Projeto: [springframeworkguru/spring-boot-rabbitmq-example](https://github.com/springframeworkguru/spring-boot-rabbitmq-example)

### ✅ Característica: Fila de mensageria (RabbitMQ)

**Trecho de código:**

```java
@Bean
Queue queue() {
    return new Queue("sfg-message-queue", false);
}
```

**Por que usar:**
A fila serve pra desacoplar partes do sistema. Em vez de um serviço depender diretamente de outro, ele só envia uma mensagem e segue a vida. Isso deixa tudo mais escalável e resistente a falhas.

---

## 🚨 Projeto: [TechPrimers/resilience4j-circuitbreaker](https://github.com/TechPrimers/resilience4j-circuitbreaker)

### ✅ Característica: Circuit Breaker

**Trecho de código:**

```java
@CircuitBreaker(name = "serviceA", fallbackMethod = "fallback")
public String callServiceA() { ... }
```

**Por que usar:**
O breaker é tipo um disjuntor. Se um serviço começa a falhar, ele corta as chamadas pra evitar quebrar tudo. Aí tenta de novo só depois de um tempo. Usaram isso pra evitar que o app fique tentando uma coisa que já deu errado.

---

## ⚙️ Projeto: [piomin/sample-spring-kafka-microservices](https://github.com/piomin/sample-spring-kafka-microservices)

### ✅ Característica: CI/CD com pipeline

**Trecho de código:**

```yaml
# .circleci/config.yml
version: 2.1
jobs:
  build:
    docker:
      - image: circleci/openjdk:11-jdk
    steps:
      - checkout
      - run: mvn clean install
```

**Por que usar:**
Tem pipeline automático pra build e teste com CircleCI. Isso ajuda a saber se o código tá funcionando logo depois que alguém faz um push. Evita quebrar o projeto sem querer.

---

## 🔍 Projeto: [piomin/sample-spring-kafka-microservices](https://github.com/piomin/sample-spring-kafka-microservices)

### ✅ Característica: Análise estática de código (Sonar)

**Trecho de código:**

```xml
<properties>
    <sonar.projectKey>...</sonar.projectKey>
    <sonar.organization>...</sonar.organization>
</properties>
```

**Por que usar:**
Eles usam Sonar pra checar a qualidade do código. A ferramenta aponta problema antes mesmo de rodar. Coisas tipo código repetido, má prática, etc. Isso deixa o projeto mais limpo e fácil de manter.

---

## 🔐 Projeto: [bezkoder/spring-boot-spring-security-jwt-authentication](https://github.com/bezkoder/spring-boot-spring-security-jwt-authentication)

### ✅ Característica: Autenticação com JWT

**Trecho de código:**

```properties
bezKoder.app.jwtSecret=bezKoderSecretKey
bezKoder.app.jwtExpirationMs=86400000
```

**Por que usar:**
JWT é prático pra autenticar sem salvar sessão no servidor. O token carrega tudo que o backend precisa saber, tipo quem é o usuário. Esse projeto usa isso pra API segura, moderna e simples de escalar.

---

## 🧬 Projeto: [aws-samples/serverless-patterns](https://github.com/aws-samples/serverless-patterns)

### ✅ Característica: Serverless / Lambda

**Trecho de código:**

```yaml
Resources:
  MyFunction:
    Type: AWS::Serverless::Function
    Properties:
      Handler: app.lambda_handler
      Runtime: python3.8
```

**Por que usar:**
Em vez de rodar servidor 24/7, com Lambda só paga quando o código roda. Ideal pra eventos esporádicos ou apps pequenos. O repositório mostra vários exemplos reais com API Gateway, S3, SQS etc.

---

## 🧪 Projeto: [gothinkster/spring-boot-realworld-example-app](https://github.com/gothinkster/spring-boot-realworld-example-app)

### ✅ Característica: Testes automatizados

**Trecho de código:**

```java
@RunWith(SpringRunner.class)
@SpringBootTest
public class ArticleRepositoryTransactionTest { ... }
```

**Por que usar:**
Tem teste de tudo no projeto: unitário, integração, repositório, serviço, etc. Isso ajuda a garantir que nada quebre sem querer quando muda alguma coisa. Muito útil pra projetos maiores e com várias pessoas mexendo ao mesmo tempo.

---
